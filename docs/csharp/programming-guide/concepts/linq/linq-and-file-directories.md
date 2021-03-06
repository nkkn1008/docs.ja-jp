---
title: "LINQ とファイル ディレクトリ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62c7ee272c788ca687b84bb76a853e58f83f69ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-c"></a>LINQ とファイル ディレクトリ (C#)
多くのファイル システム操作は基本的にクエリであるため、LINQ での使用に最適です。  
  
 ここで示すクエリは破壊的ではないことに注意してください。 元のファイルやフォルダーの内容が変更されることはありません。 これは、クエリは副作用を引き起こすべきではないという規則に従っています。 一般に、参照元データを変更するコード (create、update、または delete の各演算子を実行するクエリなど) は、単にデータを照会するだけのコードとは分離する必要があります。  
  
 このセクションでは、以下のトピックについて説明します。  
  
 [方法: 指定された属性または名前のファイルを照会する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <xref:System.IO.FileInfo> オブジェクトで 1 つ以上のプロパティを調べ、ファイルを検索する方法を示します。  
  
 [方法: 拡張子別にファイルをグループ化する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 ファイル名拡張子に基づいて、<xref:System.IO.FileInfo> オブジェクトのグループを返す方法を示します。  
  
 [方法: 一連のフォルダーの合計バイト数を問い合わせる (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 指定したディレクトリ ツリー内のすべてのファイルの合計バイト数を返す方法を示します。  
  
 [方法: 2 つのフォルダーの内容を比較する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)  
 指定した 2 つのフォルダーに存在するファイルをすべて返す方法と、一方のフォルダーにのみ存在し、もう一方には存在しないファイルをすべて返す方法を示します。  
  
 [方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 ディレクトリ ツリーで、最もサイズの大きいファイルまたは最もサイズの小さいファイル、あるいは指定した数のファイルを返す方法を示します。  
  
 [方法: ディレクトリ ツリーで重複するファイルを問い合わせる (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 指定したディレクトリ ツリーの複数の場所に出現するすべてのファイル名をグループ化する方法を示します。 また、カスタム比較演算子に基づいて、より複雑な比較を実行する方法も示します。  
  
 [方法: フォルダー内のファイルの内容を照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 ツリー内のフォルダーを反復処理し、各ファイルを開き、ファイルの内容を照会する方法を示します。  
  
## <a name="comments"></a>コメント  
 ファイル システムの内容を正確に表し、例外を適切に処理するデータ ソースを作成する手順は複雑になります。 ここに示す例では、指定したルート フォルダーおよびすべてのサブフォルダーの下にある、すべてのファイルを表す <xref:System.IO.FileInfo> オブジェクトのスナップショット コレクションを作成します。 各 <xref:System.IO.FileInfo> の実際の状態は、クエリの実行の開始時点から終了時点までの間に変化する可能性があります。 たとえば、データ ソースとして使用する <xref:System.IO.FileInfo> オブジェクトの一覧を作成したとします。 クエリで `Length` プロパティにアクセスしようとすると、<xref:System.IO.FileInfo> オブジェクトがファイル システムにアクセスして `Length` の値を更新しようとします。 ファイルがもう存在しない場合は、ファイル システムを直接照会していなくても、クエリから <xref:System.IO.FileNotFoundException> が返されます。 ここで示すクエリの中には、状況により、このような特定の例外を処理する個別のメソッドを使用しているものがあります。 別の方法として、<xref:System.IO.FileSystemWatcher> を使用して、データ ソースを動的に更新して常に最新の状態に保つこともできます。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
