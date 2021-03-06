---
title: 部分信任最佳做法
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: fca975ff4216384b970535273511eb07cd6ded68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="partial-trust-best-practices"></a>部分信任最佳做法
在部分信任環境中執行 Windows Communication Foundation (WCF) 時，本主題會描述最佳作法。  
  
## <a name="serialization"></a>序列化  
 在部分信任的應用程式中使用 <xref:System.Runtime.Serialization.DataContractSerializer> 時，請套用下列做法。  
  
-   所有可序列化的型別必須明確地加上 `[DataContract]` 屬性標記。 部分信任環境不支援下列技巧：  
  
-   使用 <xref:System.SerializableAttribute> 來標示要序列化的類別。  
  
-   實作 <xref:System.Runtime.Serialization.ISerializable> 介面以允許類別控制自己的序列化處理序。  
  
### <a name="using-datacontractserializer"></a>使用 DataContractSerializer  
  
-   所有加上 `[DataContract]` 屬性標記的型別必須是公用型別。 非公用型別無法在部分信任環境中進行序列化。  
  
-   可序列化之 `[DataContract]` 型別中的所有 `[DataContract]` 成員必須是公用的。 具有非公用 `[DataMember]` 的型別無法在部分信任環境中進行序列化。  
  
-   負責處理序列化事件 (例如，`OnSerializing`, `OnSerialized`、`OnDeserializing`，和 `OnDeserialized`) 的方法必須宣告為公用。 但是，同時支援 <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> 的明確與隱含實作。  
  
-   在標示為 `[DataContract]` 的組件中實作的 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 型別不可以在型別建構函式中執行安全性相關動作，因為 <xref:System.Runtime.Serialization.DataContractSerializer> 不會在還原序列化期間呼叫新產生物件的建構函式。 具體來說，`[DataContract]` 型別必須避免使用下列常見的安全性技巧：  
  
-   藉由將型別建構函式標示為內部或私用來嘗試限制部分信任存取。  
  
-   藉由新增 `[LinkDemand]` 至型別建構函式來限制型別的存取。  
  
-   假定因為物件已經成功產生，任何由建構函式所強制執行的驗證檢查也已通過。  
  
### <a name="using-ixmlserializable"></a>使用 IXmlSerializable  
 下列最佳做法適用於可實作 <xref:System.Xml.Serialization.IXmlSerializable> 且可透過 <xref:System.Runtime.Serialization.DataContractSerializer> 進行序列化的型別：  
  
-   <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> 靜態方法實作必須是 `public`。  
  
-   實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的執行個體方法必須是 `public`。  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>使用來自充分信任平台程式碼 (允許部分信任呼叫端的呼叫) 的 WCF  
 WCF 部分信任安全性模型假設 WCF 公用方法或屬性的任何呼叫端在裝載應用程式的程式碼存取安全性 (CAS) 內容中執行。 WCF 也會假設每個都有該只有一個應用程式的安全性內容<xref:System.AppDomain>，且此內容建立在<xref:System.AppDomain>所信任的主控件的建立時間 (例如，藉由呼叫<xref:System.AppDomain.CreateDomain%2A>或 ASP.NET 應用程式管理員)。  
  
 這個安全性模型適用於由使用者撰寫且無法判斷提示其他 CAS 權限的應用程式，例如在中度信任 ASP.NET 應用程式中執行的使用者程式碼。 不過，完全受信任的平台程式碼 （例如，協力廠商組件安裝在全域組件快取中且接受來自部分信任的程式碼呼叫） 必須特別小心 WCF 呼叫代表部分信任應用程式避免帶入應用程式層級的安全性弱點。  
  
 完全信任程式碼應該避免更改目前執行緒的 CAS 權限集 (藉由呼叫<xref:System.Security.PermissionSet.Assert%2A>， <xref:System.Security.PermissionSet.PermitOnly%2A>，或<xref:System.Security.PermissionSet.Deny%2A>) 在 WCF 應用程式開發介面呼叫代表部分信任程式碼之前。 判斷提示、拒絕或以其他方式建立無關應用程式層級安全性內容的執行緒特定權限內容可能會導致未預期的行為。 根據所使用的應用程式，這項行為可能會導致應用程式層級的安全性弱點。  
  
 WCF 使用執行緒特定權限內容的呼叫必須準備好處理下列可能發生的情況的程式碼：  
  
-   作業期間可能無法維護執行緒特定的安全性內容，進而導致可能發生的安全性例外狀況。  
  
-   內部 WCF 程式碼，以及任何使用者提供的回呼可能會執行不同的安全性內容以外的呼叫已原始啟始。 這些內容包括：  
  
    -   應用程式權限內容。  
  
    -   先前由目前執行的存留期間呼叫 WCF 應用程式使用其他使用者執行緒建立任何執行緒特定權限內容<xref:System.AppDomain>。  
  
 WCF 會保證部分信任的程式碼無法取得完全信任權限，除非這類權限會由完全信任的元件呼叫 WCF 公用 Api 之前判斷提示。 但是，它不保證將完全信任的判斷提示影響隔離在特定執行緒、作業或使用者動作之外。  
  
 最佳做法是，避免呼叫 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A> 或 <xref:System.Security.PermissionSet.Deny%2A> 來建立執行緒特定權限內容。 反之，應該針對應用程式本身授與或拒絕權限，這樣就不會需要 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A> 或 <xref:System.Security.PermissionSet.PermitOnly%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
