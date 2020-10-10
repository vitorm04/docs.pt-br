---
title: Método FindHeaderByColumn (System. Windows. Controls. GridViewHeaderRowPresenter)
description: Saiba mais sobre o método WPF privado chamado FindHeaderByColumn.
ms.date: 09/25/2020
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn
api_location:
- PresentationFramework.dll
api_type:
- Assembly
ms.openlocfilehash: 88ed2928f86602d1078488354de6d5267c0311f5
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877739"
---
# <a name="findheaderbycolumn-method"></a><span data-ttu-id="a7e57-103">Método FindHeaderByColumn</span><span class="sxs-lookup"><span data-stu-id="a7e57-103">FindHeaderByColumn method</span></span>

<span data-ttu-id="a7e57-104">Localiza o cabeçalho de coluna da coluna especificada na árvore visual.</span><span class="sxs-lookup"><span data-stu-id="a7e57-104">Finds the column header for the specified column in the visual tree.</span></span>

```csharp
private GridViewColumnHeader FindHeaderByColumn(GridViewColumn column)
```

> [!WARNING]
> <span data-ttu-id="a7e57-105">Esse método é privado e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="a7e57-105">This method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a7e57-106">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="a7e57-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="a7e57-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7e57-107">Parameters</span></span>

<span data-ttu-id="a7e57-108">`column` <xref:System.Windows.Controls.GridViewColumn></span><span class="sxs-lookup"><span data-stu-id="a7e57-108">`column` <xref:System.Windows.Controls.GridViewColumn></span></span>\
<span data-ttu-id="a7e57-109">A coluna cujo cabeçalho deve ser encontrado e retornado.</span><span class="sxs-lookup"><span data-stu-id="a7e57-109">The column whose header should be found and returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7e57-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a7e57-110">Return value</span></span>

<xref:System.Windows.Controls.GridViewColumnHeader>\
<span data-ttu-id="a7e57-111">O cabeçalho da coluna especificada ou `null` se a coluna especificada não existir.</span><span class="sxs-lookup"><span data-stu-id="a7e57-111">The header of the specified column, or `null` if the specified column doesn't exist.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7e57-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7e57-112">Requirements</span></span>

<span data-ttu-id="a7e57-113">**Namespace:** <xref:System.Windows.Controls></span><span class="sxs-lookup"><span data-stu-id="a7e57-113">**Namespace:** <xref:System.Windows.Controls></span></span>

<span data-ttu-id="a7e57-114">**Assembly:** PresentationFramework.dll</span><span class="sxs-lookup"><span data-stu-id="a7e57-114">**Assembly:** PresentationFramework.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="a7e57-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7e57-115">See also</span></span>

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
