---
title: '&lt;system.runtime.serialization&gt;'
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 6ffd4057028adcd123086173a05164eb5d2622f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemruntimeserializationgt"></a>&lt;system.runtime.serialization&gt;
代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。  
  
 system.runtime.serialization  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節說明屬性、子元素和父元素  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|能夠在還原序列化時，加入要使用的已知型別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|組態的最上層項目。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization>  
 [使用資料合約](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [資料合約已知類型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
