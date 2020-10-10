---
title: Método PrepareHeaderDrag (System. Windows. Controls. GridViewHeaderRowPresenter)
description: Saiba mais sobre o método WPF privado chamado PrepareHeaderDrag.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 6d806b8a50de3234cd04198f4ab86621dcd6ede1
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877736"
---
# <a name="prepareheaderdrag-method"></a><span data-ttu-id="72e22-103">Método PrepareHeaderDrag</span><span class="sxs-lookup"><span data-stu-id="72e22-103">PrepareHeaderDrag method</span></span>

<span data-ttu-id="72e22-104">Prepara o cabeçalho de coluna especificado para reordenação.</span><span class="sxs-lookup"><span data-stu-id="72e22-104">Prepares the specified column header for reordering.</span></span>

```csharp
private void PrepareHeaderDrag(GridViewColumnHeader header, Point pos, Point relativePos, bool cancelInvoke)
```

> [!WARNING]
> <span data-ttu-id="72e22-105">Esse método é privado e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="72e22-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="72e22-106">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="72e22-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="72e22-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72e22-107">Parameters</span></span>

<span data-ttu-id="72e22-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span><span class="sxs-lookup"><span data-stu-id="72e22-108">`header` <xref:System.Windows.Controls.GridViewColumnHeader></span></span>\
<span data-ttu-id="72e22-109">O cabeçalho da coluna a ser preparada para reordenação.</span><span class="sxs-lookup"><span data-stu-id="72e22-109">The column header to prepare for reordering.</span></span>

<span data-ttu-id="72e22-110">`pos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="72e22-110">`pos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="72e22-111">A posição, em relação a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> , onde o arrasto é iniciado.</span><span class="sxs-lookup"><span data-stu-id="72e22-111">The position, relative to <xref:System.Windows.Controls.GridViewHeaderRowPresenter>, where the dragging starts.</span></span>

<span data-ttu-id="72e22-112">`relativePos` <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="72e22-112">`relativePos` <xref:System.Windows.Point></span></span>\
<span data-ttu-id="72e22-113">A posição, em relação a `header` , onde o arrasto é iniciado.</span><span class="sxs-lookup"><span data-stu-id="72e22-113">The position, relative to `header`, where the dragging starts.</span></span>

<span data-ttu-id="72e22-114">`cancelInvoke` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="72e22-114">`cancelInvoke` <xref:System.Boolean></span></span>\
<span data-ttu-id="72e22-115">`true` para cancelar a reordenação; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="72e22-115">`true` to cancel the reordering; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="72e22-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72e22-116">Requirements</span></span>

<span data-ttu-id="72e22-117">**Namespace:** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="72e22-117">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="72e22-118">**Assembly:** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="72e22-118">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="72e22-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="72e22-119">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
