---
title: "デザイン パターン: リストに基づく公開/定期受信"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 202dd34cfc02fd17b9edaa558fe64ea44ddd6f71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="design-patterns-list-based-publish-subscribe"></a>デザイン パターン: リストに基づく公開/定期受信
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] プログラムとして実装された、リストに基づく公開/定期受信パターンを示します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 リストに基づく公開/定期受信のデザイン パターンについては、「Microsoft Patterns & Practices のパブリケーション[統合パターン](http://go.microsoft.com/fwlink/?LinkId=95894)です。 公開/定期受信パターンは、情報トピックを定期受信する受信者のコレクションに情報を渡します。 リストに基づく公開/定期受信では、サブスクライバのリストが保持されます。 共有情報が存在する場合は、コピーがリスト上の各サブスクライバに送信されます。 このサンプルでは、動的なリストに基づく公開/定期受信パターンを示します。これにより、クライアントは必要に応じて何度でも定期受信または定期受信の解除ができます。  
  
 リストに基づく公開/定期受信のサンプルは、クライアント、サービス、およびデータ ソース プログラムで構成されています。 クライアントとデータ ソース プログラムは、複数を実行できます。 クライアントはサービスを定期受信し、通知を受信して、定期受信を解除します。 データ ソース プログラムはサービスに情報を送信し、現在のすべてのサブスクライバでその情報が共有されるようにします。  
  
 このサンプルでは、クライアントとデータ ソースはコンソール プログラム (.exe ファイル) で、サービスはインターネット インフォメーション サービス (IIS) でホストされるライブラリ (.dll) です。 クライアントとデータ ソースのアクティビティは、デスクトップに表示されます。  
  
 サービスは、双方向通信を使用します。 `ISampleContract` サービス コントラクトは `ISampleClientCallback` コールバック コントラクトと対になっています。 サービスは Subscribe および Unsubscribe サービス操作を実装します。クライアントはこれらのサービス操作を使用してサブスクライバのリストに参加またはリストへの参加を解除します。 サービスは、さらに `PublishPriceChange` サービス操作も実装します。データ ソース プログラムはこれを呼び出して、新しい情報をサービスに提供します。 クライアント プログラムは `PriceChange` サービス操作を実装します。サービスはこれを呼び出して、すべてのサブスクライバに価格の変更を通知します。  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 サービスは、すべてのサブスクライバに新しい情報を通知する機構として、.NET Framework イベントを使用します。 クライアントが Subscribe を呼び出してサービスに参加すると、イベント ハンドラが提供されます。 クライアントがサービスへの参加を解除すると、イベントからイベント ハンドラの定期受信が解除されます。 データ ソースが価格の変更を報告するサービスを呼び出すと、サービスはイベントを発生させます。 これにより、サービスの各インスタンスが呼び出されます。このサービスは定期受信した各クライアントのサービスで、この呼び出しによって各インスタンスのイベント ハンドラが実行されます。 各イベント ハンドラは、コールバック関数を使用してクライアントに情報を渡します。  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is deregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 このサンプルを実行すると、複数のクライアントが起動されます。 クライアントはサービスを定期受信します。 次にデータ ソース プログラムが実行され、サービスに情報が送信されます。 サービスは、すべてのサブスクライバに情報を渡します。 各クライアント コンソールでアクティビティを表示し、情報が受信されたことを確認できます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
### <a name="to-set-up-and-build-the-sample"></a>サンプルをセットアップしてビルドするには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>サンプルを同じコンピューターで実行するには  
  
1.  ブラウザにアドレス「http://localhost/servicemodelsamples/service.svc」を入力して、サービスにアクセスできるかどうかをテストします。 これに応答して、確認ページが表示されます。  
  
2.  Client.exe を \client\bin 実行\\、言語固有のフォルダーの下。 クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。 複数のクライアントを起動します。  
  
3.  \Datasource\bin から Datasource.exe を実行\\、言語固有のフォルダーの下。 データ ソース アクティビティがコンソール ウィンドウに表示されます。 データ ソースがサービスに情報を送信すると、その情報は各クライアントに渡されます。  
  
4.  クライアント、データ ソース、およびサービス プログラムできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)です。  
  
### <a name="to-run-the-sample-across-machines"></a>サンプルを複数コンピューターで実行するには  
  
1.  サービス コンピュータを設定します。  
  
    1.  サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。 バッチ ファイルから Setupvroot.bat、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)ディスク ディレクトリと仮想ディレクトリの作成に使用することができます。  
  
    2.  サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。 \bin ディレクトリのファイルが含まれていることを確認してください。  
  
    3.  ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。  
  
2.  クライアント コンピュータを設定します。  
  
    1.  クライアント プログラム ファイルを、言語固有のフォルダにある \client\bin\ フォルダからクライアント コンピュータにコピーします。  
  
    2.  各クライアントの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに合わせて変更します。 アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
3.  データ ソース コンピュータを設定します。  
  
    1.  データ ソース プログラム ファイルを、言語固有のフォルダにある \datasource\bin\ フォルダからデータ ソース コンピュータにコピーします。  
  
    2.  データ ソースの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに合わせて変更します。 アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
4.  クライアント コンピュータで、コマンド プロンプトから Client.exe を起動します。  
  
5.  データ ソース コンピューターで、コマンド プロンプトから Datasource.exe を起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a>関連項目
