---
title: EBindPolicyLevels 列舉
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列舉
請提供旗標，以指定的層級套用或修改組件的原則。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|指定原則應該套用系統管理員層級。|  
|`ePolicyLevelApp`|指定原則應該套用應用程式層級。|  
|`ePolicyLevelHost`|指定原則應該套用主機層級。|  
|`ePolicyLevelNone`|不指定原則層級旗標。|  
|`ePolicyLevelPublisher`|指定原則應該 publisher 層級套用。|  
|`ePolicyLevelRetargetable`|指定原則應該適用變數層級。|  
|`ePolicyPortability`|指定原則應該支援.NET Framework 組件實作之間的可攜性。 請參閱[ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)組態檔元素。|  
|`ePolicyUnifiedToCLR`|指定的 common language runtime (CLR)，應該統一原則。|  
  
## <a name="remarks"></a>備註  
 此列舉會傳遞至方法的[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)介面以指定在應用程式原則的變更。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [裝載列舉](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
