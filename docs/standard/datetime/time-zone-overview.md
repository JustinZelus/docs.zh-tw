---
title: 時區概觀
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85483e4319b56c0df150558ce6c6a3878a6fa041
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="time-zone-overview"></a>時區概觀

<xref:System.TimeZoneInfo>類別簡化時區感知應用程式的建立。 <xref:System.TimeZone>類別支援使用本地時區與國際標準時間 (UTC)。 <xref:System.TimeZoneInfo>類別支援這兩個區域的相關資訊以及任何時區預先定義的登錄中。 您也可以使用<xref:System.TimeZoneInfo>來定義系統有相關的任何資訊的自訂時區。

## <a name="time-zone-essentials"></a>時區 essentials

時區是使用相同時間的地理區域。 相鄰時區一般但不一定會相差一個小時。 任何全世界時區的時間可以表示為與國際標準時間 (UTC) 的位移。

許多全世界的時區都支援日光節約時間。 日光節約時間會嘗試將日光時數延到最長，方法是將春天或夏初的時間前進一個小時，並在夏末或秋天回復正常 (或標準) 時間。 這些標準時間的變更稱為調整規則。

透過固定或浮動調整規則，可以定義轉換至及轉換自特定時區的日光節約時間。 固定調整規則會設定每年轉換至或轉換自日光節約時間的特定日期。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。 更常見的是浮動調整規則，可設定在特定月份特定週特定一天轉換至或轉換自日光節約時間。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。

對於支援調整規則的時區，轉換至和轉換自日光節約時間會建立兩種異常時間︰無效的時間和不明確的時間。 無效時間是從標準時間轉換到日光節約時間所建立的不存在時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。 不明確的時間是可以對應至單一時區中兩個不同時間的時間。 它是透過從日光節約時間轉換到標準時間所建立。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。

## <a name="time-zone-terminology"></a>時區術語

下表定義在使用時區以及開發時區感知應用程式時常用的詞彙。

| 詞彙            | 定義 |
| --------------- | ---------- |
| 調整規則 | 一種規則，定義何時從標準時間轉換為日光節約時間，以及何時從日光節約時間轉換回標準時間。 每個的調整規則有定義的規則時就地開始和結束日期 （例如，調整規則是就地 1986 年 1 月 1，從 2006 年 12 月 31 日），差異 （的時間量結果的第個應用程式變更所依據的標準時間e 調整規則），以及相關的特定日期和時間調整期間發生的轉換資訊。 轉換可以遵循固定規則或浮動規則。 |
| 不明確的時間  | 可以對應至單一時區中兩個不同時間的時間。 發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 1:00，則凌晨 1:00 與凌晨 1:59:99 之間的每個時間間隔 可以解譯為標準時間或日光節約時間。 |
| 固定規則      | 設定在特定日期轉換至或轉換自日光節約時間的調整規則。 例如，每年在 10 月 25 日從日光節約時間到標準時間的轉換會遵循固定調整規則。 |
| 浮動規則   | 設定在特定月份特定週特定一天轉換至或轉換自日光節約時間的調整規則。 例如，在三月第三個星期日從標準時間到日光節約時間的轉換會遵循浮動調整規則。 |
| 無效時間    | 不存在時間是從標準時間轉換到日光節約時間的成品。 發生時機是往前調整時鐘時間，例如從時區標準時間轉換到其日光節約時間。 例如，如果這項轉換發生在特定日的凌晨 2:00， 並將時間變更為凌晨 3:00，則凌晨 2:00 與凌晨 2:59:99 之間的每個時間間隔 無效。 |
| 轉換時間 | 特定時區中特定時間變更的相關資訊，例如從日光節約時間變更為標準時間，或從標準時間變更為日光節約時間。 |

## <a name="time-zones-and-the-timezoneinfo-class"></a>時區和 TimeZoneInfo 類別

在.NET 中，<xref:System.TimeZoneInfo>物件都代表一個時區。 <xref:System.TimeZoneInfo>類別包含<xref:System.TimeZoneInfo.GetAdjustmentRules%2A>方法會傳回的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件。 這個陣列的每個項目提供在特定時間週期的日光節約時間來回轉換的相關資訊。 （不支援日光節約時間的時區，方法會傳回空陣列。）每個<xref:System.TimeZoneInfo.AdjustmentRule>物件具有<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A>和<xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A>屬性，定義與日光節約時間的特定日期和時間轉換。 <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A>屬性表示該轉換是固定或浮動。

.NET 依賴 Windows 作業系統所提供，並儲存在登錄中時區資訊。 在地球時區的數目，因為並非所有現有的時區表示登錄中。 此外，因為登錄是動態的結構，預先定義的時區可以加入或移除它。 最後，登錄不一定會包含歷史時區資料。 例如，在 Windows XP 中登錄包含時區調整單一組的相關資料。 Windows Vista 簳窱動態時區資料，這表示單一的時區可以有多項調整規則套用至特定的時間間隔的年。 不過，大部分在 Windows Vista 登錄及支援日光節約時間中定義的時區有只需要一個或兩個預先定義的調整規則。

相依性<xref:System.TimeZoneInfo>上登錄類別表示時區感知的應用程式不能是某些特定的時區定義在登錄中。 因此，嘗試具現化特定時區 (非當地時區或代表 UTC 的時區) 應該使用例外狀況處理。 它也應該提供一些方法可讓應用程式繼續如果所需<xref:System.TimeZoneInfo>物件無法從登錄具現化。

若要處理缺少必要的時區，<xref:System.TimeZoneInfo>類別包含<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，可用來建立登錄中找不到自訂時區。 如需有關建立自訂時區的詳細資訊，請參閱[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。 此外，您可以使用<xref:System.TimeZoneInfo.ToSerializedString%2A>方法，以將新建立的時區轉換為字串，並將它儲存在資料存放區 （例如資料庫、 文字檔、 登錄或應用程式資源）。 然後您可以使用<xref:System.TimeZoneInfo.FromSerializedString%2A>方法，以將此字串轉換回<xref:System.TimeZoneInfo>物件。 如需詳細資訊，請參閱[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

因為每個時區都會具備與 UTC 的基底位移，以及具備反映任何現有調整規則之與 UTC 的位移，所以某個時區的時間可以輕鬆地轉換為另一個時區的時間。 基於此目的，<xref:System.TimeZoneInfo>物件包含數種轉換方法，包括：

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>可將 UTC 轉換成指定的時區時間。

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>可將指定的時區時間轉換成 UTC。

* <xref:System.TimeZoneInfo.ConvertTime%2A>可將指定的時區中的時間轉換成另一個指定的時區時間。

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>它會使用時區識別項 (而不是<xref:System.TimeZoneInfo>物件) 做為參數，將在指定的時區的時間轉換成另一個指定的時區時間。

如需各時區間轉換時間的詳細資訊，請參閱[在各時區間轉換時間](../../../docs/standard/datetime/converting-between-time-zones.md)。

## <a name="see-also"></a>另請參閱

[日期、時間和時區](../../../docs/standard/datetime/index.md)
