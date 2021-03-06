---
title: "&lt;serviceActivations&gt; 的 &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;serviceActivations&gt; 的 &lt;add&gt;
組態項目，這個項目可讓您定義虛擬服務啟動設定，這些設定會對應至您的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務型別。  如此一來，不需 .svc 檔案也能啟動裝載於 WAS\/IIS 中的服務。  
  
## 語法  
  
```  
  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|factory|字串，指定產生服務啟動項目之處理站的 CLR 型別名稱。|  
|服務|實作服務的 ServiceType 可以是完整 Typename 或簡短 Typename \(置於 App\_Code 資料夾時\)。|  
|relativeAddress|在目前 IIS 應用程式中的相對位址，例如 "Service.svc"。  在 WCF 4.0 中，此相對位址必須包含其中一個已知的副檔名 \(.svc、.xamlx...\)。  relativeUrl 不一定要有實體檔案存在|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|描述啟動設定的組態區段。|  
  
## 備註  
 下列範例示範如何在您的 web.config 檔案中設定啟動設定。  
  
```  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。  
  
 請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。  您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。  此外，`serviceHostingEnvironment` 是 machinetoApplication 可繼承的區段。  如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。  
  
 以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。  relatativeAddress 必須有副檔名，亦即  .svc、.xoml 或 .xamlx。  您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。  發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>