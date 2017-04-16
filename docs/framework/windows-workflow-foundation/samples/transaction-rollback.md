---
title: "トランザクションのロールバック | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# トランザクションのロールバック
このサンプルでは、アンビエント <xref:System.Activities.RuntimeTransactionHandle> にアクセスしてアンビエント トランザクションを取得し、そのトランザクションを明示的にロールバックするカスタム <xref:System.Activities.NativeActivity> を作成する方法を示します。  
  
## サンプルの詳細  
 ワークフローでは、最も外側の <xref:System.Activities.Statements.TransactionScope> または <xref:System.ServiceModel.Activities.TransactedReceiveScope> が完了すると、トランザクションは自動的に完了します。未処理の例外がスコープの境界を越えて伝達されると、トランザクションは暗黙的にロールバックします。ただし、例外をスローせずにトランザクションを明示的にロールバックすることが有効な場合もあります。この場合、このサンプルのアクティビティのようなカスタム ロールバック アクティビティを使用して、アンビエント トランザクションを明示的に中止し、必要に応じて例外の理由を提供することができます。  
  
 `RollbackActivity` は、アンビエント <xref:System.Activities.RuntimeTransactionHandle> を取得するために実行プロパティにアクセスする必要があるので、<xref:System.Activities.NativeActivity> になります。`Execute` メソッドでは、<xref:System.Activities.RuntimeTransactionHandle> を取得し、アンビエント ランタイム トランザクションなしでアクティビティが使用されたことを示す `null` であるかどうかを確認します。次にトランザクションを取得し、`null` が存在するかどうかを再度確認します。ランタイム トランザクションを初期化せずにアンビエント <xref:System.Activities.RuntimeTransactionHandle> を取得することができます。最後に、<xref:System.Transactions.Transaction.Rollback%2A> を呼び出し、ユーザー指定の例外、またはアクティビティによってトランザクションがロールバックされたことを示す汎用的な例外を指定して、トランザクションを中止します。  
  
 このサンプルのワークフローは、`RollbackActivity` の実行の前後にトランザクションの状態を印刷する本体を持つ <xref:System.Activities.Statements.TransactionScope> で構成されます。トランザクションがロールバックされた場合でも、<xref:System.Activities.Statements.TransactionScope> は完了まで実行され、本体が完了するまでワークフローは中止されないことに注意してください。ワークフローが中止されるのは、<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> プロパティが既定で `true` に設定されるためです。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に TransactionRollback.sln ソリューションを読み込みます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## 参照  
 [トランザクション](../../../../docs/framework/windows-workflow-foundation//workflow-transactions.md)