---
title: "中間結果の具体化 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 46d347921e24bc5504c69534d7b5c087818a6c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="intermediate-materialization-c"></a>中間結果の具体化 (C#)
不注意なユーザーは、クエリ内でコレクションを早期に具体化して、アプリケーションのメモリおよびパフォーマンスのプロファイルを大幅に変更してしまうことがあります。 一部の標準クエリ演算子では、単一の要素を生成する前に、ソース コレクションを具体化する場合があります。 たとえば、<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> は最初にソース コレクション全体を反復処理し、次にすべての項目を並べ替えて、最後に最初の項目を生成します。 これは、順序付けられたコレクションの最初の項目の取得が高コストであることを意味しています。これ以降の各項目の取得は高コストではありません。 このクエリ演算子は他の方法では処理を実行できないため、これは処理方法として適切なものです。  
  
## <a name="example"></a>例  
 この例では、前の例を変更します。 `AppendString` メソッドは、ソースを反復処理する前に、<xref:System.Linq.Enumerable.ToList%2A> ‚ðŒÄ‚Ño‚µ‚Ü‚·B これにより、具体化が行われます。  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 この例では、<xref:System.Linq.Enumerable.ToList%2A> の呼び出しにより、`AppendString` が、最初の項目を生成する前にソース全体を列挙することがわかります。 ソースが大きな配列である場合は、これによってアプリケーションのメモリ プロファイルが大幅に変更されます。  
  
 標準クエリ演算子も連結することができます。 これについては、このチュートリアルの最後のトピックで説明します。  
  
-   [標準クエリ演算子の連結 (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
