---
title: "ICLRDataTarget3::GetExceptionContextRecord メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2e645222553f4000b300fa4f010ff81ff44d23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord メソッド
ターゲット プロセスに関連付けられたコンテキスト レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。 たとえば、ダンプ ターゲットについてなります経由で渡されるコンテキスト レコードと同じ、`ExceptionParam`への引数、 [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bufferSize`  
 [入力] 入力バッファー サイズ (バイト単位)。 これはコンテキスト レコードを格納するのに十分な大きさである必要があります。  
  
 `bufferUsed`  
 [出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。  
  
 `buffer`  
 [出力] コンテキスト レコードのコピーを受け取るメモリ バッファーへのポインター。 例外レコードとして返されます、[コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)型です。  
  
## <a name="return-value"></a>戻り値  
 戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。 次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|`S_OK`|メソッドが成功しました。 コンテキスト レコードは出力バッファーにコピーされました。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|コンテキスト レコードはターゲットに関連付けられていません。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|入力バッファーのサイズが足りないため、コンテキスト レコードを格納できません。|  
  
## <a name="remarks"></a>コメント  
 [コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)Windows SDK によって提供されたヘッダーで定義されているプラットフォームに固有の構造です。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRDataTarget3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionRecord メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [GetExceptionThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
