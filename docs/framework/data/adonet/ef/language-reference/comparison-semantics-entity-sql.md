---
title: "比較セマンティクス (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a>比較セマンティクス (Entity SQL)
次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。  
  
## <a name="explicit-comparison"></a>明示的な比較  
 等価演算  
  
-   =  
  
-   !=  
  
 順序付け操作  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 NULL 値が許容される操作  
  
-   IS_NULL  
  
-   IS NOT NULL  
  
## <a name="explicit-distinction"></a>明示的な区別  
 等価区別  
  
-   DISTINCT  
  
-   GROUP BY  
  
 順序付け区別  
  
-   ORDER BY  
  
## <a name="implicit-distinction"></a>暗黙的な区別  
 設定操作および述語 (等価)  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 項目述語 (等価)  
  
-   IN  
  
## <a name="supported-combinations"></a>サポートされている組み合わせ  
 次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。  
  
|**Type**|**=**<br /><br /> **!=**|**グループ化**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **点を除いて**<br /><br /> **設定**<br /><br /> **重複しています**|**IN**|**<   <=**<br /><br /> **>   >=**|**ORDER BY**|**NULL です。**<br /><br /> **NULL でないです。**|  
|-|-|-|-|-|-|-|-|  
|エンティティ型|Ref<sup>1</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|Ref<sup>1</sup>|  
|複合型|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|行|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|  
|プリミティブ型|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|  
|マルチセット|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|参照|[はい]<sup>5</sup>|[はい]<sup>5</sup>|[はい]<sup>5</sup>|[はい]<sup>5</sup>|Throw|Throw|[はい]<sup>5</sup>|  
|関連付け<br /><br /> 型|スロー<sup>3</sup>|Throw|Throw|Throw|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
  
 <sup>1</sup>特定のエンティティ型のインスタンスの参照は、暗黙的に比較すると、次の例で示すようにします。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 エンティティ インスタンスは、明示的な参照に対して比較できません。 明示的な参照に対する比較を行った場合は、例外がスローされます。 たとえば、次のクエリを実行すると、例外がスローされます。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>複合型のプロパティが比較可能な (ただし、すべてのプロパティが比較可能な) になるように、ストアに送信される前にフラット化します。 参照してください<sup>4 です。</sup>  
  
 <sup>3</sup>Entity Framework ランタイムでサポートされていないケースが検出し、プロバイダー/ストアは呼び出されず、意味のある例外をスローします。  
  
 <sup>4</sup>試行をすべてのプロパティを比較します。 比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。  
  
 <sup>5</sup>参照のすべての個々 の要素を比較 (エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む)。  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
