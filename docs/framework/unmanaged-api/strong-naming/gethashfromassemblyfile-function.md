---
title: "GetHashFromAssemblyFile 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1598e4e332525f87392ae5b0ad486a735e760651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfile-function"></a>GetHashFromAssemblyFile 関数
指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szFilePath`  
 [in]ハッシュされるファイルへのパス。  
  
 `piHashAlg`  
 [入力、出力].ハッシュ アルゴリズムを指定する定数。 0 を既定のハッシュ アルゴリズムを使用します。  
  
 `pbHash`  
 [out]返されるハッシュ バッファー。  
  
 `cchHash`  
 [in]場合は、要求された最大サイズ`pbHash`です。  
  
 `pchHash`  
 [out]サイズをバイト単位で返される`pbHash`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [GetHashFromAssemblyFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [GetHashFromAssemblyFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
