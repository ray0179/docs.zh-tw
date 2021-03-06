---
title: "聯結作業 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: df2f88f2988a4c91730bcfc4e39f10e3471e4ddf
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="join-operations-c"></a>聯結作業 (C#)
兩個資料來源的「聯結」，就是某個資料來源中的物件，和另一個資料來源中共用通用屬性的物件的關聯。  
  
 對於不能直接追蹤目標資料來源彼此之間的關聯性的查詢而言，聯結是很重要的作業。 在物件導向的程式設計中，這可能表示物件之間的相互關聯沒有模組化，例如單向關聯性的返回方向。 一個單向關聯性的範例是「客戶」類別，其具有類型「城市」的屬性，但「城市」類別沒有「客戶」物件集合的屬性。 若您有「城市」物件清單，且您想要尋找每個城市中的所有客戶，您就可以使用聯結作業來尋找客戶。  
  
 LINQ 架構中所提供的 join 方法是 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。 這些方法會執行等聯結，或是執行根據其索引鍵相等與否配對兩個資料來源的聯結。 (相較下，Transact-SQL 支援「等於」運算子以外的聯結運算子，例如「小於」運算字)。在關聯式資料庫規定中，<xref:System.Linq.Enumerable.Join%2A> 會實作內部聯結，在這種聯結中，只會傳回在其他資料集中有相符項目的物件。 <xref:System.Linq.Enumerable.GroupJoin%2A> 方法從關聯式資料庫觀點來看沒有直接的對應項目，但它會實作內部聯結和左方外部聯結的超集。 左方外部聯結是傳回第一個 (左) 資料來源中每個項目的聯結，即使它在其他資料來源中沒有相互關聯的項目也一樣。  
  
 以下概念圖示範兩個集合，以及兩個集合中包含在內部聯結或左外部聯結中的項目。  
  
 ![顯示內部&#47;外部的兩個重疊圓形。](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|根據索引鍵選取器函式聯結兩個序列並擷取值組。|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|根據索引鍵選取器函式聯結兩個序列，並為每個項目的相符結果進行分組。|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [制定聯結和交叉乘積查詢](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)   
 [join 子句](../../../../csharp/language-reference/keywords/join-clause.md)   
 [如何：使用複合索引鍵執行聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [如何：從不同的檔案聯結內容 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)   
 [如何：排序 Join 子句的結果](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [如何：執行自訂聯結作業](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)   
 [如何：執行群組聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [如何：執行內部聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [如何：執行左方外部聯結](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [如何：從多個來源填入物件集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)

