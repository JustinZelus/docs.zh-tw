---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle
## <a name="properties"></a>屬性  
  
|||  
|-|-|  
|ID|1041|  
|關鍵字|WFRuntime|  
|層級|資訊|  
|通道|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>描述  
 表示工作流程應用程式處於閒置狀態且為永續性。 工作流程應用程式將會閒置或持續。  
  
## <a name="message"></a>訊息  
 WorkflowApplication Id: '%1' 處於閒置狀態且可保存。  將會採取下列動作: %2。  
  
## <a name="details"></a>詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:string|工作流程應用程式 ID|  
|ActionTaken|xs:string|將要對工作流程應用程式要採取的動作。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|
