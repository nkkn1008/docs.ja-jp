---
title: "方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28e1667d086f26759e0129fc62d94ea79c68d880
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>方法 : デザイナーを使用して Windows フォームの Button コントロールをキャンセル ボタンとして指定する
すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを [キャンセル] ボタンを配置します。 ユーザーがフォーム上の他のコントロールにフォーカスがあるか、ESC キーを押すたびに [キャンセル] ボタンをクリックします。 このようなボタンは通常、ユーザー操作をコミットすることがなくすばやく操作を終了するために設定します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-designate-the-cancel-button"></a>[キャンセル] ボタンを指定するには  
  
1.  ボタンが置かれているフォームを選択します。  
  
2.  **プロパティ**ウィンドウで、設定、フォームの<xref:System.Windows.Forms.Form.CancelButton%2A>プロパティを<xref:System.Windows.Forms.Button>コントロールの名前。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: デザイナーを使用して Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
