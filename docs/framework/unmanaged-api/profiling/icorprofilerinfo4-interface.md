---
title: "ICorProfilerInfo4 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR) イベントの監視の制御と要求情報を通信に使用するメソッドを提供します。 」を参照してください。 `ICorProfilerInfo4`インターフェイスは、その他の拡張機能`ICorProfilerInfo`インターフェイスです。 追加された、・ イン タイム (JIT) の再コンパイルをサポートする新しいメソッドを提供、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumJITedFunctions2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|以前に JIT コンパイルされ、JIT 再コンパイルしていたすべての関数の列挙子を返します。|  
|[EnumThreads メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|プロファイリングされたプロセスのすべてのマネージ スレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を取得します。|  
|[GetCodeInfo3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。|  
|[GetFunctionFromIP2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|マネージ コードの命令ポインターを指定された関数の JIT 再コンパイル バージョンにマップします。|  
|[GetILToNativeMapping2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Microsoft intermediate language (MSIL) が指定の関数の JIT 再コンパイル バージョンに含まれるコードのネイティブ オフセットへオフセットから、マップを取得します。|  
|[GetObjectSize2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|指定したオブジェクトのサイズを返します。|  
|[GetReJITIDs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|JIT 再コンパイルのすべてのバージョン指定の関数はまだ割り当てられていることを識別する Id の配列を返します。|  
|[InitializeCurrentThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|後続のプロファイラー API は、デッドロックを回避するため、同じスレッドで呼び出しの前に、現在のスレッドを初期化します。|  
|[RequestReJIT メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。|  
|[RequestRevert メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|指定された関数のすべてのインスタンスを元のバージョンに戻します。|  
  
## <a name="remarks"></a>コメント  
 CLR は、`ICorProfilerInfo4` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
