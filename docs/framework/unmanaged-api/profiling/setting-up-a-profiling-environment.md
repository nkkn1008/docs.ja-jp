---
title: "プロファイル環境の設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ff2c57be82166ecf5eb8a012491044eb2cb79d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="setting-up-a-profiling-environment"></a>プロファイル環境の設定
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では、プロファイル機能が大幅に変更されています。  
  
 マネージ プロセス (アプリケーションまたはサービス) は、起動されると、共通言語ランタイム (CLR: Common Language Runtime) を読み込みます。 CLR は、初期化されると、プロファイラーに接続する必要があるかどうかを決定するために、次の 2 つの環境変数を評価します。  
  
-   COR_ENABLE_PROFILING: この環境変数が存在し、1 に設定されている場合にのみ、CLR はプロファイラーに接続します。  
  
-   COR_PROFILER: COR_ENABLE_PROFILING のチェックに合格した場合、CLR はこの CLSID または ProgID (あらかじめレジストリに格納されている) を持つプロファイラーに接続します。 COR_PROFILER 環境変数は文字列として定義されます。以下に 2 つの例を示します。  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 CLR アプリケーションのプロファイリングを行うには、COR_ENABLE_PROFILING 環境変数および COR_PROFILER 環境変数を設定してから、アプリケーションを実行する必要があります。 また、プロファイラー DLL が登録済みであることも確認してください。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降では、プロファイラーを登録する必要はありません。  
  
> [!NOTE]
>  .NET Framework version 2.0、3.0、および 3.5 のプロファイラーを使用する、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]し、それ以降のバージョンでは、COMPLUS_ProfAPI_ProfilerCompatibilitySetting 環境変数を設定する必要があります。  
  
## <a name="environment-variable-scope"></a>環境変数名のスコープ  
 COR_ENABLE_PROFILING 環境変数と COR_PROFILER 環境変数をどのように設定するかによって、これらの変数が影響を及ぼすスコープが決定します。 これらの変数は、次のいずれかの方法で設定できます。  
  
-   変数を設定した場合、 [icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)呼び出し、時に実行しているアプリケーションにのみ適用されます。 (そのアプリケーションから起動されて環境を継承する他のアプリケーションにも適用されます)。  
  
-   コマンド プロンプト ウィンドウで設定した変数は、そのウィンドウから起動したすべてのアプリケーションに適用されます。  
  
-   ユーザー レベルで設定した変数は、エクスプローラーを使用して開始するすべてのアプリケーションに適用されます。 変数を設定した後にコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 ユーザー レベル環境変数を設定するには、右**マイ コンピューター**、 をクリックして**プロパティ**をクリックして、 **詳細設定**  タブで、をクリックして**環境変数**、変数を追加し、**ユーザー変数** ボックスの一覧です。  
  
-   コンピューター レベルで設定した変数は、そのコンピューターで起動するすべてのアプリケーションに適用されます。 そのコンピューターでコマンド プロンプト ウィンドウを開くと、それらの環境設定が表示されます。そのウィンドウから起動するアプリケーションにも同じ設定が適用されます。 つまり、そのコンピューター上のすべてのマネージ プロセスがプロファイラーと共に起動します。 コンピューター レベルで環境変数を設定するには、右**マイ コンピューター**、 をクリックして**プロパティ**をクリックして、 **詳細設定**  タブで、をクリックして**環境変数**、変数を追加して、**システム変数**ボックスの一覧し、コンピューターを再起動します。 再起動後、変数はシステム全体で試用できるようになります。  
  
 Windows サービスのプロファイリングを行う場合は、環境変数を設定した後、コンピューターを再起動してプロファイラー DLL を登録する必要があります。 これらの考慮事項の詳細については、セクションを参照して[Windows サービスのプロファイリング](#windows_service)です。  
  
## <a name="additional-considerations"></a>その他の考慮事項  
  
-   プロファイラー クラスを実装して、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)と[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)インターフェイスです。 .NET Framework Version 2.0 では、プロファイラーは `ICorProfilerCallback2` を実装する必要があります。 実装していない場合、`ICorProfilerCallback2` は読み込まれません。  
  
-   一度に 1 つのプロファイラーのみが、指定された環境でプロセスのプロファイリングを行うことができます。 2 つの異なるプロファイラーを別々の環境に登録することはできますが、各プロファイラーは別々のプロセスのプロファイリングを行う必要があります。 プロファイラーは、インプロセス COM サーバー DLL として実装する必要があります。この DLL は、プロファイリング対象プロセスと同じアドレス領域にマップされます。 つまり、プロファイラーはインプロセスで実行されます。 .NET Framework では、これ以外の種類の COM サーバーはサポートしていません。 たとえば、プロファイラーがリモート コンピューターからアプリケーションを監視する場合は、各コンピューターにコレクター エージェントを実装する必要があります。 実装したエージェントは、結果をまとめて中央のデータ収集用コンピューターに送信します。  
  
-   プロファイラーはインプロセスでインスタンス化される COM オブジェクトであるため、プロファイリングされる各アプリケーションに専用のプロファイラーのコピーが存在します。 したがって、単一のプロファイラー インスタンスが複数のアプリケーションからのデータを処理する必要はありません。 ただし、プロファイラーのログ コードに、他のプロファイリング対象アプリケーションからのログ ファイルの上書きを回避するロジックを追加する必要があります。  
  
## <a name="initializing-the-profiler"></a>プロファイラーの初期化  
 両方の環境変数のチェックに合格すると、CLR は COM `CoCreateInstance` 関数と同様の方法でプロファイルのインスタンスを作成します。 このプロファイルについては、`CoCreateInstance` の直接呼び出しによる読み込みは行われません。 そのため、スレッド処理モデルの設定が必要な `CoInitialize` の呼び出しが回避されます。 CLR は呼び出し、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)プロファイラーのメソッドです。 このメソッドのシグネチャは次のとおりです。  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 プロファイラーを照会する必要があります`pICorProfilerInfoUnk`の[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)または[ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)インターフェイス ポインターをし、プロファイル中に後で詳細を要求できるように保存します。  
  
## <a name="setting-event-notifications"></a>イベント通知の設定  
 プロファイラーを呼び出して、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)通知のカテゴリを求めているを指定します。 たとえば、関数の Enter および Leave の通知とガベージ コレクションの通知のみを確認する場合は、次のように指定します。  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 通知マスクをこのように設定することによって、プロファイラーで受け取る通知を制限できます。 この方法は、単純なプロファイラーまたは特別な目的を持つプロファイラーを作成するときに役立ちます。 また、プロファイラーが無視するだけの通知を送信するのに消費される CPU 時間が削減されます。  
  
 特定のプロファイラー イベントは変更できません。 つまり、これらのイベントが `ICorProfilerCallback::Initialize` コールバックで設定されるとすぐに、イベントはオフにできなくなり、新しいイベントをオンにすることもできません。 変更できないイベントを変更しようとすると、失敗を表す HRESULT が `ICorProfilerInfo::SetEventMask` から返されます。  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Windows サービスのプロファイリング  
 Windows サービスのプロファイリングは、共通言語ランタイム アプリケーションのプロファイリングと同様です。 どちらのプロファイリング操作も環境変数で有効にできます。 Windows サービスはオペレーティング システムの起動時に開始されるため、前の環境変数をあらかじめ作成し、必要な値を設定しておく必要があります。 さらに、プロファイル DLL を事前にシステムに登録しておく必要もあります。  
  
 環境変数 COR_ENABLE_PROFILING と COR_PROFILER を設定し、プロファイラー DLL を登録したら、これらの変更が Windows サービスで検出されるようにするために、ターゲット コンピューターを再起動してください。  
  
 これらの変更を行うと、プロファイリングがシステム全体で有効になります。 以降に実行するすべてのマネージ アプリケーションがプロファイルされるのを避けるには、ターゲット コンピューターを再起動した後で、システム環境変数を削除します。  
  
 この方法では、すべての CLR プロセスもプロファイリングの対象になります。 プロファイラーは、ロジックを追加する必要があります、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)現在のプロセスは対象とするかどうかを検出するためにコールバックします。 プロファイリングの対象ではない場合、プロファイラーは、初期化を実行せずにコールバックからエラーを返すことができます。  
  
## <a name="see-also"></a>関連項目  
 [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
