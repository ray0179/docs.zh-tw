---
title: "&lt;AttributeImplies&gt; 項目 (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fcb3f476a00f00e00eeea90db75699c2c4cdf76
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="ltattributeimpliesgt-element-net-native"></a>&lt;AttributeImplies&gt; 項目 (.NET Native)
定義套用包含屬性之程式碼元素的原則。  
  
## <a name="syntax"></a>語法  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|屬性類型|說明|  
|---------------|--------------------|-----------------|  
|`Activate`|反射|選擇性屬性。 控制建構函式的執行階段存取，以便啟動執行個體。|  
|`Browse`|反射|選擇性屬性。 控制程式項目相關資訊的查詢，但不會啟用任何執行階段存取。|  
|`Dynamic`|反射|選擇性屬性。 控制對所有類型成員 (包括建構函式、方法、欄位、屬性和事件) 的執行階段存取，以啟用動態程式設計。|  
|`Serialize`|序列化|選擇性屬性。 控制建構函式、欄位和屬性的執行階段存取，以便 Newtonsoft JSON 序列化程式等程式庫可對類型執行個體進行序列化和還原序列化。|  
|`DataContractSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> 類別的序列化原則。|  
|`DataContractJsonSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> 類別的 JSON 序列化原則。|  
|`XmlSerializer`|序列化|選擇性屬性。 控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 類別的 XML 序列化原則。|  
|`MarshalObject`|Interop|選擇性屬性。 控制 Windows 執行階段和 COM 之參考類型的封送處理原則。|  
|`MarshalDelegate`|Interop|選擇性屬性。 控制將委派類型當作函式指標封送處理至機器碼的原則。|  
|`MarshalStructure`|Interop|選擇性屬性。 控制將值類型封送處理為原生程式碼的原則。|  
  
## <a name="all-attributes"></a>所有屬性  
  
|值|說明|  
|-----------|-----------------|  
|*policy_setting*|要套用到此原則類型的設定。 可能的值為 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 和 `Required All`。 如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|將反映原則套用至類型及其所有成員。|  
  
## <a name="remarks"></a>備註  
 如果 `<AttributeImplies>` 元素的包含類型是屬性 (也就是衍生自 <xref:System.Attribute?displayProperty=fullName> 的類別)，就會使用此元素。 如果屬性套用至特定的程式元素，則 `<AttributeImplies>` 元素所定義的原則會套用至該程式元素。  
  
 反映、序列化和 interop 屬性都是選用性，但至少要有一個屬性存在。  
  
## <a name="see-also"></a>另請參閱  
 [\<Type> 元素](../../../docs/framework/net-native/type-element-net-native.md)   
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [執行階段指示詞元素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)

