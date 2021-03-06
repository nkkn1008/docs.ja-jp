---
title: ".NET Framework による複数のプラットフォームの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ad765ca133b9757d7649f55b9dc100084a753e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>.NET Framework による複数のプラットフォームの開発
.NET Framework と Visual Studio を使用して、Microsoft プラットフォームと Microsoft 以外のプラットフォームの両方を対象としたアプリを開発できます。  
  
## <a name="options-for-cross-platform-development"></a>クロスプラットフォーム開発のオプション  
 複数プラットフォームを対象として開発する場合は、ソース コードやバイナリを共有し、.NET Framework コードと Windows ランタイム API の間で呼び出しを実行できます。  
  
|目的|用途|  
|-----------------------|------------|  
|Windows Phone 8.1 アプリと Windows 8.1 アプリの間でソース コードを共有する|**共有プロジェクト**(Visual Studio 2013 Update 2 でユニバーサル アプリ テンプレート)。<br /><br /> -現在 Visual Basic はサポートされません。<br /># を使用してプラットフォーム固有のコードを分離-`if`ステートメントです。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [Visual Studio を使用して、Windows および Windows Phone を対象とするアプリをビルド](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)(MSDN 記事)<br />-   [Visual Studio を使用してユニバーサル XAML アプリをビルドする](http://blogs.msdn.com/b/visualstudio/archive/2014/04/14/using-visual-studio-to-build-universal-xaml-apps.aspx)(ブログの投稿)<br />-   [Visual Studio で XAML Converged アプリのビルドを使用して](http://channel9.msdn.com/Events/Build/2014/3-591)(ビデオ)|  
|異なるプラットフォームを対象とするアプリ間でバイナリを共有する|**ポータブル クラス ライブラリ プロジェクト**プラットフォームに依存しないコード。<br /><br /> -この方法はビジネス ロジックを実装するコードを通常使用されます。<br />-には、Visual Basic または c# を使用できます。<br />API のサポートはプラットフォームによって異なります。<br />の Windows 8.1 および Windows Phone 8.1 を対象ポータブル クラス ライブラリ プロジェクトでは、Windows ランタイム Api と XAML をサポートします。 これらの機能は、古いバージョンのポータブル クラス ライブラリでは使用できません。<br />-必要な場合はインターフェイスまたは抽象クラスを使用してプラットフォーム固有のコードを抽象化ことができます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)(MSDN 記事)<br />-   [ポータブル クラス ライブラリの作成作業をするための方法](http://blogs.msdn.com/b/dsplaisted/archive/2012/08/27/how-to-make-portable-class-libraries-work-for-you.aspx)(ブログの投稿)<br />-   [MVVM をポータブル クラス ライブラリを使用して](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)(MSDN 記事)<br />-   [アプリ リソースのライブラリをターゲット複数のプラットフォームの](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)(MSDN 記事)<br />-   [.NET 移植性アナライザー](http://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b) (Visual Studio 拡張機能)|  
|Windows 8.1 および Windows Phone 8.1 以外のプラットフォームを対象としたアプリの間でソース コードを共有する|**リンクとして追加**機能します。<br /><br /> -この方法は、アプリケーション ロジックには両方のアプリを一般的な移植できないなんらかの理由に適しています。 この機能は Visual Basic または Visual C# のコードに使用できます。<br />     たとえば Windows Phone 8 と Windows 8 は Windows ランタイム API を共有しますが、ポータブル クラス ライブラリはこれらのプラットフォームでは Windows ランタイムをサポートしていません。 Windows Phone 8 アプリと、Windows 8 を対象とした Windows ストア アプリの間で共通する Windows ランタイム コードを共有するには、`Add as link` を使用できます。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [リンクとして追加のコードを共有する](http://msdn.microsoft.com/library/windowsphone/develop/jj714082\(v=vs.105\).aspx)(MSDN 記事)<br />-   [方法: 既存の項目をプロジェクトに追加](http://msdn.microsoft.com/library/vstudio/9f4t9t92\(v=vs.100\).aspx)(MSDN 記事)|  
|.NET Framework を使用して Windows ストア アプリを作成するか、または .NET Framework コードから Windows ランタイム API を呼び出します。|**Windows ランタイム Api** .NET Framework c# または Visual Basic コード、および Windows ストア アプリを作成する .NET Framework を使用するからです。 2 つのプラットフォーム間の API の違いについて注意してください。 ただし、これらの違いに対処するためのクラスがあります。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [.NET framework サポートの Windows ストア アプリおよび Windows ランタイム](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)(MSDN 記事)<br />-   [Windows ランタイムへの URI の引き渡し](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)(MSDN 記事)<br />-   <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>-->`System.IO.WindowsRuntimeStreamExtensions` (MSDN API リファレンス ページ)<br />-   <!--zz <xref:System.WindowsRuntimeSystemExtensions>-->`System.WindowsRuntimeSystemExtensions` (MSDN API リファレンス ページ)|  
|Microsoft 以外のプラットフォームに対応した .NET Framework アプリの開発|**ポータブル クラス ライブラリ参照アセンブリ**で .NET Framework、および Xamarin などの Visual Studio 拡張機能またはサード パーティ製のツールです。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [ポータブル クラス ライブラリすべてのプラットフォームで利用可能です。](http://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx) (ブログの投稿)<br />-   [Xamarin](http://xamarin.com/visual-studio) (Xamarin web サイト)|  
|JavaScript および HTML を使用したクロスプラットフォーム開発|**ユニバーサル アプリ テンプレート**Visual Studio 2013、Windows 8.1 および Windows Phone 8.1 用 Windows ランタイム Api に対して開発を 2 を更新します。 現在、クロスプラットフォーム アプリを開発するときに .NET Framework API で JavaScript と HTML を使用することはできません。<br /><br /> 詳細については、以下の資料を参照してください。<br /><br /> -   [JavaScript プロジェクト テンプレート](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx)<br />-   [Windows Phone に JavaScript を使用して Windows ランタイム アプリの移植](http://msdn.microsoft.com/library/windows/apps/dn636144.aspx)|
