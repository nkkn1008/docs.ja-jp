---
title: "System.Math メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: af5e18b9c4334cfab26c9a84ac647bb433391ef1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="systemmath-methods"></a>System.Math メソッド
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Math> メソッドをサポートしていません。  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET との相違  
 .NET Framework で使用される丸めセマンティクスは SQL Server とは異なります。 <xref:System.Math.Round%2A> .NET Framework のメソッドは、実行*銀行型丸めが*.5 で終わる数値を丸めるをここでの代わりに次の上位桁に偶数桁の数字に最も近いです。 たとえば、2.5 は 2 に丸められ、3.5 は 4 に丸められます  (この方法は、大規模なデータ トランザクションで、値が大きくなる組織的バイアスの回避に役立ちます)。  
  
 SQL では、`ROUND` 関数は常に、0 から遠ざかる方向に丸めを実行します。 したがって、2.5 は 3 に丸められます。これは、2 に丸められる .NET Framework とは対照的です。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL の `ROUND` セマンティクスに到達するため、銀行型丸めを実装しようとしません。  
  
## <a name="see-also"></a>関連項目  
 [データ型および関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
