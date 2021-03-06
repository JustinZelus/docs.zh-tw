---
title: CorTypeAttr 列舉
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f71e59eb13321517de61315d3ba06b96c5458f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 列舉
包含值，這些值表示類型中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`tdVisibilityMask`|用於型別可視性資訊。|  
|`tdNotPublic`|指定的類型不是公用的範圍中。|  
|`tdPublic`|指定的類型是公用的範圍中。|  
|`tdNestedPublic`|指定的類型使用巢狀公用可視性。|  
|`tdNestedPrivate`|指定的類型巢狀具有私用的可視性。|  
|`tdNestedFamily`|指定的型別使用家族可視性所產生的巢狀。|  
|`tdNestedAssembly`|指定的類型巢狀與組件可見性。|  
|`tdNestedFamANDAssem`|指定型別使用家族和組件可視性所產生的巢狀。|  
|`tdNestedFamORAssem`|指定型別使用家族或組件可視性所產生的巢狀。|  
|`tdLayoutMask`|取得類型的配置資訊。|  
|`tdAutoLayout`|指定此類型的欄位會自動配置。|  
|`tdSequentialLayout`|指定此類型的欄位會循序配置。|  
|`tdExplicitLayout`|指定明確提供該欄位的配置。|  
|`tdClassSemanticsMask`|取得類型的語意資訊。|  
|`tdClass`|指定此類型為類別。|  
|`tdInterface`|指定此類型為介面。|  
|`tdAbstract`|指定此類型為抽象。|  
|`tdSealed`|指定類型，無法擴充。|  
|`tdSpecialName`|指定類別名稱是特殊。 其名稱會說明如何。|  
|`tdImport`|指定的類型匯入。|  
|`tdSerializable`|指定的型別是可序列化。|  
|`tdWindowsRuntime`|指定此類型為[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。|  
|`tdStringFormatMask`|取得如何編碼和格式字串的相關資訊。|  
|`tdAnsiClass`|指定此類型會解譯為 ANSI LPTSTR。|  
|`tdUnicodeClass`|指定此類型會解譯為 Unicode LPTSTR。|  
|`tdAutoClass`|指定此類型會自動解譯 LPTSTR。|  
|`tdCustomFormatClass`|指定類型具有非標準的編碼，依指定`CustomFormatMask`。|  
|`tdCustomFormatMask`|您可以使用這個遮罩，取得原生 interop 的非標準編碼資訊。 未指定這些兩位元值的意義。|  
|`tdBeforeFieldInit`|指定第一次嘗試存取的靜態欄位之前，必須初始化型別。|  
|`tdForwarder`|指定的已匯出類型，以及類型轉送子。|  
|`tdReservedMask`|這個旗標，而且下列旗標，則會由 common language runtime 內部使用。|  
|`tdRTSpecialName`|指定通用語言執行平台應該檢查名稱編碼。|  
|`tdHasSecurity`|指定類型具有與其相關聯的安全性。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
