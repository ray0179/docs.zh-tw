---
title: "選取認證類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# 選取認證類型
「*認證*」\(Credential\) 是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用於建立宣告的身分識別或功能的資料。  例如，護照是政府發給的認證，以證明一個國家或地區的公民身分。  在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，認證可以有許多形式，例如使用者名稱權杖和 X.509 憑證。  本主題將說明認證、如何在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中使用，以及如何為應用程式選擇正確的認證。  
  
 在許多國家和地區，駕駛執照是認證的一個例子。  執照包含了代表一個人身分識別和能力的資料。  其中包含以持有人的照片做為所有權的證明。  執照是由受信任的授權單位發出，通常是政府的發照部門。  執照會經過密封，而且可能內含雷射防偽，表示沒有遭到竄改或偽造。  
  
 出示認證包括出示資料以及資料的所有權證明。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援傳輸和訊息安全層級的各種認證類型。  例如，請試想 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中支援的兩種認證類型：使用者名稱和 \(X.509\) 憑證認證。  
  
 對於使用者名稱認證，使用者名稱代表宣告的身分識別，而密碼提供所有權的證明。  在此案例中，受信任的授權單位是驗證使用者名稱和密碼的系統。  
  
 使用 X.509 憑證認證，憑證內的主體名稱、主體別名或特定欄位都可以用來做為身分識別的宣告，而其他欄位 \(例如 `Valid From` 和 `Valid To` 欄位\) 則指定憑證的有效性。  
  
## 傳輸認證類型  
 下表顯示在傳輸安全性模式中，可以由繫結使用之用戶端認證的可能類型。  當建立服務時，請將 `ClientCredentialType` 屬性設定為這些值的其中之一，以指定用戶端必須提供才能與您服務通訊之認證的類型。  您可以使用程式碼或組態檔來設定類型。  
  
|設定|描述|  
|--------|--------|  
|無|指定用戶端不需要提出任何認證。  這會轉譯成匿名用戶端。|  
|基本|為用戶端指定基本驗證。  如需其他資訊，請參閱 RFC2617—[HTTP 驗證：基本與摘要式驗證](http://go.microsoft.com/fwlink/?LinkID=88313)。|  
|摘要|為用戶端指定摘要式驗證。  如需其他資訊，請參閱 RFC2617—[HTTP 驗證：基本與摘要式驗證](http://go.microsoft.com/fwlink/?LinkID=88313)。|  
|Ntlm|指定 NT LAN 管理員 \(NTLM\) 驗證。  這是用於當您因故無法使用 Kerberos 驗證時。  您也可以將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> 屬性設為 `false`，以停用它做為後援的用途，讓 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在使用 NTLM 時能夠盡力擲回例外狀況。  請注意，將此屬性設為 `false`，不一定能夠禁止 NTLM 認證透過網路傳送。|  
|Windows|指定 Windows 驗證。  如果在 Windows 網域上只要指定 Kerberos 通訊協定，請將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> 屬性設定為 `false` \(預設為 `true`\)。|  
|憑證|使用 X.509 憑證執行用戶端驗證。|  
|密碼|使用者必須提供使用者名稱和密碼。  請使用 Windows 驗證或其他自訂方案來驗證使用者名稱\/密碼組。|  
  
### 訊息用戶端認證類型  
 下表顯示在建立使用訊息安全性的應用程式時，您可以使用的可能認證類型。  您可以在程式碼或組態檔中使用這些值。  
  
|設定|描述|  
|--------|--------|  
|無|指定用戶端不需要出示認證。  這會轉譯成匿名用戶端。|  
|Windows|允許在使用 Windows 認證建立的安全性內容下發生 SOAP 訊息交換。|  
|使用者名稱|允許服務要求用戶端必須使用使用者名稱認證進行驗證。  請注意，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不允許任何利用使用者名稱的密碼編譯作業，例如產生簽章或加密資料。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在利用使用者名稱認證時，確保傳輸安全受到保護。|  
|憑證|允許服務要求用戶端使用 X.509 憑證進行驗證。|  
|發行的權杖|根據安全性原則設定的自訂權杖類型。  預設的權杖類型為 Security Assertions Markup Language \(SAML\)。  權杖是由安全的權杖服務所發行。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [聯合與發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### 服務認證的交涉模型  
 「*交涉*」\(Negotiation\) 是藉由交換認證，在用戶端和服務之間建立信任的處理程序。  此處理程序會在用戶端和服務之間反覆執行，以便只透露交涉處理程序中下一個步驟所需要的資訊。  實際上，最終結果是將服務的認證傳遞至要用於後續作業中的用戶端。  
  
 除了一個例外狀況以外，根據預設，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中由系統提供的繫結會在使用訊息層級安全性時自動交涉服務認證。  \(例外狀況為 <xref:System.ServiceModel.BasicHttpBinding>，根據預設不會啟用安全性\)。如果要停用這個行為，請參閱 <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> 和 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> 屬性。  
  
> [!NOTE]
>  SSL 安全性與 .NET Framework 3.5 \(含\) 以後版本搭配使用時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端會使用其憑證存放區中的中繼憑證以及在 SSL 交涉期間收到的中繼憑證，在服務的憑證上執行憑證鏈結驗證。  .NET Framework 3.0 只會使用安裝在本機憑證存放區中的中繼憑證。  
  
#### 超出範圍交涉  
 如果停用自動交涉，在傳送任何訊息給服務之前，必須在用戶端提供服務認證。  這也稱為「*超出範圍*」\(Out\-of\-Band\) 提供。  例如，如果指定的認證類型是憑證，且停用自動交涉，用戶端就必須連絡服務擁有者，以在執行用戶端應用程式的電腦上接收並安裝憑證。  例如，在商業案例中，當您希望嚴格控制哪些用戶端可以存取服務時，可能會完成這項操作。  這個超出範圍交涉可能會以電子郵件進行，且 X.509 憑證會透過如 Microsoft Management Console \(MMC\) 憑證嵌入式管理單元的工具儲存在 Windows 憑證存放區中。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性是用於為服務提供透過超出範圍交涉所取得的憑證。  這在使用 <xref:System.ServiceModel.BasicHttpBinding> 類別時是必要的，因為繫結不允許自動化交涉。  此屬性也用於沒有關聯的雙工案例中。  在這個案例中，用戶端不需要先將要求傳送至伺服器，伺服器就可以將訊息傳送到用戶端。  由於伺服器沒有來自用戶端的要求，因此必須使用用戶端的憑證來對用戶端加密訊息。  
  
## 設定認證值  
 在選擇安全性模式之後，您必須指定實際的認證。  例如，如果認證類型設定為「憑證」，則您必須建立特定認證 \(例如特定的 X.509 憑證\) 與服務或用戶端的關聯。  
  
 根據您是對服務或用戶端進行程式設計，設定認證值的方法會有些許不同。  
  
### 設定服務認證  
 如果您是使用傳輸模式，並使用 HTTP 做為傳輸，您必須使用網際網路資訊服務 \(IIS\) 或使用憑證設定連接埠。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)和[HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。  
  
 如果要在程式碼中提供含有認證的服務，請建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體，並使用 <xref:System.ServiceModel.Description.ServiceCredentials> 類別指定適當的認證 \(透過 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 屬性存取\)。  
  
#### 設定憑證  
 如果要提供含有用於對用戶端驗證服務之 X.509 憑證的服務，請使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> 方法。  
  
 如果要提供含有用戶端憑證的服務，請使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法。  
  
#### 設定 Windows 認證  
 如果用戶端指定有效的使用者名稱和密碼，會使用該認證來驗證用戶端。  否則便會使用目前登入之使用者的認證。  
  
### 設定用戶端認證  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，用戶端應用程式會使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端來連接服務。  每個用戶端都是衍生自 <xref:System.ServiceModel.ClientBase%601> 類別，而用戶端上的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性允許用戶端認證之各種不同值的規格。  
  
#### 設定憑證  
 如果要提供含有用於對服務驗證用戶端之 X.509 憑證的服務，請使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法。  
  
## 如何使用用戶端認證對服務驗證用戶端  
 與服務通訊所需要的用戶端認證資訊是使用 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 屬性或 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 屬性來提供的。  安全性通道會使用此資訊對服務驗證用戶端。  驗證是透過兩種模式的其中之一完成的：  
  
-   在傳送第一個訊息之前，會使用一次用戶端認證，使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端執行個體來建立安全性內容。  然後所有的應用程式訊息都會透過安全性內容來保護其安全。  
  
-   用戶端認證是用於驗證傳送到服務的每個應用程式訊息。  在這種情況中，不會在用戶端和服務之間建立內容。  
  
### 無法變更已建立的身分識別  
 當使用第一個方法時，已建立的內容會與用戶端身分識別建立永久性的關聯。  也就是說，在建立安全性內容之後，就無法變更與用戶端有關聯的身分識別。  
  
> [!IMPORTANT]
>  當無法切換身分識別時 \(也就是，當開啟已建立之安全性內容時的預設行為\)，有一種情況要注意。  如果您建立與第二個服務通訊的服務，就無法變更用於對第二個服務開啟 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的身分識別。  如果允許多個用戶端使用第一個服務，且該服務在存取第二個服務時模擬用戶端，這就會變成問題。  如果服務對所有的呼叫者重複使用相同的用戶端，第二個服務的所有呼叫都會在用於對第二個服務開啟用戶端之第一個呼叫者的身分識別下完成。  換言之，服務會對所有用戶端使用第一個用戶端的身分識別來與第二個服務通訊。  這會造成權限的升級。  如果這不是您的服務所需要的行為，您必須追蹤每個呼叫者，並為每個不同的呼叫者建立第二個服務的新用戶端，然後確保服務只對正確的呼叫者使用正確的用戶端，以與第二個服務通訊。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]認證及安全工作階段的詳細資訊，請參閱[安全工作階段的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>   
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=fullName>   
 [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)   
 [確保服務與用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [WCF 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)   
 [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)