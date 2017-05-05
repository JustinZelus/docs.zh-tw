---
title: "風險降低：TLS 通訊協定 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1474aeb0e1be38018f9d27c49e8711800ecb9f01
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-tls-protocols"></a>風險降低：TLS 通訊協定
從 .NET Framework 4.6 開始，<xref:System.Net.ServicePointManager?displayProperty=fullName> 和 <xref:System.Net.Security.SslStream?displayProperty=fullName> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。 不支援 SSL3.0 通訊協定與 RC4 編碼器。  
  
## <a name="impact"></a>影響  
 這項變更會影響：  
  
-   使用 SSL 與 HTTPS 伺服器或使用下列任一類型之通訊端伺服器通訊的任何應用程式：<xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient> 和 <xref:System.Net.Security.SslStream>。  
  
-   無法升級到支援 Tls1.0、Tls1.1 或 Tls 1.2 的任何伺服器端應用程式。  
  
## <a name="mitigation"></a>緩和  
 建議的風險降低措施是將伺服器端應用程式升級至 Tls1.0、Tls1.1 或 Tls 1.2。 如果這並不可行，或是用戶端應用程式已中斷，則可使用 <xref:System.AppContext> 類別搭配下列兩種方式之一以選擇退出這項功能：  
  
-   以程式設計方式，利用如下所示的程式碼片段：  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     因為 <xref:System.Net.ServicePointManager> 物件只能初始化一次，因此應用程式必須優先定義這些相容性設定。  
  
-   將下列程式行加入至 app.config 檔案的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 區段：  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 但是請注意，我們並不建議您停用這項預設行為，因為這樣會讓應用程式較不安全。  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)