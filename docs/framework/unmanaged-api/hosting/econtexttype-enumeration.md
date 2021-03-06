---
title: "EContextType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EContextType
api_location: mscoree.dll
api_type: COM
f1_keywords: EContextType
helpviewer_keywords: EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73e6e9a1f1118a524b86b3711c0c7a6af4777f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="econtexttype-enumeration"></a>EContextType 列挙型
現在実行中のスレッドのセキュリティ コンテキストをについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eCurrentContext`|共通言語ランタイム (CLR) の呼び出し時に現在のスレッドのコンテキストを示す、 [ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)メソッド、またはへの呼び出しで CLR によって要求されたコンテキスト、 [Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)メソッドです。|  
|`eRestrictedContext`|対象では、ホストは、ガベージ コレクターでは、またはクラスまたはモジュール コンス トラクターなど、低い特権コンテキストを示します。|  
  
## <a name="remarks"></a>コメント  
 いずれかの CLR が用意されて、`EContextType`値への呼び出しのパラメーター値として、`IHostSecurityManager::GetSecurityContext`と`IHostSecurityManager::SetSecurityContext`メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [ホスティングの列挙体](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
