---
title: ICoreClrDebugTarget::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c09b70b5afb0561d32e55dd89df6cac083abc068
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses 方法
列舉在遠端電腦上執行的處理序。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcProcs`  
 [out] `ppProcs` 中傳回的處理序數目。 這個值可以是 0 (零)。  
  
 `ppProcs`  
 [out]陣列[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) ，此結構表示遠端電腦上執行的處理程序。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 無法為 `ppProcs` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  
 若要釋放由這個方法所配置的記憶體，請呼叫[icoreclrdebugtarget:: Freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces.h  
  
 **程式庫：** mscordbi_macx86.dll  
  
 **.NET framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>另請參閱  
 [ICoreClrDebugTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
