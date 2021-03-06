---
title: "方法: コントロールの背景にテキストを描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>方法: コントロールの背景にテキストを描画する
コントロールの背景に直接テキストを描画するにはテキスト文字列を変換することで、<xref:System.Windows.Media.FormattedText>オブジェクト、およびコントロールのオブジェクトを描画<xref:System.Windows.Media.DrawingContext>です。 派生したオブジェクトの背景に描画用に、この手法を使用することもできます<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Canvas>と<xref:System.Windows.Controls.StackPanel>です。  
  
 ![背景としてテキストを表示するコントロール](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
カスタム テキスト背景のコントロールの例  
  
## <a name="example"></a>例  
 コントロールの背景を描画するには、新規作成<xref:System.Windows.Media.DrawingBrush>オブジェクトおよびオブジェクトの変換後のテキストを描画<xref:System.Windows.Media.DrawingContext>です。 その後、新しい割り当てる<xref:System.Windows.Media.DrawingBrush>コントロールの背景のプロパティにします。  
  
 次のコード例を作成する方法を示しています、<xref:System.Windows.Media.FormattedText>オブジェクトし、の背景を描画する<xref:System.Windows.Controls.Label>と<xref:System.Windows.Controls.Button>オブジェクト。  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.FormattedText>  
 [書式設定されたテキストの描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
