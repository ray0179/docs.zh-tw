---
title: "規則運算式活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 規則運算式活動
這個範例示範如何建立可公開 <xref:System.Text.RegularExpressions> 命名空間規則運算式功能的一組活動。這些自訂活動可在工作流程應用程式中使用。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]規則運算式，請參閱 [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) 命名空間。  
  
 下表詳述這個範例中的自訂活動。  
  
|活動|說明|  
|--------|--------|  
|IsMatch|指定規則運算式是否找到輸入字串的符合項目。|  
|Matches|在輸入字串中搜尋規則運算式的所有符合項目，並傳回所有符合項目。|  
|Replace|在指定的輸入字串中，以指定的取代字串來取代符合規則運算式的字串。|  
  
## IsMatch  
 如果 `Input` 字串屬性找到 `Pattern` 屬性中所指定規則運算式的符合項目，`IsMatch` 自訂動作會傳回 `true`。此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法。  
  
 下表描述 `IsMatch` 自訂活動的屬性和傳回值。  
  
|屬性或傳回值|說明|  
|------------|--------|  
|Pattern \(必要\)|用來搜尋的規則運算式。|  
|Input \(必要\)|要搜尋的輸入字串。|  
|RegexOptions|[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) 列舉值的位元 OR 組合。|  
|傳回值|如果輸入找到所提供模式的符合項目，則為 `true`，否則為 `false`。|  
  
 下列程式碼範例示範如何使用 `IsMatch` 自訂活動。  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
  
```  
  
## Matches  
 `Matches` 自訂活動會在輸入字串中搜尋規則運算式的所有符合項目，並傳回所有符合項目。此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 方法。  
  
 下表描述 `IsMatch` 自訂活動的屬性和傳回值。  
  
|屬性或傳回值|說明|  
|------------|--------|  
|Pattern \(必要\)|用來搜尋的規則運算式。|  
|Input \(必要\)|要搜尋的輸入字串。|  
|RegexOptions|[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) 列舉值的位元 OR 組合。|  
|傳回值|<xref:System.Text.RegularExpressions.MatchCollection>，其中包含所有符合項目的集合。|  
  
 下列程式碼範例示範如何使用 `Matches` 自訂活動。  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
  
```  
  
## Replace  
 `Replace` 自訂活動會搜尋輸入字串，並以字串取代符合指定之規則運算式的所有字串。此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法。  
  
 下表描述 `Replace` 自訂活動的屬性和傳回值。  
  
|屬性或傳回值|說明|  
|------------|--------|  
|Pattern \(必要\)|用來搜尋的規則運算式。|  
|Input \(必要\)|要搜尋的輸入字串。|  
|Replacement|取代字串。<br /><br /> 如果指定 `Replacement`，則會忽略 `MatchEvaluator` 屬性。必須設定 `Replacement` 或 `MatchEvaluator` 其中一個屬性。|  
|MatchEvaluator|檢查每個符合項目並傳回原始符合字串或取代字串的自訂方法。<br /><br /> 如果指定 `Replacement`，則會忽略 `MatchEvaluator` 屬性。必須設定 `Replacement` 或 `MatchEvaluator` 其中一個屬性。|  
|RegexOptions|[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) 列舉值的位元 OR 組合。|  
|傳回值|<xref:System.Text.RegularExpressions.MatchCollection>，其中包含所有符合項目的集合。|  
  
 下列程式碼範例示範如何使用 `Replace` 自訂活動。  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
  
```  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 RegexActivities.sln 方案檔。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按下 CTRL\+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`  
  
## 請參閱