---
title: "浮動小数点数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3e8ac8b5a97c62bb173fba57ac8aeb26a1dad42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="floating-point-numbers"></a>浮動小数点数
このトピックでは、開発者が [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] で浮動小数点数を扱う際によく遭遇する問題について説明します。 これらはコンピューターによる浮動小数点数の格納方法に起因する問題であり、<xref:System.Data.SqlClient> や <xref:System.Data.OracleClient> など、特定のプロバイダーに固有の問題ではありません。  
  
 通常、浮動小数点数には正確なバイナリ表現がありません。 その代わり、数値の近似値がコンピューターによって格納されます。 浮動小数点数を表現するために使用されるバイナリ桁数はそのときどきで異なります。 浮動小数点数をある表現から別の表現に変換した場合、その数値の最下位の桁がわずかに変わってしまう場合があります。 一般に、変換が発生するのは型をキャストしたときです。 この差異は、変換を 1 つのデータベース内で行うか、データベースの値を表す型間で行うか、型と型の間で行うかに関係なく生じます。 このような差が生じてしまう関係上、論理的には等しくなるはずの数値でも、最下位の桁の値が異なる場合があります。 数値の有効桁数が、本来の桁数よりも大きくなったり小さくなったりすることもあります。 また、数値を文字列として表した場合に、期待した値が得られない場合もあります。  
  
 こうした影響を最小限に抑えるには、使用できる数値型のうち、最も近い型を使用する必要があります。 たとえば、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] を使用している場合、実数型の Transact-SQL 値を浮動小数点型の値に変換すると、厳密には数値が変わってしまう場合があります。 同様に、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、<xref:System.Single> を <xref:System.Double> に変換すると、予想外の結果になることがあります。 いずれの場合も、最善の方法は、アプリケーションのすべての値に同じ数値型を使用することです。 固定精度の decimal 型を使用したり、あらかじめ浮動小数点数を固定精度の decimal 型にキャストしておく方法もあります。  
  
 等価比較の問題を回避するには、最下位桁の差異を無視できるようにアプリケーションをコーディングすることを検討してください。 たとえば、2 つの数値の等価性を比較するのではなく、一方の数値からもう一方の数値を減算するようにします。 その差が丸め処理の許容範囲内であれば、2 つの数値が等価であるものとして処理できます。  
  
## <a name="see-also"></a>関連項目  
 [浮動小数点数の精度の低下](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
