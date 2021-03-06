---
title: "ICorDebugType::GetType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20e2a1415d5dda9c4097d984af46942ebcf2365a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType メソッド
共通言語ランタイム (CLR) のネイティブ型を記述する CorElementType 値を取得<xref:System.Type>この ICorDebugType によって表されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ty`  
 [out]値へのポインター、`CorElementType`を CLR を示す列挙体<xref:System.Type>この`ICorDebugType`を表します。  
  
## <a name="remarks"></a>コメント  
 場合の値`ty`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE のいずれかが、 [icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)メソッドを呼び出すことが、ジェネリック型のインスタンス化されていない型を取得します。 それ以外の場合、呼び出す必要はありません`ICorDebugType::GetClass`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
