---
title: ICorRuntimeHost 介面
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: facc756061e7eb381abecc544ca4b15bfdde6343
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost 介面
提供方法，讓主應用程式啟動和停止 common language runtime (CLR) 明確地建立和設定應用程式定義域，若要存取的預設網域，並列舉處理序中執行的所有網域。  
  
 在.NET Framework 2.0 版中，這個介面由取代[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|將定義域列舉值重設回網域清單的開頭。|  
|[CreateDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|建立應用程式定義域。 呼叫端會收到類型的介面指標<xref:System._AppDomain>型別的執行個體<xref:System.AppDomain?displayProperty=nameWithType>。|  
|[CreateDomainEx 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|建立應用程式定義域。 這個方法可讓呼叫端將 IAppDomainSetup 執行個體來設定傳回的其他功能<xref:System._AppDomain>執行個體。|  
|[CreateDomainSetup 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|取得類型的介面指標`IAppDomainSetup`至<xref:System.AppDomainSetup>執行個體。 `IAppDomainSetup` 提供方法來設定應用程式定義域的層面，才能建立。|  
|[CreateEvidence 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|取得類型的介面指標<xref:System.Security.Principal.IIdentity>，可讓主應用程式建立要傳遞給安全性辨識項[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)。|  
|[CreateLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|請勿使用。|  
|[CurrentDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|取得類型的介面指標<xref:System._AppDomain>，代表目前執行緒上載入的網域。|  
|[DeleteLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|請勿使用。|  
|[EnumDomains 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|取得目前的處理序中網域的列舉值。|  
|[GetConfiguration 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|取得物件，可讓主機指定的 CLR 回呼組態。|  
|[GetDefaultDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|取得類型的介面指標<xref:System._AppDomain>，代表目前的處理序的預設網域。|  
|[LocksHeldByLogicalThread 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|請勿使用。|  
|[MapFile 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|將指定的檔案對應到記憶體中。 這個方法已過時。|  
|[NextDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|取得列舉中的下一個網域的介面指標。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|啟動 CLR。|  
|[Stop 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|停止執行目前處理序的執行階段中的程式碼。|  
|[SwitchInLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|請勿使用。|  
|[SwitchOutLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|請勿使用。|  
|[UnloadDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|卸載指定的應用程式定義域，從目前的處理序。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0、 1.1  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomain>  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [執行階段主機](http://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
