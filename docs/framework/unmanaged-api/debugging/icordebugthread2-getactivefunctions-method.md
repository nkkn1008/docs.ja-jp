---
title: "ICorDebugThread2::GetActiveFunctions メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetActiveFunctions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1f7f416a5441b788394e93a98d274d02fa2ec2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions メソッド
このスレッドのフレームのそれぞれに、アクティブな関数に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cFunctions`  
 [in] `pFunctions` 配列のサイズ。  
  
 `pcFunctions`  
 [out]返されたオブジェクトの数へのポインター、`pFunctions`配列。 返されるオブジェクトの数は、スタック上のマネージ フレームの数と等しくなります。  
  
 `pFunctions`  
 [入力、出力].このスレッドのフレームでアクティブな関数についての情報を含む各 COR_ACTIVE_FUNCTION オブジェクトの配列。  
  
 最初の要素は、リーフ フレームとスタックのルートまでさかのぼりますに使用されます。  
  
## <a name="remarks"></a>コメント  
 場合`pFunctions`が入力で null`GetActiveFunctions`はスタック上にある関数の数のみを返します。 つまり場合、`pFunctions`が入力で null`GetActiveFunctions`値を返しますでのみ`pcFunctions`です。  
  
 `GetActiveFunctions`メソッドは最適化の手法として、スタック トレースでのフレームから同じ情報を取得経由でありがありました ICorDebugILFrame オブジェクトに完全なスタック トレースでのフレームのみが含まれています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
