---
title: "使用 FlowChart 及 Pick 組合的 StateMachine 案例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 使用 FlowChart 及 Pick 組合的 StateMachine 案例
這個範例示範如何實作一個使用 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Pick> 活動組合的簡單馬錶案例。在 Pick 活動中使用 Receive 和 Send 以接聽馬錶事件。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 \(下載頁面\) 以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## 範例詳細資料  
 下表列出這個範例中的專案。  
  
|||  
|-|-|  
|專案名稱|說明|  
|StopWatchService|這個專案包含一個使用 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Pick> 活動組合之馬錶範例的狀態機器實作。<br /><br /> <xref:System.Activities.Statements.Pick> 活動的 <xref:System.Activities.Statements.Pick.Branches%2A> 屬性中有 3 個 <xref:System.Activities.Statements.PickBranch> 陳述式，會接聽 `GetStart`、`GetStop` 和 `GetOff` 事件。根據傳入事件，每個分支的觸發程式會啟動，而且對應的 <xref:System.Activities.Statements.PickBranch.Action%2A> 會觸發。在 <xref:System.Activities.Statements.PickBranch.Action%2A> 屬性中，<xref:System.Activities.Statements.Switch%601> 陳述式會評估狀態轉換是否為合法轉換，如果是的話，`currentState` 屬性會更新為轉換中狀態並傳送至用戶端。<br /><br /> 在 <xref:System.Activities.Statements.Flowchart> 結束時 <xref:System.Activities.Statements.FlowDecision> 活動會評估 `currentState` 屬性，以判斷狀態是否為末期。如果是的話，工作流程會結束，否則控制權會循環回到 <xref:System.Activities.Statements.Pick> 活動的開頭，工作流程在此等候其他馬錶事件。|  
|StopWatchClient|這是簡單循序工作流程主控台應用程式，會傳送具有簡單 Send 或 Receive 活動組合的各種馬錶事件。|  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 StateMachineWithPick.sln 方案檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  以滑鼠右鍵按一下 StopWatchService.exe 檔案，並選取 \[**以系統管理員身分執行**\]，從 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 以系統管理員的身分啟動此 .exe 檔案。  
  
    1.  巡覽至 StateMachineWithPick\\CS\\StopWatchService\\bin\\Debug 資料夾。  
  
    2.  以滑鼠右鍵按一下 StopWatchService.exe 檔案，然後選取 \[**以系統管理員身分執行**\]。  
  
4.  從 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中啟動 StopWatchClient 用戶端應用程式。  
  
    1.  在 \[**方案總管**\] 中，選取 **StopWatchClient** 專案，以滑鼠右鍵按一下 \[**設定為啟始專案**\]。  
  
    2.  若要執行方案，請按 CTRL\+F5。  
  
5.  切換回 StopWatchService.exe 的主控台視窗，以檢視狀態轉換。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## 請參閱