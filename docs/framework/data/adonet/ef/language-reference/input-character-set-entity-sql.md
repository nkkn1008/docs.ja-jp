---
title: "入力文字セット (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a>入力文字セット (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、UTF-16 でエンコードされた UNICODE 文字を受け取ります。  
  
 文字列リテラルには、単一引用符で囲んだ任意の UTF-16 文字を含めることができます  たとえば、N'リテラル文字列' のように記述します。 文字列リテラルが比較される際は、元の UTF-16 の値が使用されます。 たとえば、N'ABC' は、日本語とラテンのコードページでは異なります。  
  
 コメントには、任意の UTF-16 文字を含めることができます。  
  
 エスケープされた識別子には、角かっこで囲んだ任意の UTF-16 文字を含めることができます  たとえば、[エスケープされた識別子] のように記述します。 UTF-16 エスケープされた識別子の比較では、大文字と小文字が区別されません。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、同じように表示されても別のコード ページに由来する文字の複数のバージョンを別々の文字として扱います。 たとえば、対応する文字が同じコード ページである場合、[ABC] は [abc] と同じものと見なされます。 ただし、同じ 2 つの識別子のコード ページが異なる場合は、同じものと見なされません。  
  
 空白は、任意の UTF-16 空白文字です。  
  
 改行は、任意の正規化 UTF-16 改行文字です。 たとえば、'\n' および '\r\n' は改行文字と見なされますが、'\r' は改行文字ではありません。  
  
 キーワード、式、および句読点には、ラテン語に正規化された任意の UTF-16 文字を使用できます。 たとえば、日本語のコードページの SELECT は有効なキーワードです。  
  
 キーワード、式、および区切り記号に使用できるのは、ラテン文字だけです。 `SELECT` は、日本語のコード ページではキーワードではありません。 +、-、*、/、=、(、)、‘、[、]、およびここに示されていないその他の言語コンストラクトに使用できるのは、ラテン文字だけです。  
  
 シンプルな識別子に使用できるのはラテン文字だけです。 元の値が比較されるので、比較の際のあいまいさが回避されます。 たとえば、[ABC] は、日本語とラテン語のコードページでは異なります。  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
