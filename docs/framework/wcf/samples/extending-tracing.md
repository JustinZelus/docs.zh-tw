---
title: 擴充追蹤
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59291b6a57ba602e5fea84dcd571a8d767b7cc04
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="extending-tracing"></a>擴充追蹤
這個範例示範如何在用戶端與服務程式碼中撰寫使用者定義的活動追蹤的擴充 Windows Communication Foundation (WCF) 追蹤功能。 這樣可以讓使用者建立追蹤活動，並將追蹤分組成工作的邏輯單位 (Logical Unit)。 也可以透過傳輸 (在相同的端點內) 以及傳播 (跨端點) 方式來關聯活動。 在此範例中，用戶端與服務都會啟用追蹤。 如需如何在用戶端和服務組態檔中啟用追蹤的詳細資訊，請參閱[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)。  
  
 這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>追蹤與活動傳播  
 使用者定義的活動追蹤 」 可讓使用者建立自己的 「 追蹤 」 活動來群組追蹤成工作邏輯單位的、 透過傳輸和傳播，活動相互關聯，並降低 WCF 追蹤 （例如成本的磁碟空間的效能成本記錄檔）。  
  
### <a name="adding-custom-sources"></a>新增自訂來源  
 使用者定義的追蹤可以同時新增至用戶端與服務程式碼。 加入追蹤來源的用戶端或服務組態檔來允許這些自訂的追蹤以記錄並顯示於[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。 下列程式碼示範如何將名為 `ServerCalculatorTraceSource` 之使用者定義的追蹤來源新增至組態檔。  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>關聯活動  
 若要直接關聯跨端點的活動，在 `propagateActivity` 追蹤來源中的 `true` 屬性必須設定為 `System.ServiceModel`。 此外，而不需要透過 WCF 活動傳播追蹤，ServiceModel 活動追蹤必須關閉。 這項設定將如下列程式碼範例所示。  
  
> [!NOTE]
>  關閉 ServiceModel 活動追蹤的方式不同於指定追蹤層級 (以設定為 Off 的 `switchValue` 屬性表示)。  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>降低效能成本  
 將 `ActivityTracing` 追蹤來源中的 `System.ServiceModel` 設定為 Off 時會產生追蹤檔，其中只包含使用者定義的活動追蹤，而不包含任何 ServiceModel 活動追蹤。 這樣會使記錄檔的大小變小許多。 不過，有機會處理追蹤 WCF 相互關聯會遺失。  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
