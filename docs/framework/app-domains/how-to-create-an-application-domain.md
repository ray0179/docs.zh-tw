---
title: "如何：建立應用程式定義域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 39d8db32f82827e76d9517d387e2fc001fc209aa
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：建立應用程式定義域
Common Language Runtime 主應用程式會在需要時自動建立應用程式定義域。  然而，您可以建立自己的應用程式定義域，並將它們載入那些您要自行管理的組件。  您也可以建立應用程式定義域並從該應用程式定義域中執行程式碼。  
  
 您可以使用 <xref:System.AppDomain?displayProperty=fullName> 類別中 **CreateDomain** 方法的其中一個多載，以建立新的應用程式定義域。  您可以提供應用程式定義域名稱，並可依該名稱進行參考。  
  
 下列範例建立新的應用程式定義域、將之命名為 `MyDomain`，然後將主應用程式定義域名稱和新建立的子應用程式定義域列印至主控台 \(Console\)。  
  
## 範例  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)

