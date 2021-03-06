---
title: 資料服務版本控制 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: 0d77f54b5ef20db81c3c20f486ac7314f73aece8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-service-versioning-wcf-data-services"></a>資料服務版本控制 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]可讓您建立資料服務，讓用戶端可以存取資料，做為使用 Uri 中的資料模型為基礎的資源。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 也支援服務作業的定義。 初始部署並在其存留期期間潛在進行數次之後，可能會因為各種原因而需要變更這些資料服務 (例如變更商務需要、資訊技術需求) 或處理其他問題。 當您針對現有的資料服務進行變更時，必須考慮是否要定義新的資料服務版本，以及如何妥善地將對於現有用戶端應用程式的影響降至最低。 本主題提供建立新資料服務版本時機和方式的指引。 本主題也會描述 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 如何處理支援不同版本 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定之用戶端與資料服務之間的交換。  
  
## <a name="versioning-a-wcf-data-service"></a>WCF Data Services 的版本控制  
 部署資料服務並取用資料之後，對於資料服務的變更便有可能造成與現有用戶端應用程式的相容性問題。 不過，由於服務的整體商務需求通常需要變更，因此您必須考慮建立新資料服務版本的時機與方式，並將對於用戶端應用程式的影響降至最低。  
  
### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>建議新資料服務版本的資料模型變更  
 考慮是否要發行新資料服務版本時，最好先了解不同種類的變更影響用戶端應用程式的方式。 對於可能要求您建立新資料服務版本之資料服務的變更可分成下列兩種類別：  
  
-   對於服務合約的變更—其中包括服務作業的更新、對於實體集 (摘要) 存取範圍的變更、版本變更，以及對於服務行為的其他變更。  
  
-   對於資料合約的變更—其中包括對於資料模型、摘要格式或摘要自訂的變更。  
  
 下表詳細說明您應該考慮發行新資料服務版本的哪些變更種類：  
  
|變更類型|需要新版本|不需要新版本|  
|--------------------|----------------------------|----------------------------|  
|服務作業|加入新的參數<br />變更傳回型別<br />移除服務作業|刪除現有的參數<br />新增新的服務作業|  
|服務行為|-停用計數要求<br />-停用投影支援<br />-增加所需的資料服務版本|-啟用計數要求<br />-啟用投影支援<br />-減少所需的資料服務版本|  
|實體集權限|限制實體集權限<br />變更回應碼 (新第一位數值) <sup>1</sup>|放寬實體集權限<br />變更回應碼 (相同第一位數值)|  
|實體屬性|-移除現有的內容或關聯性<br />新增非 null 的屬性<br />變更現有的屬性|新增可為 null 的屬性<sup>2</sup>|  
|實體集|移除實體集|加入衍生的類型<br />變更基底類型<br />加入實體集|  
|摘要自訂|變更實體屬性對應||  
  
 <sup>1</sup>這可能取決於用戶端應用程式依賴接收特定錯誤碼嚴格程度。  
  
 <sup>2</sup>您可以設定<xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A>屬性`true`讓用戶端略過資料服務所傳送的用戶端上未定義任何新內容。 不過，進行插入時，用戶端沒有包含在 POST 要求中的屬性會設為其預設值。 若是更新，屬性中用戶端未知的任何現有資料都可能會以預設值覆寫。 在此情況下，您應該將更新當做 MERGE 要求傳送，這是預設值。 如需詳細資訊，請參閱[管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)。  
  
### <a name="how-to-version-a-data-service"></a>如何進行資料服務的版本控制  
 必要時，您可以使用更新的服務合約或資料模型建立新的服務執行個體，藉以定義新的資料服務版本。 接著，您要使用新的 URI 端點公開這個新服務，以區別舊版本。 例如：  
  
-   舊版本：`http://services.odata.org/Northwind/v1/Northwind.svc/`  
  
-   新版本：`http://services.odata.org/Northwind/v2/Northwind.svc/`  
  
 升級資料服務時，用戶端也需要根據新的資料服務中繼資料進行更新，並使用新的根 URI。 如果可能，您應該維護資料服務的舊版本，以支援尚未進行升級以使用新版本的用戶端。 不再需要舊版本的資料服務時，可以將其移除。 您應該考慮在外部組態檔中維護資料服務端點 URI。  
  
## <a name="odata-protocol-versions"></a>OData 通訊協定版本  
 新版本的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]會釋放，用戶端應用程式可能不使用相同版本的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]資料服務所支援的通訊協定。 舊版用戶端應用程式可以存取支援新版 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的資料服務。 用戶端應用程式也使用較新版的[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫，可支援較新版的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]比正在存取資料服務。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 利用所提供的支援[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]來處理這類版本控制案例。 此外，也支援產生及使用資料模型中繼資料來建立用戶端資料服務類別，用戶端使用不同版本的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]與資料服務所使用。 如需詳細資訊，請參閱[OData： 通訊協定版本控制](http://go.microsoft.com/fwlink/?LinkId=186071)。  
  
### <a name="version-negotiation"></a>版本交涉  
 資料服務可以設定來定義的最新版本[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]將服務，不論哪個版本的用戶端要求所使用的通訊協定。 您可以藉由指定<xref:System.Data.Services.Common.DataServiceProtocolVersion>值<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>屬性<xref:System.Data.Services.DataServiceBehavior>資料服務所使用。 如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 當應用程式使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫來存取資料服務時，程式庫會根據 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 的版本和您應用程式中所使用的特性，自動將這些標頭設定為正確的值。 根據預設，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]使用支援要求的作業的最低通訊協定版本。  
  
 下表詳細說明 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 和 [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] 的版本，其中包含特定版本 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 通訊協定的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 支援。  
  
|[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定版本|下列版本引入的支援|  
|-----------------------------------------------------------------------------------|----------------------------|  
|第 1 版|-   [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Service Pack 1 (SP1)<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] 第 3 版|  
|第 2 版|-   [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]<br />-若要更新[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]SP1。 您可以下載並安裝更新的[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=158125)。<br />-   [!INCLUDE[silverlight](../../../../includes/silverlight-md.md)] 第 4 版|  
|第 3 版|-您可以下載並安裝支援的發行前版本[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從第 3 版[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=203885)。|  
  
### <a name="metadata-versions"></a>中繼資料版本  
 根據預設，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會使用 1.1 版的 CSDL 來代表資料模型。 這就是以反映提供者或自訂資料服務提供者為基礎之資料模型的情況。 但是，當使用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 來定義資料模型時，傳回的 CSDL 版本會與 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 所使用的版本相同。 CSDL 的版本取決於命名空間的[結構描述項目](http://msdn.microsoft.com/library/396074d8-f99c-4f50-a073-68bce848224f)。 如需詳細資訊，請參閱規格[ \[MC-CSDL\]： 概念結構定義檔案格式](http://go.microsoft.com/fwlink/?LinkId=159072)。  
  
 傳回之中繼資料的 `DataServices` 項目還包含 `DataServiceVersion` 屬性，該值與回應訊息中 `DataServiceVersion` 標頭的值相同。 用戶端應用程式，例如**加入服務參考**對話方塊中，在 Visual Studio 中使用這項資訊來產生用戶端資料服務類別使用的版本正確[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]裝載的資料服務。 如需詳細資訊，請參閱[OData： 通訊協定版本控制](http://go.microsoft.com/fwlink/?LinkId=186071)。  
  
## <a name="see-also"></a>另請參閱  
 [資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
