---
title: "無法取得記錄檔的資料流 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 無法取得記錄檔的資料流
無法取得記錄檔的資料流。 以 \<名稱\> 為主的檔名已經在使用中。  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別無法建立新的記錄檔，因為所有以 \<名稱\> 為主的記錄檔名稱已經在使用中。  
  
 記錄檔太多可能表示應用程式發生架構問題。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別的文件。  
  
### 更正這個錯誤  
  
1.  請將 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 屬性設定為 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption>，以在記錄檔名稱中包括日期戳記。  
  
2.  封存現有的記錄檔並將其從電腦中移除，讓 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 物件可以建立新的記錄檔。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [My.Application.Log 物件](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [My.Log Object](../../visual-basic/language-reference/objects/my-log-object.md)