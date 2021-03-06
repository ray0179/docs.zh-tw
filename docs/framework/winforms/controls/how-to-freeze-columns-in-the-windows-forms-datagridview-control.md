---
title: "如何：凍結 Windows Form DataGridView 控制項中的資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料行 [Windows Form], 凍結"
  - "DataGridView 控制項 [Windows Form], 一直在檢視中的資料行"
  - "DataGridView 控制項 [Windows Form], 凍結資料行"
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：凍結 Windows Form DataGridView 控制項中的資料行
當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。  例如，在顯示包含許多資料行的客戶資訊資料表時，如果其他資料行可在可見區域外捲動時，仍一直顯示客戶的名稱，將會非常有用。  
  
 若要達到這種行為，您可以凍結控制項中的資料行。  當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 \(如果是從右至左的字集，則會凍結右邊的所有資料行\)。  凍結的資料行會留在原處，而其他所有資料行則可以捲動。  
  
> [!NOTE]
>  如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。  使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。  
  
 資料行的 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> 屬性會決定資料行在格線內是否一律顯示。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\))。  
  
### 以程式設計方式凍結資料行  
  
-   將 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName> 屬性設定為 `true`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的控制項 <xref:System.Windows.Forms.DataGridView>，包含名為 `AddToCartButton` 的資料行。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 [Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [如何：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)