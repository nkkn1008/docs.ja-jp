---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 612f2eb04ae3449fddc8fb871683b26138d046d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>メソッド  
 HttpTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 HttpTransportBindingElement クラスには、次のプロパティがあります。  
  
### <a name="allowcookies"></a>AllowCookies  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP リスナーにより処理されているクライアント要求の認証に使用する認証方式です。  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 プロキシをローカル アドレスで無視するかどうかを示す値です。  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 有効な場合は、HTTP 接続がアクティビティ レベルとは無関係に維持されます。  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 バッファー プールの最大サイズ。  
  
### <a name="proxyaddress"></a>ProxyAddress  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP 要求に使用するプロキシのアドレスを格納する URI です。  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP プロキシにより処理されているクライアント要求の認証に使用する認証方式です。  
  
### <a name="realm"></a>Realm  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 認証領域。  
  
### <a name="transfermode"></a>TransferMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージが要求や応答をバッファーするか、ストリーミングするかを指定する値です。  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 サーバー上で安全ではない接続共有を有効にするかどうかを示す値です。  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 ユーザー固有の設定ではなく、コンピューター全体のプロキシ設定を使用するかどうかを示す値です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
