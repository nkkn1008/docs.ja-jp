---
title: "正規関数を呼び出す方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a>正規関数を呼び出す方法
<xref:System.Data.Objects.EntityFunctions> クラスには、LINQ to Entities クエリで使用する正規関数を公開するメソッドが含まれています。 正規関数については、「[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> クラスの <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> メソッドと <xref:System.Data.Objects.EntityFunctions> メソッドには正規関数に相当するものがありません。  
  
 値のセットに対して計算を実行して 1 つの値を返す正規関数 (集計正規関数とも呼ばれる) は、直接呼び出すことができます。 他の正規関数は、LINQ to Entities クエリの一部としてしか呼び出すことができません。 集計関数を直接呼び出すには、その関数に <xref:System.Data.Objects.ObjectQuery%601> を渡す必要があります。 詳細については、以下の 2 番目の例を参照してください。  
  
 一部の正規関数は、LINQ to Entities クエリで共通言語ランタイム (CLR) メソッドを使用して呼び出すことができます。 正規関数にマップされる CLR メソッドの一覧は、次を参照してください。[正規の関数マッピングに CLR メソッド](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)です。  
  
## <a name="example"></a>例  
 次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。 この例で実行される LINQ to Entities クエリは、<xref:System.Data.Objects.EntityFunctions.DiffDays%2A> メソッドを使用して、`SellEndDate` と `SellStartDate` の差が 365 日よりも少ないすべての製品を返します。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、 [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832)です。 この例では、<xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> の小計の標準偏差を返す集計 `SalesOrderHeader` メソッドを直接呼び出します。 <xref:System.Data.Objects.ObjectQuery%601> は関数に渡されているため、LINQ to Entities クエリに含まれていなくても呼び出すことができる点に注意してください。  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Entities クエリで関数の呼び出し](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
