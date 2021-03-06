---
title: "Windows における .NET Core の前提条件"
description: "Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。"
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 16a72edde39e4857dbdfb400f195deb9975f993c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a>Windows における .NET Core の前提条件

この記事では、Windows で .NET Core アプリケーションを開発するために必要な依存関係を示します。 後述のサポート対象 OS のバージョンと依存関係は、Windows で .NET Core アプリを開発する次の 3 つの方法に適用されます。

* [コマンド ライン](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://www.visualstudio.com/downloads/)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET Core がサポートされている Windows バージョン

.NET Core は、次のバージョンでサポートされています。

* Windows 7 SP1
* Windows 8.1
* Windows 10、Windows 10 Anniversary Update (バージョン 1607) 以降のバージョン
* Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 R2 (フル サーバーまたは Server Core)
* Windows Server 2016 (フル サーバー、Server Core または Nano Server)

.NET Core 2.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。

.NET Core 1.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

1.1 およびそれ以前の .NET core は、Windows 10 および Windows Server 2016 より前のバージョンの Windows で実行されている場合、Visual C 再頒布可能が必要です。 この依存関係は、.NET Core インストーラーにより自動でインストールされます。

次の場合には、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685) を手動でインストールする必要があります。

   * [インストーラー スクリプト](./tools/dotnet-install-script.md)を使用して .NET Core をインストールする。
   * 自己完結型の .NET Core アプリケーションを展開する。

> [!NOTE]
> <em>Windows 7 および Windows Server 2008 コンピューターのみ:</em><br>
> Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/help/2533623) をインストールしていることを確認してください。

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 の前提条件

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。  [Visual Studio 2017](#visual-studio-2017) では、Windows 上に .NET Core アプリ用の統合開発環境が提供されます。

Visual Studio 2017 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)を参照してください。
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Visual Studio 2017 で .NET Core 2.x アプリを開発するには、次の手順を実行します。

 1. (**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 バージョン 15.3.0 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。
![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-15-3-workloads.jpg)

**.NET Core クロスプラットフォームの開発**ツールセットがインストールされると、Visual Studio 2017 で .NET Core 1.x が既定で使用されます。 Visual Studio 2017 で .NET Core 2.x がサポートされるように、.NET Core 2.x SDK をインストールします。

 2. [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core) をインストールします。
 3. 次の手順を使用して、既存または新規の .NET Core 1.x プロジェクトを .NET Core 2.x に再ターゲットします。
    * **[プロジェクト]** メニューの **[プロパティ]**をクリックします。 
    * **[ターゲット フレームワーク]** 選択メニューで、値を **[.NET Core 2.0]** に設定します。

![[ターゲット フレームワーク] メニュー項目で [.NET Core 2.0] が選択された Visual Studio 2017 のアプリケーション プロジェクト プロパティのスクリーンショット](./media/windows-prerequisites/Targeting-dotnetCore2.png)

.NET Core 2.x SDK がインストールされると、Visual Studio 2017 は .NET Core SDK 2.x を既定で使用し、次のアクションをサポートします。

  * 既存の .NET Core 1.x プロジェクトを開き、ビルドし、実行する。
  * .NET Core 1.x プロジェクトを .NET Core 2.x、ビルド、および実行に再ターゲット。
  * .NET Core 2.x の新しいプロジェクトを作成する。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
Visual Studio で .NET Core 1.x アプリを開発するには、(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 RTM (バージョン 15.0.26228.4) 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。
![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)
> [!IMPORTANT]
> .NET Core 1.x の開発に Visual Studio 2015 を使用することはできますが、次の理由からお勧めできません。
  > * .NET Core Tooling は、サポートされていないプレビュー バージョンです。
  > * プロジェクトは、非推奨の project.json ベースです。
>
> プロジェクト形式の変更の詳細については、[変更点の概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。
---

>[!TIP]
  > お使いの Visual Studio 2017 バージョンを確認するには、次の手順を実行します。
>
     > * **[ヘルプ]** メニューの **[About Microsoft Visual Studio]** (Microsoft Visual Studio のバージョン情報) を選択します。
     > * **[Microsoft Visual Studio のバージョン情報]** ダイアログで、バージョン番号を確認します。
>     * .NET Core 2.x アプリの場合は、Visual Studio 2017 バージョン 15.3 (26730.01) 以降です。
>     * .NET Core 1.x アプリの場合は、Visual Studio 2017 バージョン 15.0 (26228.04) 以降です。
