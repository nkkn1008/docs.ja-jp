---
title: "方法: Web サービスを非同期で呼び出す (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6410ef93a706c047047aa24b3d47f8915e928015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>方法: Web サービスを非同期で呼び出す (Visual Basic)
この例では、Web サービスの非同期ハンドラー イベントにハンドラーをアタッチして、非同期メソッド呼び出しの結果を取得できるようにします。 この例で使用した Web サービスは、http://www.xmethods.net にある DemoTemperatureService です。  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 統合開発環境 (IDE) でプロジェクトの Web サービスを参照すると、この Web サービスが `My.WebServices` オブジェクトに追加され、指定された Web サービスにアクセスするためのクライアント プロキシ クラスが IDE によって生成されます。  
  
 プロキシ クラスを使用すると、Web サービス メソッドを同期的に呼び出すことができ、この場合、アプリケーションは関数が完了するまで待機します。 また、プロキシはメソッドを非同期的に呼び出すために使用できる追加のメンバーを作成します。 Web サービス関数 *NameOfWebServiceFunction* ごとに、プロキシは *NameOfWebServiceFunction*`Async` サブルーチン、*NameOfWebServiceFunction*`Completed` イベント、および *NameOfWebServiceFunction*`CompletedEventArgs` クラスを作成します。 この例では、DemoTemperatureService Web サービスの `getTemp` 関数にアクセスする非同期メンバーの使用方法を示します。  
  
> [!NOTE]
>  ASP.NET では `My.WebServices` オブジェクトがサポートされていないため、このコードは Web アプリケーションでは動作しません。  
  
### <a name="to-call-a-web-service-asynchronously"></a>Web サービスを非同期的に呼び出すには  
  
1.  http://www.xmethods.net にある DemoTemperatureService Web サービスを参照します。 アドレスは次のとおりです。  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  `getTempCompleted` イベントのイベント ハンドラーを追加します。  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  `Handles` ステートメントを使用して、イベント ハンドラーを `My.WebServices` オブジェクトのイベントに関連付けることはできません。  
  
3.  イベント ハンドラーが `getTempCompleted` イベントに追加されたかどうかを追跡するためのフィールドを追加します。  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  必要に応じて、イベント ハンドラーを `getTempCompleted` イベントに追加するメソッドを追加し、`getTempAsynch` メソッドを呼び出すメソッドを追加します。  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     `getTemp` Web メソッドを非同期的に呼び出すには、`CallGetTempAsync` メソッドを呼び出します。 Web メソッドが終了すると、その戻り値が `getTempCompletedHandler` イベント ハンドラーに渡されます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションの Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
