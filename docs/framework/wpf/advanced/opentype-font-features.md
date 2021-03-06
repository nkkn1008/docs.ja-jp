---
title: "OpenType フォントの機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c80769a1563953fc412afc6baeffcb91b49667d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="opentype-font-features"></a>OpenType フォントの機能
このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] における [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント技術の主要機能の概要を説明します。  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType フォントの書式  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント書式は [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] フォント書式の拡張で、PostScript フォント データのサポートが追加されています。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント書式は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] および Adobe Corporation により共同開発されました。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントおよび [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントをサポートするオペレーティング システム サービスでは、フォントに [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] アウトラインまたは CFF (PostScript) アウトラインのどちらが含まれていても、ユーザーは簡単な方法でフォントのインストールと使用ができます。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント書式では、次のような開発者の課題に対処します。  
  
-   より広範なマルチプラットフォームのサポート。  
  
-   国際文字セットのサポート強化。  
  
-   フォント データの保護強化。  
  
-   ファイルのサイズを小さくして、より効率的にフォントを配布。  
  
-   高度なテキスト編集コントロールの幅広いサポート。  
  
> [!NOTE]
>  Windows SDK には、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションで使用できるサンプルの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント セットが含まれています。 これらのフォントでは、このトピックで説明していく機能の大半が提供されています。 詳細については、「[OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)」を参照してください。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォント書式の詳細については、[OpenType の仕様](http://go.microsoft.com/fwlink/?LinkId=96731)に関するページを参照してください。  
  
### <a name="advanced-typographic-extensions"></a>高度なテキスト編集の拡張機能  
 高度なテキスト編集のテーブル ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] レイアウト テーブル) では、[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] または CFF アウトラインを使用してフォントの機能を拡張しています。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] レイアウトのフォントには、フォントの機能を拡張する追加の情報が含まれ、高品質の国際タイポグラフィをサポートします。 ほとんどの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、利用可能な [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 機能全体のサブセットのみを公開するものです。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントには次のような特徴があります。  
  
-   合字、位置フォーム、代替、およびその他のフォント置換をサポートする、文字とグリフの間の充実したマッピング。  
  
-   2 次元配置とグリフ結合のサポート。  
  
-   フォントには明示的なスクリプトと言語情報が含まれるため、テキスト処理アプリケーションはそれに従って動作を調整可能。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] レイアウト テーブルについては、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] の仕様の[「フォント ファイル テーブル」](http://www.microsoft.com/typography/otspec/otff.htm)セクションで詳しく説明されています。  
  
 この概要の残りの部分では、幅と、視覚的にで関心のいくつかの柔軟性が導入されています[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]のプロパティによって公開される機能、<xref:System.Windows.Documents.Typography>オブジェクト。 このオブジェクトの詳細については、「[タイポグラフィ クラス](#typography_class)」を参照してください。  
  
<a name="variants"></a>   
## <a name="variants"></a>バリアント  
 バリアントを使用して、上付き文字と下付きなどのさまざまなタイポグラフィ スタイルを表示します。  
  
### <a name="superscripts-and-subscripts"></a>上付き/下付きの文字  
 <xref:System.Windows.Documents.Typography.Variants%2A>プロパティでは、上付き文字と下付き文字の値を設定することができます、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントです。  
  
 次のテキストは、Palatino Linotype フォントの上付き文字を示したものです。  
  
 ![OpenType の上付き文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
OpenType の上付き文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの上付き文字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 次のテキストは、Palatino Linotype フォントの下付き文字を表示します。  
  
 ![OpenType の下付き文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
OpenType の下付き文字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの下付き文字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上付き文字と下付き文字の装飾的な用途  
 上付き文字と下付き文字を使用して、大文字と小文字が混在したテキストに装飾的効果をつけることもできます。 次のテキストは、Palatino Linotype フォントの上付き文字と下付き文字を示したものです。 大文字には影響がないことに注目してください。  
  
 ![OpenType の上付き文字と下付き文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
OpenType の上付き文字と下付き文字を使用するテキスト  
  
 次のマークアップの例は、のプロパティを使用して、フォントの下付き文字の上付き文字とを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大文字  
 大文字は、大文字スタイルのグリフでテキストをレンダリングするタイポグラフィ形式のセットです。 通常、テキストをすべて大文字で表示すると、文字間隔が狭すぎるように見え、文字の印象と縦横比が重すぎるように感じられます。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] では、小型英大文字、超小型英大文字、タイトル用、大文字スペーシングを含め、大文字に関する多くのスタイル形式をサポートしています。 これらのスタイル形式を使用して、英大文字の外観を変えることができます。  
  
 次のテキストは、Pescadero フォントの標準の大文字と、その後に "SmallCaps" および "AllSmallCaps" のスタイルをあてた文字を示したものです。 この場合、同じフォント サイズは 3 つすべての単語の使用します。  
  
 ![OpenType の大文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
OpenType の大文字を使用するテキスト  
  
 次のマークアップの例は、英大文字のプロパティを使用して、Pescadero フォントを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。 "SmallCaps" 形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>タイトル用大文字  
 タイトル用大文字は、重みと縦横比が軽く、標準の大文字よりも洗練された印象を与えるように設計されています。 タイトル用大文字は、見出しとしてフォント サイズを大きくに用いられます。 次のテキストには、Pescadero フォントの通常の動作とタイトル用大文字が表示されます。 2 番目の行のテキストの幅の狭い縦線の幅に注意してください。  
  
 ![OpenType のタイトル大文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
OpenType のタイトル大文字を使用するテキスト  
  
 次のマークアップの例は、タイトル用大文字のプロパティを使用して、Pescadero フォントを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大文字スペーシング  
 大文字スペーシングは、テキストをすべて大文字にする場合に間隔を広くする機能です。 大文字は通常小文字とのブレンドに設計されます。 間で魅力的な間隔を表示し、大文字と小文字可能性がありますが密接すぎますすべて大文字を使用する場合。 次のテキストは、Pescadero フォントの通常の動作と大文字の間隔を表示します。  
  
 ![OpenType の大文字スペーシングを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
OpenType の大文字スペーシングを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pescadero フォントの大文字の間隔を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>合字  
 合字とは、2 つ以上のグリフを、より読みやすい、あるいはより魅力的なテキストにするために、1 つのグリフに形成したものです。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、4 種類の合字をサポートします。  
  
-   **標準合字**。 読みやすさを高めるように設計されています。 標準合字には、"fi"、"fl" および "ff" があります。  
  
-   **コンテキスト合字**。 合字を構成する文字の間の結合を向上させることによって、読みやすさを高めるよう設計されています。  
  
-   **随意合字**。 装飾を加える設計で、特に読みやすくなるようには設計されていません。  
  
-   **歴史的合字**。 歴史的な記述に相応しい設計で、特に読みやすくなるようには設計されていません。  
  
 次のテキストは、Pericles フォントの標準合字グリフを示したものです。  
  
 ![OpenType の標準合字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
OpenType の標準合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントの標準合字のグリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 次のテキストは、Pericles フォントの随意合字グリフを示したものです。  
  
 ![OpenType の随意合字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
OpenType の随意合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントの随意合字のグリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 既定では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントでは標準合字が有効です。 たとえば、Palatino Linotype フォントを使用する場合、標準合字 "fi"、"ff" および "fl" は組み合わせ文字グリフとして表示されます。 各標準合字の文字のペアが互いに接触することに注意してください。  
  
 ![OpenType の標準合字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
OpenType の標準合字を使用するテキスト  
  
 ただし、標準合字機能を無効にして、"ff" などの標準合字が、組み合わせ文字グリフとしてではなく、2 つの別々のグリフとして表示されるようにできます。  
  
 ![OpenType の標準合字を無効になっているテキストを使用して](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
OpenType の無効な標準合字を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの標準合字のグリフを無効にする方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>飾り付き  
 飾り付きは装飾的なグリフで、カリグラフィを連想させる、手の込んだ装飾が使用されます。 次のテキストには、Pescadero フォントの標準と飾り付きグリフが表示されます。  
  
 ![OpenType の標準と飾り付きグリフを使用するテキスト](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
OpenType の標準グリフと飾り付きグリフを使用するテキスト  
  
 飾り付きは、季節のご挨拶などの短いフレーズで装飾的な要素としてよく使用されます。 次のテキストは、イベントの名前の大文字を強調するのに巻き髭を使用します。  
  
 ![OpenType の巻き髭を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
OpenType の巻き髭を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、フォントの巻き髭を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>コンテキスト飾り付き  
 飾り付きグリフの特定の組み合わせでは、隣りあう文字の下に延びる部分が重なり合うなど、美しくない外観になる可能性があります。 コンテキスト スワッシュを使用するより優れた外観を生成する代替スワッシュ グリフを使用できます。 次のテキストは前に、とコンテキスト スワッシュが適用された後に、同じ単語を示します。  
  
 ![OpenType のコンテキスト巻き髭を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
OpenType のコンテキスト巻き髭を使用するテキスト  
  
 次のマークアップの例は、のプロパティを使用して、Pescadero フォント コンテキスト スワッシュを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>代替  
 代替文字は、標準的なグリフの代わりに使用できるグリフです。 次の例で使用される Pericles フォントなどの [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントには、テキストの異なる外観を作るのに使用できる代替グリフを含めることができます。 次のテキストは、Pericles フォントの標準グリフを示したものです。  
  
 ![OpenType の標準グリフを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
OpenType の標準グリフを使用するテキスト  
  
 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントには、標準グリフ セットに代替スタイルを提供する追加グリフが含まれています。 次のテキストでは、スタイル代替グリフが表示されています。  
  
 ![OpenType のスタイル代替グリフを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
OpenType のスタイル代替グリフを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Pericles フォントのスタイル代替グリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 次のテキストは、いくつか他のスタイル代替グリフの Pericles フォントを表示します。  
  
 ![OpenType のスタイル代替グリフを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
OpenType のスタイル代替グリフを使用するテキスト  
  
 次のマークアップの例では、これらの他のスタイル代替グリフを定義する方法を示します。  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>ランダムなコンテキスト代替  
 ランダムなコンテキスト代替は、単一文字に複数の代替グリフを提供します。 スクリプトの種類のフォントで実装された場合、この機能は、一連のランダムに選択されたグリフの外観にわずかに異なりますを使用して手書き入力をシミュレートできます。 次のテキストは、Lindsey フォントのランダムなコンテキスト代替グリフを使用します。 注意して、文字"a"が多少異なります外観  
  
 ![OpenType のランダムなコンテキスト代替グリフを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
OpenType のランダムなコンテキスト代替を使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Lindsey フォントのランダムなコンテキスト代替グリフを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>歴史的形式  
 歴史的形式は、過去に一般的であった表示形式です。 次のテキストには、「ボストン, Massachusetts」という語句が表示されます。 Palatino Linotype フォントのグリフの履歴フォームを使用します。  
  
 ![OpenType の履歴フォームを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
OpenType の履歴フォームを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの履歴フォームを定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>数値スタイル  
 OpenType フォントでは、テキスト内の数値に使用できる数多くの機能をサポートします。  
  
### <a name="fractions"></a>小数  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、スラッシュや横棒を使用した小数スタイルをサポートします。  
  
 次のテキストは、Palatino Linotype フォントの小数スタイルを示したものです。  
  
 ![OpenType を使用してテキストをスラッシュし、分数を積み上げ](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
OpenType の分数 (横) と分数 (縦) を使用するテキスト  
  
 次のマークアップの例は、分数のプロパティを使用して、Palatino Linotype フォント スタイルを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>旧式スタイルの数字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、旧式スタイルの数字形式をサポートします。 この形式は、もはや標準ではなくなったスタイルで数字を表示するのに便利です。 次のテキストは、Palatino Linotype フォントの標準と古いスタイルの数値表示形式で 18 世紀日付を表示します。  
  
 ![OpenType の古いスタイルの数字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
OpenType の古いスタイルの数字を使用するテキスト  
  
 次のテキストは、Palatino Linotype フォントの標準の数字と、旧式スタイルの数字を示したものです。  
  
 ![OpenType 古いスタイルの数字セットを使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
OpenType の古いスタイルの数字セットを使用するテキスト  
  
 次のマークアップの例のプロパティを使用して、Palatino Linotype フォントの古いスタイルの数字を定義する方法を示しています、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>プロポーショナルと表形式の数字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントはプロポーショナルと表形式の数字をサポートし、数字を扱うときに幅を調整します。 プロポーショナルの数字では、それぞれの数字は異なる幅を持つものとして扱われます。たとえば "1" は "5" より狭い幅です。 表形式の図は、位置が揃う垂直方向に、型が財務情報の読みやすさを向上できるように、等幅の数字として扱われます。  
  
 次のテキストは、Miramonte フォントを使用して最初の列に 2 つのプロポーショナル数字を表示します。 「5」と「1」数字の幅の違いに注意してください。 2 番目の列は、表形式の図の機能を使用して調整幅と同じ 2 つの数値を示します。  
  
 ![OpenType のプロポーショナル & 表形式の数字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
OpenType のプロポーショナルと表形式の数字を使用するテキスト  
  
 次のマークアップの例は、のプロパティを使用して、Miramonte フォント比例と表形式の数値を定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>スラッシュ付きゼロ  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] フォントは、英文字 "O" と数字の "0" の違いを強調するためのスラッシュ付きゼロの数字形式をサポートします。 スラッシュ付きゼロは、財務およびビジネス情報における ID によく使用されます。  
  
 次のテキストには、Miramonte フォントを使用して、サンプル注文識別子が表示されます。 最初の行は、標準の数字を使用します。 使用する 2 番目の線はスラッシュ ゼロ大文字の"O"により優れたコントラストを提供します。  
  
 ![OpenType を使用してテキストをスラッシュ ゼロ](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
OpenType のスラッシュ付きのゼロを使用するテキスト  
  
 次のマークアップの例を定義する方法を示しています。 スラッシュ ゼロのプロパティを使用して、Miramonte フォント、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>タイポグラフィ クラス  
 <xref:System.Windows.Documents.Typography>オブジェクトは一連の機能を公開する、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォントをサポートしています。 プロパティを設定して<xref:System.Windows.Documents.Typography>マークアップではを活用するドキュメントを作成することが簡単に[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]機能します。  
  
 次のテキストは、Pescadero フォントの標準の大文字と、その後に "SmallCaps" および "AllSmallCaps" のスタイルをあてた文字を示したものです。 この場合、同じフォント サイズは 3 つすべての単語の使用します。  
  
 ![OpenType の大文字を使用してテキストを](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
OpenType の大文字を使用するテキスト  
  
 次のマークアップの例は、英大文字のプロパティを使用して、Pescadero フォントを定義する方法を示します、<xref:System.Windows.Documents.Typography>オブジェクト。 "SmallCaps" 形式を使用する場合は、先頭の大文字は無視されます。  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 次のコード例では、前のマークアップの例と同じタスクを実行します。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>タイポグラフィ クラスのプロパティ  
 次の表は、プロパティ、値、および既定の設定、<xref:System.Windows.Documents.Typography>オブジェクト。  
  
|プロパティ|[値]|既定値|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|数値 - バイト|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Documents.Typography>  
 [OpenType の仕様](http://go.microsoft.com/fwlink/?LinkId=96731)  
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [OpenType フォント パックのサンプル](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)  
 [アプリケーションでのフォントのパッケージング](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
