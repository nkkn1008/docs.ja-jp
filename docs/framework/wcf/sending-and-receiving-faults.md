---
title: "エラーの送受信"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5897d107fc27b56ffd1eb476dff1fa1d507f5de5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="sending-and-receiving-faults"></a>エラーの送受信
SOAP エラーは、エラー状態情報をサービスからクライアントに伝達します。双方向通信の場合は、相互運用可能な方法でクライアントからサービスにも伝達します。 通常、サービスは、カスタムのエラー コンテンツを定義し、そのエラー コンテンツを返すことができる操作を指定します  (詳細については、次を参照してください[を指定するエラーの定義および](../../../docs/framework/wcf/defining-and-specifying-faults.md)。)。ここでは、対応するエラー状態が発生したときにサービスまたは双方向クライアントがエラーを送信する方法、およびクライアントまたはサービス アプリケーションがエラーを処理する方法について説明します。 エラー処理の概要については[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]アプリケーションを参照してください[を指定して処理のエラー コントラクトおよびサービスの](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)します。  
  
## <a name="sending-soap-faults"></a>SOAP エラーの送信  
 宣言された SOAP エラーは、カスタム SOAP エラーの種類を指定する <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> を含む操作で発生します。 宣言されていない SOAP エラーとは、操作のコントラクトに指定されていないエラーです。  
  
### <a name="sending-declared-faults"></a>宣言されたエラーの送信  
 宣言された SOAP エラーを送信するには、SOAP エラーに該当するエラー状態を検出し、新しい <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> をスローします。この場合、型パラメーターは、その操作の <xref:System.ServiceModel.FaultContractAttribute> に指定されている型の新しいオブジェクトです。 次のコード例は、<xref:System.ServiceModel.FaultContractAttribute> 操作で `SampleMethod` の詳細な型と共に SOAP エラーを返すことができることを指定するために、`GreetingFault` を使用しています。  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 `GreetingFault` エラー情報をクライアントに伝達するには、適切なエラー状態をキャッチし、次のコード例に示すように、新しい <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> オブジェクトを引数として使用して `GreetingFault` 型の新しい `GreetingFault` をスローします。 クライアントが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント アプリケーションの場合、これはマネージ例外として認識されます。この場合の型は、<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> 型の `GreetingFault` です。  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>宣言されていないエラーの送信  
 宣言されていないエラーを送信すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションの問題をすばやく診断してデバッグできます。これは非常に便利ですが、デバッグ ツールとしての有用性は制限されています。 一般的に、デバッグ時には <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティを使用することをお勧めします。 この値を true に設定すると、クライアントはこのエラーを <xref:System.ServiceModel.FaultException%601> 型の <xref:System.ServiceModel.ExceptionDetail> 例外として認識します。  
  
> [!IMPORTANT]
>  マネージ例外が内部アプリケーション情報を開示する可能性があるので、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> を `true` に設定すると、個人の身元を確認できる情報またはその他の機密情報を含む内部サービス操作例外に関する情報を [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントで取得できます。  
>   
>  したがって、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> を `true` に設定することは、サービス アプリケーションを一時的にデバッグする方法としてのみお勧めできます。 さらに、このようにして未処理のマネージ例外を返すメソッドの WSDL には、<xref:System.ServiceModel.FaultException%601> 型の <xref:System.ServiceModel.ExceptionDetail> のコントラクトが含まれません。 クライアントは、デバッグ情報を適切に取得するために、([!INCLUDE[indigo2](../../../includes/indigo2-md.md)] オブジェクトとして <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> クライアントに返される) 不明な SOAP エラーの可能性について想定しておく必要があります。  
  
 宣言されていない SOAP エラーを送信するには、<xref:System.ServiceModel.FaultException?displayProperty=nameWithType> (つまり、ジェネリック型の <xref:System.ServiceModel.FaultException%601> でない) オブジェクトをスローし、文字列をコンストラクターに渡します。 これは、スローされた [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 例外として <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> クライアント アプリケーションに公開されるため、<xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> メソッドを呼び出して文字列を使用できます。  
  
> [!NOTE]
>  文字列型の SOAP エラーを宣言し、これを型パラメーターが <xref:System.ServiceModel.FaultException%601> の <xref:System.String?displayProperty=nameWithType> としてサービス内でスローすると、文字列値が <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> プロパティに割り当てられるため、<xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> から使用できません。  
  
## <a name="handling-faults"></a>エラーの処理  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントでは、クライアント アプリケーションに関係する通信中の SOAP エラーは、マネージ例外として発生します。 プログラムの実行中にはさまざまな例外が発生する可能性がありますが、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント プログラミング モデルを使用するアプリケーションは、通信の結果として、次の 2 種類の例外を処理できます。  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> オブジェクトは、操作が、指定されたタイムアウト期間を超えた場合にスローされます。  
  
 <xref:System.ServiceModel.CommunicationException> オブジェクトは、回復可能な通信エラー状態がサービスまたはクライアントで発生した場合にスローされます。  
  
 <xref:System.ServiceModel.CommunicationException> クラスには、<xref:System.ServiceModel.FaultException> および一般的な <xref:System.ServiceModel.FaultException%601> 型という 2 つの重要な派生型があります。  
  
 <xref:System.ServiceModel.FaultException> 例外は、予期しないエラーまたは操作コントラクト内に指定されていないエラーをリスナーが受信した場合にスローされます。この例外は、通常、サービスの <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティを `true` に設定してアプリケーションをデバッグしている場合に発生します。  
  
 <xref:System.ServiceModel.FaultException%601> 例外は、操作コントラクト内に指定されたエラーが、双方向操作 (つまり、<xref:System.ServiceModel.OperationContractAttribute> に <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> が設定されている `false` 属性を持つメソッド) への応答で受信された場合に、クライアントでスローされます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティが `true` に設定されている場合、クライアントは、この例外を <xref:System.ServiceModel.FaultException%601> 型の宣言されていない <xref:System.ServiceModel.ExceptionDetail> として認識します。 クライアントは、この特定のエラーをキャッチするか、<xref:System.ServiceModel.FaultException> の catch ブロックで処理できます。  
  
 通常、クライアントとサービスには、<xref:System.ServiceModel.FaultException%601>、<xref:System.TimeoutException>、および <xref:System.ServiceModel.CommunicationException> の各例外だけが関係します。  
  
> [!NOTE]
>  上記以外の例外も発生します。 予期しない例外には <xref:System.OutOfMemoryException?displayProperty=nameWithType> のような致命的なエラーも含まれますが、通常、アプリケーションでは、このようなメソッドをキャッチしません。  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>正しい順序でエラー例外をキャッチする  
 <xref:System.ServiceModel.FaultException%601> は <xref:System.ServiceModel.FaultException> から派生します。また、<xref:System.ServiceModel.FaultException> は <xref:System.ServiceModel.CommunicationException> からも派生します。したがって、これらの例外を正しい順序でキャッチすることが重要になります。 たとえば、try/catch ブロックで最初に <xref:System.ServiceModel.CommunicationException> がキャッチされたとします。その場合、すべての SOAP エラー (指定されている SOAP エラーおよび指定されていない SOAP エラー) はそこで処理され、カスタムの <xref:System.ServiceModel.FaultException%601> 例外を処理する後続の catch ブロックは呼び出されません。  
  
 指定した例外が 1 つの操作から複数返される場合があることに注意してください。 その場合は、エラーごとに型が異なるため、個別に処理する必要があります。  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>チャネルを閉じるときに例外を処理する  
 これまでの説明のほとんどは、アプリケーション メッセージの処理の過程で送信されるエラー (つまり、クライアント アプリケーションが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトの操作を呼び出す際に、クライアントによって明示的に送信されるメッセージ) に関するものでした。  
  
 ローカル オブジェクトでも、オブジェクトを破棄すると、リサイクル プロセスで起こる例外が発生したり、マスクされたりする場合があります。 同様のことは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトを使用する際にも発生します。 操作を呼び出すと、既に確立されている接続を通じてメッセージが送信されます。 また、チャネルを閉じると、すべての操作が正常に返されたとしても、接続を完全に閉じることができなかったり、接続が既に閉じたりしている場合には、例外がスローされる可能性があります。  
  
 通常、クライアント オブジェクトのチャネルは、次のいずれかが発生すると閉じられます。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント オブジェクトがリサイクルされるとき。  
  
-   クライアント アプリケーションが <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> を呼び出すとき。  
  
-   クライアント アプリケーションが <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> を呼び出すとき。  
  
-   クライアント アプリケーションが、セッションの終了操作となる操作を呼び出すとき。  
  
 いずれの場合でも、チャネルを閉じると、アプリケーション レベルで複雑な機能をサポートするためにメッセージを送信している可能性がある基になるチャネルをすべて閉じる操作を開始するように、チャネルに通知されます。 たとえば、コントラクトがセッションを要求している場合、バインディングは、セッションが確立されるまでサービス チャネルとメッセージを交換してセッションを確立しようとします。 チャネルが閉じられると、基になるセッション チャネルは、セッションが終了したことをサービスに通知します。 この場合、チャネルが既に中止されたり閉じられたりしている、または使用できない (たとえば、ネットワーク ケーブルが外れている) ときには、クライアント チャネルはサービス チャネルに対し、セッションが終了し例外が発生する可能性があることを通知できません。  
  
### <a name="abort-the-channel-if-necessary"></a>必要に応じてチャネルを中止する  
 チャネルを閉じると例外がスローされる可能性があるため、正しい順序でエラー状態をキャッチするだけでなく、呼び出しに使用されたチャネルを catch ブロックで中止することが重要です。  
  
 エラーによって操作に固有のエラー情報が伝えられた場合、他のユーザーがそのエラー情報を使用できるときはチャネルを中止する必要はありません (ただし、このような状況は非常にまれです)。 それ以外の場合は、チャネルを中止することをお勧めします。 これらのポイントのすべてを示すサンプルについては、次を参照してください。[予想例外](../../../docs/framework/wcf/samples/expected-exceptions.md)です。  
  
 次のコード例は、基本的なクライアント アプリケーションで、宣言されたエラーと宣言されていないエラーを含む SOAP エラー例外を処理する方法を示しています。  
  
> [!NOTE]
>  このサンプル コードは、`using` コンストラクトを使用していません。 チャネルを閉じると例外が発生する可能性があるため、まず [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントをアプリケーションで作成し、その [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を同じ try ブロックで開いて使用してから、閉じることをお勧めします。 詳細については、「 [WCF クライアントの概要](../../../docs/framework/wcf/wcf-client-overview.md)と[Using ステートメントに関する問題を回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)です。  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultException%601>  
 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
 [予期される例外](../../../docs/framework/wcf/samples/expected-exceptions.md)  
 [Using ステートメントに関する問題の回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)
