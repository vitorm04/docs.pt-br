---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496877"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="51136-101">DataGridCellsPanel.BringIndexIntoView gera ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="51136-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="51136-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="51136-102">Details</span></span>

<span data-ttu-id="51136-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> será executado assincronamente quando a virtualização de coluna estiver habilitada, mas as larguras das colunas ainda não estiverem determinadas.</span><span class="sxs-lookup"><span data-stu-id="51136-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="51136-104">Se as colunas forem removidas antes da operação assíncrona, um <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> poderá ocorrer.</span><span class="sxs-lookup"><span data-stu-id="51136-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="51136-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="51136-105">Suggestion</span></span>

<span data-ttu-id="51136-106">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="51136-106">Any one of the following:</span></span><ol><li><span data-ttu-id="51136-107">Atualize para o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="51136-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="51136-108">Instale o patch de manutenção mais recente para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="51136-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="51136-109">Evitar remover colunas até que a resposta assíncrona ao método <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> seja concluída.</span><span class="sxs-lookup"><span data-stu-id="51136-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="51136-110">Nome</span><span class="sxs-lookup"><span data-stu-id="51136-110">Name</span></span>    | <span data-ttu-id="51136-111">Valor</span><span class="sxs-lookup"><span data-stu-id="51136-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="51136-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="51136-112">Scope</span></span>   |<span data-ttu-id="51136-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="51136-113">Edge</span></span>|
|<span data-ttu-id="51136-114">Versão</span><span class="sxs-lookup"><span data-stu-id="51136-114">Version</span></span>|<span data-ttu-id="51136-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="51136-115">4.6.2</span></span>|
|<span data-ttu-id="51136-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="51136-116">Type</span></span>|<span data-ttu-id="51136-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="51136-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="51136-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="51136-118">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->
