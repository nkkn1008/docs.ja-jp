---
title: "コア通信 : Webhost サポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 707b97c49d6a6f5262719e91f8cb38fe7da53601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-webhost-support"></a>コア通信 : Webhost サポート
ここでは、Webhost サポートによって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|Hosting_CompatibilityServiceNotHosted|このサービスでは、ASP.NET 互換性が必要です。 また、IIS でホストする必要もあります。 Web.config で ASP.NET 互換性を有効にして IIS でサービスをホストするか、または AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode プロパティを Required 以外の値に設定します。|  
|Hosting_ListenerNotFoundForActivationInRecycling|指定されたアドレスをアクティブにリッスンしているチャネルはありません。 アプリケーションがリサイクルされる場合、サービスは閉じられます。|  
|Hosting_NonHTTPInCompatibilityMode|ASP.NET 互換性でサポートされるプロトコルは HTTP と HTTPS のみです。 指定されたエンドポイントを削除するか、アプリケーションに対して ASP.NET 互換性を無効にします。|  
|Hosting_ProcessNotExecutingUnderHostedContext|指定されたホスト プロセスは、現在のホスト環境内で呼び出すことができません。 この API では、アプリケーションの呼び出しがインターネット インフォメーション サービスまたは Windows プロセス アクティブ化サービス内で干すとされている必要があります。|  
|Hosting_ServiceCompatibilityRequire|このサービスは ASP.NET 互換性を必要とするため、アクティブにできません。 このアプリケーションに対して、ASP.NET 互換性が有効になっていません。 Web.config ファイルで ASP.NET 互換性を有効にするか、AspNetCompatibilityRequirementsAttribute.AspNetCompatibilit を設定します。|
