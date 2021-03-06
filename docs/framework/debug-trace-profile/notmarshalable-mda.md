---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1dcce60b18169e1ca7c87440cec7e36e08634461
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
在跨內容封送處理介面時，當 Common Language Runtime (CLR) 遇到 COM 介面指標，卻無有效已登錄的 Proxy/Stub 或 `IMarshal` 界面實作不正確，則會啟動 `notMarshalable` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆   
 未服務呼叫，或呼叫在錯誤的 COM 介面指標的內容中發生。  
  
## <a name="cause"></a>原因  
 嘗試跨內容封送處理介面時，沒有有效的已登錄 Proxy/Stub 或 `IMarshal` 不正確。  
  
## <a name="resolution"></a>解決方式  
 請確定您已註冊 Proxy 虛設常式，並確定 `IMarshal` 實作是否有效。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對執行階段沒有影響。  
  
## <a name="output"></a>輸出  
 描述問題的訊息。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [使用 Managed 偵錯助理診斷錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)

