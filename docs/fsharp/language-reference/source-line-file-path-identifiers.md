---
title: 原始碼程式行、檔案與路徑識別項 (F#)
description: '了解如何使用內建 F # 識別碼的值可讓您存取原始程式碼行號、 目錄和檔案名稱，在程式碼中。'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="source-line-file-and-path-identifiers"></a>原始碼程式行、檔案與路徑識別項

識別項`__LINE__`，`__SOURCE_DIRECTORY__`和`__SOURCE_FILE__`是內建可讓您存取您的程式碼的來源行號、 目錄和檔案名稱的值。


## <a name="syntax"></a>語法

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>備註
每個這些值都有類型`string`。

下表摘要說明原始程式行、 檔案和 F # 中可用的路徑識別項。 這些識別項不是前置處理器巨集;它們是編譯器可辨識的內建值。

|預先定義的識別項|描述|
|---------------------|-----------|
|`__LINE__`|判斷值為目前的行號，考慮`#line`指示詞。|
|`__SOURCE_DIRECTORY__`|評估目前的完整路徑的來源目錄中，為考慮`#line`指示詞。|
|`__SOURCE_FILE__`|判斷值為目前的來源檔案名稱和其路徑中，考慮`#line`指示詞。|
如需有關`#line`指示詞，請參閱[編譯器指示詞](compiler-directives.md)。

## <a name="example"></a>範例

下列程式碼範例示範如何使用這些值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

輸出：

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>另請參閱
[編譯器指示詞](compiler-directives.md)

[F# 語言參考](index.md)
