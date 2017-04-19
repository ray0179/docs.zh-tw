---
title: "WS-AtomicTransaction 組態 MMC 嵌入式管理單元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# WS-AtomicTransaction 組態 MMC 嵌入式管理單元
WS\-AtomicTransaction 組態 MMC 嵌入式管理單元用於設定本機電腦和遠端電腦上的部分 WS\-AtomicTransaction 設定。  
  
## 備註  
 如果您執行的是 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 或 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]，請依序巡覽至 \[**控制台\/系統管理工具\/元件服務\/**\]，以滑鼠右鍵按一下 \[**我的電腦**\]，然後選取 \[**內容**\]，即可找到 MMC 嵌入式管理單元。這個位置與您設定 MSDTC 的位置相同。組態的可用選項會分組在 \[**WS\-AT**\] 索引標籤之下。  
  
 如果您執行的是 Windows Vista 或 [!INCLUDE[lserver](../../../includes/lserver-md.md)]，可以按一下 \[**開始**\] 按鈕，然後在 \[**搜尋**\] 方塊中輸入 `dcomcnfg.exe`，即可找到 MMC 嵌入式管理單元。當 MMC 開啟時，巡覽至 \[**我的電腦\\分散式交易協調器\\本機 DTC**\] 節點，以滑鼠右鍵按一下之後，選取 \[**內容**\]。組態的可用選項會分組在 \[**WS\-AT**\] 索引標籤之下。  
  
 上述的步驟用於啟動設定本機電腦的嵌入式管理單元。如果您要設定遠端電腦，請依序巡覽至 \[**控制台\/系統管理工具\/元件服務\/**\]，即可在其中找到遠端電腦的名稱，然後執行類似於 [!INCLUDE[wxp](../../../includes/wxp-md.md)] 或 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] 中所執行的步驟。如果您執行的是 Windows Vista 或 [!INCLUDE[lserver](../../../includes/lserver-md.md)]，請執行上述針對 Vista 或 [!INCLUDE[lserver](../../../includes/lserver-md.md)] 的步驟，但改為使用遠端電腦節點下的 \[**分散式交易協調器\\本機 DTC**\] 節點。  
  
 若要使用此工具提供的使用者介面，您必須註冊 WsatUI.dll 檔，此檔位於以下路徑，  
  
 **%PROGRAMFILES%\\Microsoft SDKs\\Windows\\v6.0\\Bin\\WsatUI.dll**  
  
 下列命令可完成註冊。  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 您可以使用這個工具修改基本 WS\-AtomicTransaction 設定。例如，您可以啟用或停用 WS\-AtomicTransaction 通訊協定支援、設定 WS\-AT 的 HTTP 連接埠、將 SSL 憑證繫結至 HTTP 連接埠、透過指定憑證主體名稱來設定憑證、選取追蹤模式，以及設定預設逾時與最大逾時。  
  
 如果您必須在本機電腦上設定 WS\-AtomicTransaction 支援，可使用這個工具的命令列版本。[!INCLUDE[crabout](../../../includes/crabout-md.md)]命令列工具的詳細資訊，請參閱 [WS\-AtomicTransaction 組態公用程式 \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) 主題。  
  
 請注意，MMC 嵌入式管理單元和命令列工具都不支援設定所有 WS\-AT 設定。這些設定只能透過直接修改登錄來編輯。[!INCLUDE[crabout](../../../includes/crabout-md.md)]這些登錄的詳細資訊，請參閱[設定 WS\-Atomic 交易支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)。  
  
### 使用者介面說明  
 **啟用 WS\-Atomic 交易網路支援**：  
  
 切換這個核取方塊可啟用或停用此嵌入式管理單元的所有 GUI 元件。  
  
 在核取此方塊前，您應該先確認已啟用網路 DTC 存取和傳入或傳出通訊 \(或兩者\)。在 MSDTC 嵌入式管理單元的 \[**安全性**\] 索引標籤中可驗證這個值。  
  
#### 網路群組方塊  
 您可以在 \[網路\] 群組中指定 HTTPS 連接埠和其他安全性設定，如 SSL 加密。如果 \[DTC 網路交易\] 未啟用，則這個群組為停用 \(呈現淡灰色\)。  
  
 **HTTPS 連接埠**  
  
 這是用於 WS\-AT 之 HTTPS 連接埠的值。這個值必須在 1\-65535 的範圍內 \(用於表示有效連接埠\)。變更 HTTP 連接埠會修改 HTTP 服務組態，意指先前使用的 WS\-AT Service Address 已釋放，並根據新的連接埠註冊新的 WS\-AT Service Address。此外，新選取的連接埠會使用目前選取的 SSL 加密憑證進行加密。  
  
> [!NOTE]
>  如果在執行此工具之前，您已啟用防火牆，則會自動在例外狀況清單中註冊該連接埠。如果在執行此工具之前，您已停用防火牆，則不必為該防火牆進行任何額外的設定。  
  
 如果您在設定 WS\-AT 後啟用了防火牆，您必須再次執行這個工具，並使用這個參數提供連接埠號碼。如果您在設定後停用防火牆，WS\-AT 會繼續運作，而不必進行額外的輸入。  
  
 **端點憑證**  
  
 按一下 \[**選取**\] 按鈕顯示 \[本機電腦\] 上目前可用憑證的清單，讓使用者可選取用於 SSL 加密的憑證。憑證必須包含私密金鑰。否則，您會收到錯誤訊息。  
  
> [!NOTE]
>  為選取的連接埠設定 SSL 憑證時，如果與該連接埠關聯的原始 SSL 憑證存在的話，將會覆寫該憑證。  
  
 **授權的帳戶**  
  
 按一下 \[**選取**\] 按鈕可叫用 \[Windows 存取控制清單\] 編輯器，您可以在其中核取 \[**加入**\] 權限群組的 \[**允許**\] 或 \[**拒絕**\] 方塊，來指定參與 WS\-Atomic 交易的使用者或群組。  
  
 **授權的憑證**  
  
 按一下 \[**選取**\] 按鈕顯示 \[本機電腦\] 上目前可用憑證的清單。您可以選取允許哪些憑證識別參與 WS\-Atomic 交易。  
  
#### 逾時群組方塊  
 \[**逾時**\] 群組方塊可讓您為 WS\-Atomic 交易指定預設逾時和最大逾時。傳出逾時的有效值介於 1 和 3600。傳入逾時的有效值介於 0 和 3600。  
  
#### 追蹤和記錄群組方塊  
 \[**追蹤和記錄**\] 群組方塊可讓您設定所需的追蹤和記錄層級。  
  
 按一下 \[**選項**\] 按鈕會開啟一個頁面，您可以在其中指定其他設定。  
  
 \[**追蹤層級**\] 組合方塊可讓您選取 <xref:System.Diagnostics.TraceLevel> 列舉的任何有效值。您也可以使用核取方塊來指定您是否要執行活動追蹤、活動傳播，或收集個人可識別資訊。  
  
 您也可以使用 \[**記錄工作階段**\] 群組方塊來指定記錄工作階段。  
  
> [!NOTE]
>  當有其他追蹤消費者正在使用 WS\-AT 追蹤提供者時，您無法為追蹤事件建立新的記錄工作階段。在此時任何設定記錄的嘗試，都會導致產生「無法啟用提供者。錯誤碼：1"。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]追蹤和記錄的詳細資訊，請參閱[管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)。  
  
## 請參閱  
 [設定 WS\-Atomic 交易支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)   
 [WS\-AtomicTransaction 組態公用程式 \(wsatConfig.exe\)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)   
 [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)