---
title: 雙工服務
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: da92b8f2d1223f582677a93a8ff6fd697512d297
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="duplex-services"></a>雙工服務
雙工服務合約為訊息交換模式，其中的兩個端點可以彼此獨立地傳送訊息。 因此，雙工服務可以將訊息傳送回用戶端端點，以提供類似事件的行為。 用戶端建立與服務的連線，並提供服務所需的通道以供服務將訊息傳回用戶端，這個程序即是所謂的雙工通訊。 請注意，雙工服務的類似事件行為只會在工作階段內運作。  
  
 若要建立雙工合約，您可建立一組介面。 第一個是服務合約介面，說明用戶端可叫用的作業。 該服務合約必須指定*回呼合約*中<xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>屬性。 回呼合約是一個介面，會定義服務可在用戶端端點上呼叫的作業。 雙工合約不需要工作階段，不過系統提供的雙工繫結會利用工作階段。  
  
 以下為雙工合約的範例。  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` 類別會實作主要的 `ICalculatorDuplex` 介面。 服務會使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體模式維持各工作階段的結果。 而名為 `Callback` 的私用屬性會存取用戶端的回呼通道。 服務會使用回呼，以透過回呼介面將訊息傳回用戶端，如以下範例程式碼所示。  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 用戶端必須提供實作雙工合約回呼介面的類別，用於接收來自服務的訊息。 以下範例程式碼將示範實作 `CallbackHandler` 介面的 `ICalculatorDuplexCallback` 類別。  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 WCF 用戶端所產生的雙工合約需要<xref:System.ServiceModel.InstanceContext>在建構時提供的類別。 這個 <xref:System.ServiceModel.InstanceContext> 類別會用來做為站台，讓物件實作回呼介面並處理服務傳回的訊息。 <xref:System.ServiceModel.InstanceContext> 類別是以 `CallbackHandler` 類別的執行個體所建構。 這個物件會處理回呼介面上，從服務傳回至用戶端的訊息。  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 服務的組態必須進行設定，以提供同時支援工作階段通訊和雙工通訊的繫結。 `wsDualHttpBinding` 項目支援工作階段通訊，並且藉由提供雙重 HTTP 連接 (一個方向一個連接) 允許雙工通訊。  
  
 在用戶端上，您必須設定伺服器可用來連接用戶端的位址，如下面的範例組態中所示。  
  
  
  
> [!NOTE]
>  無法使用安全對話來進行驗證的非雙工用戶端通常會擲回 <xref:System.ServiceModel.Security.MessageSecurityException>。 不過，如果使用安全對話的雙工用戶端驗證失敗，則用戶端會收到 <xref:System.TimeoutException>。  
  
 如果您使用 `WSHttpBinding` 項目建立用戶端/服務，但是未包含用戶端回呼端點，則會收到以下錯誤。  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 下列範例程式碼示範如何指定用戶端端點位址以程式設計的方式。
  
```csharp  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")  
```

 以下範例程式碼將示範如何在組態中指定用戶端端點位址。  
  
```xml  
<client>  
    <endpoint name ="ServerEndpoint"   
          address="http://localhost:12000/DuplexTestUsingConfig/Server"  
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"   
            binding="wsDualHttpBinding"  
           contract="IDuplexTest" />  
</client>  
<bindings>  
    <wsDualHttpBinding>  
        <binding name="WSDualHttpBinding_IDuplexTest"    
          clientBaseAddress="http://localhost:8000/myClient/" >  
            <security mode="None"/>  
         </binding>  
    </wsDualHttpBinding>  
</bindings>  
```  
  
> [!WARNING]
>  此雙工模型不會自動偵測服務或用戶端關閉其通道的時間。 因此，如果某個用戶端意外終止，預設不會通知此服務，或者如果某個用戶端意外終止，也不會通知此服務。 用戶端和服務可以實作自己的通訊協定來通知彼此 (如果選擇這樣做的話)。  
  
## <a name="see-also"></a>另請參閱  
 [雙面](../../../../docs/framework/wcf/samples/duplex.md)  
 [指定用端執行階段行為](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [如何：建立通道處理站並使用它來建立與管理通道](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
