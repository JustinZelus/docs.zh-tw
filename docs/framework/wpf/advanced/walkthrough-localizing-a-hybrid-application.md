---
title: 逐步解說：當地語系化混合應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 010c8f75a1151f5606be5ffa63d60fca364bdb59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>逐步解說：當地語系化混合應用程式
本逐步解說會示範如何當地語系化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的項目[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-混合式應用程式。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]主應用程式專案。  
  
-   新增可當地語系化的內容。  
  
-   啟用當地語系化。  
  
-   指派資源識別碼。  
  
-   使用 LocBaml 工具產生附屬組件。  
  
 在此逐步解說中所述的工作的完整程式碼清單，請參閱[當地語系化混合式應用程式範例](http://go.microsoft.com/fwlink/?LinkID=160015)。  
  
 完成之後，就會有當地語系化的混合應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-windows-forms-host-project"></a>建立 Windows Forms 主專案  
 第一個步驟是建立[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式專案，並新增[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具有將當地語系化的內容項目。  
  
#### <a name="to-create-the-host-project"></a>建立主專案  
  
1.  建立 WPF 應用程式專案，名為`LocalizingWpfInWf`。 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  新增[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>項目稱為`SimpleControl`至專案。  
  
3.  使用<xref:System.Windows.Forms.Integration.ElementHost>放置控制項`SimpleControl`項目表單上的。 如需詳細資訊，請參閱[逐步解說： 將 3-D WPF 複合控制項在 Windows Form 中裝載](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。  
  
## <a name="adding-localizable-content"></a>新增可當地語系化的內容  
 接下來，您將加入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]標籤控制項，並設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目的內容，可當地語系化的字串。  
  
#### <a name="to-add-localizable-content"></a>新增可當地語系化的內容  
  
1.  在 [方案總管] 中，按兩下**SimpleControl.xaml**中將它開啟[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
2.  設定的內容<xref:System.Windows.Controls.Button>控制使用下列程式碼。  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  在 [方案總管] 中，按兩下**Form1**在 Windows Form 設計工具中開啟它。  
  
4.  開啟 [工具箱]，然後按兩下**標籤**將標籤控制項新增至表單。 將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設定為 `"Hello"`。  
  
5.  按 F5 鍵建置並執行應用程式。  
  
     這兩個`SimpleControl`項目和標籤控制項： 將文字顯示 **"Hello"**。  
  
## <a name="enabling-localization"></a>啟用當地語系化  
 Windows Forms 設計工具提供在附屬組件中啟用當地語系化的設定。  
  
#### <a name="to-enable-localization"></a>啟用當地語系化  
  
1.  在 [方案總管] 中，按兩下**Form1.cs**在 Windows Form 設計工具中開啟它。  
  
2.  在 [屬性] 視窗中，將表單的值**Localizable**屬性`true`。  
  
3.  在 [屬性] 視窗中設定的值**語言**屬性**西班牙文 （西班牙）**。  
  
4.  在 [Windows Forms 設計工具] 中，選取 Label 控制項。  
  
5.  在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Control.Text%2A>屬性`"Hola"`。  
  
     名為 Form1.es-ES.resx 的新資源檔會新增至專案。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下**Form1.cs**按一下**檢視程式碼**程式碼編輯器中開啟它。  
  
7.  下列程式碼複製到`Form1`建構函式之前呼叫`InitializeComponent`。  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  在 [方案總管] 中，以滑鼠右鍵按一下**LocalizingWpfInWf**按一下**卸載專案**。  
  
     專案名稱會標記為**（無法使用）**。  
  
9. 以滑鼠右鍵按一下**LocalizingWpfInWf**，然後按一下**編輯 LocalizingWpfInWf.csproj**。  
  
     隨即在程式碼編輯器中開啟專案檔。  
  
10. 將下列行複製到第一個`PropertyGroup`專案檔中。  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. 儲存並關閉專案檔。  
  
12. 在 [方案總管] 中，以滑鼠右鍵按一下**LocalizingWpfInWf**按一下**重新載入專案**。  
  
## <a name="assigning-resource-identifiers"></a>指派資源識別碼  
 您可以使用資源識別碼，將可當地語系化的內容對應至資源組件。 MsBuild.exe 應用程式會自動指派資源識別項，當您指定`updateuid`選項。  
  
#### <a name="to-assign-resource-identifiers"></a>指派資源識別碼  
  
1.  從 [開始] 功能表中，開啟 Visual Studio 命令提示字元。  
  
2.  使用下列命令，將資源識別碼指派給可當地語系化的內容。  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  在 [方案總管] 中，按兩下**SimpleControl.xaml**程式碼編輯器中開啟它。 您會看到`msbuild`命令已加入`Uid`屬性的所有項目。 這有助於透過資源識別碼指派進行當地語系化。  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  按 F6 建置此方案。  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>使用 LocBaml 產生附屬組件  
 當地語系化的內容會儲存在資源專用*附屬組件*。 使用命令列工具 LocBaml.exe 產生當地語系化的組件，如您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容。  
  
#### <a name="to-produce-a-satellite-assembly"></a>產生附屬組件  
  
1.  將 LocBaml.exe 複製至專案的 obj\Debug 資料夾。 如需詳細資訊，請參閱[當地語系化應用程式](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。  
  
2.  在 [命令提示字元] 視窗中，使用下列命令來將資源字串擷取至暫存檔。  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  使用 Visual Studio 或其他文字編輯器中開啟 temp.csv 檔案。 取代字串`"Hello"`與西班牙文的翻譯， `"Hola"`。  
  
4.  儲存 temp.csv 檔案。  
  
5.  使用下列命令來產生已當地語系化的資源檔。  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     LocalizingWpfInWf.g.es-ES.resources 檔案會在 obj\Debug 資料夾中建立。  
  
6.  使用下列命令來建置已當地語系化的附屬組件。  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     LocalizingWpfInWf.resources.dll 檔案會在 obj\Debug 資料夾中建立。  
  
7.  將 LocalizingWpfInWf.resources.dll 檔案複製至專案的 bin\Debug\es-ES 資料夾。 取代現有檔案。  
  
8.  執行 LocalizingWpfInWf.exe，其位於專案的 bin\Debug 資料夾中。 請不要重建應用程式，否則將會覆寫附屬組件。  
  
     應用程式會顯示當地語系化字串，而不是英文字串。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [逐步解說： 當地語系化 Windows Form](http://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
