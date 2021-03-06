---
title: "ICorProfilerInfo3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3
helpviewer_keywords: ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 471fbae929723fb47dd6bc2a65196de1800717bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR: Common Language Runtime) とやり取りして、イベント監視を制御したり、情報を要求したりするために使用する各種メソッドを提供します。 `ICorProfilerInfo3`インターフェイスの拡張機能は、 [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)インターフェイスです。 このインターフェイスには、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 以降のバージョンでサポートされる新しいメソッドが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumJITedFunctions メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|以前に JIT でコンパイルされたすべての関数に対する列挙子を返します。|  
|[EnumModules メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|アプリケーションに読み込まれるマネージ モジュールのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。|  
|[GetAppDomainsContainingModule メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|指定したモジュールが読み込まれているアプリケーション ドメインの識別子を取得します。|  
|[GetFunctionEnter3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|によってプロファイラーに報告される関数のスタック フレームおよび引数情報を提供、 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)関数です。 中にのみ呼び出すことができます、`FunctionEnter3WithInfo`コールバック。|  
|[GetFunctionLeave3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|スタック フレームとによってプロファイラーに報告される関数の戻り値を提供、 [FunctionLeave3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)関数です。 中にのみ呼び出すことができます、`FunctionLeave3WithInfo`コールバック。|  
|[GetFunctionTailcall3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|によってプロファイラーに報告される関数のスタック フレームを提供、 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)関数です。 中にのみ呼び出すことができます、`FunctionTailcall3WithInfo`コールバック。|  
|[GetModuleInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|指定したモジュール ID に応じて、モジュールのファイル名、モジュールの親アセンブリの ID、およびモジュールのプロパティを示すビットマスクを返します。|  
|[GetRuntimeInformation メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|プロファイリングされているランタイムに関するバージョン情報を提供します。|  
|[GetStringLayout2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|文字列オブジェクトのレイアウトに関する情報を取得します。|  
|[GetThreadStaticAddress2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。|  
|[RequestProfilerDetach メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|プロファイラーをデタッチするようにランタイムに指示します。|  
|[SetEnterLeaveFunctionHooks3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|呼び出されるプロファイラー実装関数を指定します、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)関数。|  
|[SetEnterLeaveFunctionHooks3WithInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|呼び出されるプロファイラー実装関数を指定します、 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)マネージ関数のフックします。|  
|[SetFunctionIDMapper2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。 このメソッドによって拡張[icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)プロファイラーがランタイムの間で区別するために使用できるパラメーターを使用します。|  
  
## <a name="remarks"></a>コメント  
 CLR は、`ICorProfilerInfo3` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
 CLR から渡される、`ICorProfilerInfo3`へのプロファイラーの実装を使用して初期化中に、各コード プロファイラーのインターフェイス、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)または[ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)メソッドです。 その後、コード プロファイラーは `ICorProfilerInfo3` メソッドを呼び出して、CLR の制御下で実行中のマネージ コードに関する情報を取得できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
