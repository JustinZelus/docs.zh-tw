---
title: '&lt;certificate&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 02444e66326bec10150ba52541aedd02ec7bb784
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificategt-element"></a>&lt;certificate&gt; 項目
指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<clientCredentials>  
\<對等 >  
\<憑證 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`findValue`|字串，其中包含要在 X.509 憑證存放區內搜尋的值。 屬性所包含的型別必須滿足指定之 `x509FindType` 的需求。 預設為空字串。|  
|`storeLocation`|指定 X.509 憑證存放區的位置，用戶端會使用該憑證存放區針對這個位置驗證對等的憑證。 有效值包括以下的值：<br /><br /> -LocalMachine: 指派憑證存放區至本機電腦。<br />-CurrentUser: 指派憑證存放區目前的使用者。<br /><br /> 預設為 LocalMachine。|  
|`storeName`|指定要開啟之 X.509 憑證存放區的名稱。 有效值包括以下的值：<br /><br /> -AddressBook： 其他使用者的憑證存放區。<br />-AuthRoot： 協力廠商憑證授權單位 (Ca) 的存放區的憑證。<br />-CertificateAuthority： 中繼憑證授權單位 (Ca) 憑證存放區。<br />-不允許： 憑證已撤銷之憑證存放區。<br />-My： 憑證個人憑證存放區。<br />-Root： 信任的根憑證授權單位 (Ca) 憑證存放區。<br />-TrustedPeople： 直接信任之人員和資源的憑證存放區。<br />-TrustedPublisher： 直接信任之發行者的憑證存放區。<br /><br /> 預設為 My。|  
|`X509FindType`|定義要執行之 X.509 搜尋的類型。 有效值包括以下的值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 屬性所包含的型別必須滿足指定之 `X509FindType` 的需求。<br /><br /> 預設值為 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定驗證對等用戶端時所使用的認證。|  
  
## <a name="remarks"></a>備註  
 這個組態項目包含在驗證對等網狀結構中鄰接項目時所使用的 X509Certificate2 執行個體。  
  
 如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="example"></a>範例  
 下列程式碼說明如何尋找對等案例中使用的憑證。  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 [使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [對等通道訊息驗證](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [對等通道自訂驗證](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [保護對等通道應用程式的安全](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
