---
title: "暗黙の変換 &#39;&lt;typename1&gt;&#39; の &#39;&lt;typename2&gt;&#39; の値 &#39; のコピー中ByRef &#39;パラメーター &#39;&lt;parametername&gt;&#39; 一致する引数に戻します。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>暗黙の変換 &#39;&lt;typename1&gt;&#39; の &#39;&lt;typename2&gt;&#39; の値 &#39; のコピー中ByRef &#39;パラメーター &#39;&lt;parametername&gt;&#39; 一致する引数に戻します。
プロシージャが呼び出される、 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)対応するパラメーターとは異なる型の引数。  
  
 引数を渡す場合`ByRef`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]場合がありますの参照を渡す代わりにプロシージャ内のローカル変数に引数の値をコピーします。 このような場合は、プロシージャから返されるときに、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は呼び出し元のコードの引数にローカル変数の値をコピーする必要があります。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 型が異なる場合、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] は双方向で変換する必要があります。 使用できないため`CType`または暗黙的なプロシージャ引数、またはパラメーター、そのような変換でその他の変換キーワードのいずれかが常にします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC41999  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能な場合は、プロシージャのパラメーターと同じ型の呼び出し元引数を使用して、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で変換する必要がないようにします。  
  
-   パラメーターの型の異なる型引数を持つプロシージャを呼び出す必要がある場合は、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`です。  
  
## <a name="see-also"></a>関連項目  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
