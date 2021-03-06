---
title: "ワークフロー サービスのホストの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0f473de9f16203d1b47ac227a1614b972b09e2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-workflow-services-overview"></a>ワークフロー サービスのホストの概要
ワークフロー サービスを実行するには、ホストされている必要があります。 <xref:System.ServiceModel.WorkflowServiceHost> は、複数のインスタンス、構成、および WCF メッセージングをサポートする標準ワークフロー ホストです (ワークフローはホストされるためにメッセージングを使用する必要はありません)。  また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。  WCF の <xref:System.ServiceModel.ServiceHost> と同様に、<xref:System.ServiceModel.WorkflowServiceHost> は任意のマネージ .NET アプリケーションでの自己ホスト、または IIS/WAS での Web ホスト (.xamlx ファイルとして) が可能です。  このセクションのトピックでは、ワークフロー サービスをホストする方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ワークフロー サービスのホスティング](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 ワークフロー サービスのホスティングについて説明します。  
  
 [ワークフロー サービス ホストの内部](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <xref:System.ServiceModel.WorkflowServiceHost> がどのように受信メッセージを処理するかについて説明します。  
  
 [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 ワークフロー サービス ホストの機能を拡張する方法について説明します。  
  
 [ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 ワークフロー インスタンスを作成できるエンドポイントを定義する方法について説明します。  
  
 [方法: IIS でサービス以外のワークフローのホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 IIS のワークフロー サービスではないワークフローのホスティングについて説明します。  
  
 [方法: Windows Server App Fabric でワークフロー サービス ホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Windows Server AppFabric の既存のワークフロー サービスをホストする方法について説明します。  
  
 [WorkflowServiceHost の構成](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 永続性、追跡、アイドル状態、および未処理の例外動作を制御する方法を説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>関連項目  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
