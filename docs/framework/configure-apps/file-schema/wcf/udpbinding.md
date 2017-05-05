---
title: "&lt;udpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;udpBinding&gt;
用來設定 <xref:System.ServiceModel.UdpBinding> 繫結的組態元素。  
  
## 語法  
  
```  
  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength=”Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxPendingMessagesTotalSize=”Integer”  
       maxReceivedMessageSize="Integer"  
       maxRetransmitCount=”Integer”  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"      
            maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|`duplicateMessageHistoryLength`|指定重複訊息記錄長度的整數值。|  
|`maxBufferPoolSize`|整數值，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。  預設值為 524288 \(0x80000\) 位元組。|  
|`maxBufferSize`|整數值，指定儲存訊息之緩衝區的大小上限 \(以位元組為單位\)。在為此繫結設定的端點處理訊息時，可以將訊息儲存在緩衝區中。  預設值為 65,536 位元組。|  
|`maxPendingMessagesTotalSize`|整數值，指定已接收但尚未從個別通道執行個體的輸入佇列移除的訊息數目上限。|  
|`maxReceivedMessageSize`|正整數，定義在使用此繫結設定之通道上可以接收的訊息大小上限 \(以位元組為單位，包括標頭\)。  如果對收件者而言訊息太大，寄件者便會收到 SOAP 錯誤。  收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。  預設為 65,536 個位元組。|  
|`maxRetransmitCount`|指定重新傳輸訊息數目上限的整數值。|  
|`multicastInterfaceId`|指定多點傳送介面 ID 的整數值。|  
|`name`|包含繫結之組態名稱的字串。  這個值應該是唯一的，因為它會當做繫結的識別使用。  每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。  此外，這個名稱在相同型別的繫結中也是唯一的。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|`receiveTimeout`|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:10:00。|  
|`sendTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。  這個值應該大於或等於 <xref:System.TimeSpan.Zero>。  預設為 00:01:00。|  
|`textEncoding`|設定要在繫結上發出訊息時使用的字元集編碼方式。  有效值包括以下的值：<br /><br /> -   BigEndianUnicode：Unicode BigEndian 編碼方式。<br />-   Unicode：16 位元編碼方式。<br />-   UTF8：8 位元編碼方式。<br /><br /> 預設為 UTF8。  此屬性的型別為 <xref:System.Text.Encoding>。|  
|`timeToLive`|指定繫結存留時間的 timespan 值。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。  此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<繫結\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## 備註  
 UdpBinding 允許 WCF 服務透過 UDP 傳輸進行通訊。  它允許「射後不理」\(Fire And Forget\) 訊息交換，也就是用戶端傳送訊息給服務，並不預期有回應傳回。  
  
## 範例  
 下列範例示範如何使用 \<`udpBinding`\> 項目設定 <xref:System.ServiceModel.UdpBinding>。  
  
```xml  
<udpBinding>  
        <binding  closeTimeout="00:10:00"  
                   duplicateMessageHistoryLength="100"  
                   maxBufferPoolSize="100"  
                   maxPendingMessagesTotalSize="100000"  
                   maxReceivedMessageSize="65536"  
                    maxRetransmitCount="10"  
                   multicastInterfaceId="00000"  
                   name="myUdpBinding"  
                   openTimeout="00:10:00"  
                   receiveTimeout="00:10:00"  
                   sendTimeout="00:10:00"  
                   textEncoding="utf-8"  
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.Binding>   
 <xref:System.ServiceModel.Channels.BindingElement>   
 <xref:System.ServiceModel.BasicHttpBinding>   
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>   
 [繫結](../../../../../docs/framework/wcf/bindings.md)   
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/zh-tw/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<繫結\>](../../../../../docs/framework/misc/binding.md)