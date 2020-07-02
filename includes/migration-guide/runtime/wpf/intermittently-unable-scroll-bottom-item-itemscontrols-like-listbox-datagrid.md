---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621918"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="b5952-101">Não é possível rolar intermitentemente para o item na parte inferior em ItemsControls (como ListBox e DataGrid) ao usar DataTemplates personalizados</span><span class="sxs-lookup"><span data-stu-id="b5952-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="b5952-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b5952-102">Details</span></span>

<span data-ttu-id="b5952-103">Em alguns casos, um bug no .NET Framework 4.5 está fazendo com que ItemsControls (como <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> etc.) não rolem para o item na parte inferior ao usar DataTemplates personalizados.</span><span class="sxs-lookup"><span data-stu-id="b5952-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="b5952-104">Se houver uma tentativa de rolagem pela segunda vez (depois da rolagem de volta), ela funcionará.</span><span class="sxs-lookup"><span data-stu-id="b5952-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b5952-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b5952-105">Suggestion</span></span>

<span data-ttu-id="b5952-106">Esse problema foi corrigido no .NET Framework 4.5.2 e pode ser solucionado com o upgrade para essa versão (ou uma versão posterior) do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5952-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="b5952-107">Como alternativa, os usuários ainda podem arrastar as barras de rolagem para os itens finais nessas coleções, mas pode ser necessário tentar duas vezes para obter êxito.</span><span class="sxs-lookup"><span data-stu-id="b5952-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="b5952-108">Name</span><span class="sxs-lookup"><span data-stu-id="b5952-108">Name</span></span>    | <span data-ttu-id="b5952-109">Valor</span><span class="sxs-lookup"><span data-stu-id="b5952-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b5952-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="b5952-110">Scope</span></span>   |<span data-ttu-id="b5952-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="b5952-111">Minor</span></span>|
|<span data-ttu-id="b5952-112">Versão</span><span class="sxs-lookup"><span data-stu-id="b5952-112">Version</span></span>|<span data-ttu-id="b5952-113">4.5</span><span class="sxs-lookup"><span data-stu-id="b5952-113">4.5</span></span>|
|<span data-ttu-id="b5952-114">Type</span><span class="sxs-lookup"><span data-stu-id="b5952-114">Type</span></span>|<span data-ttu-id="b5952-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b5952-115">Runtime</span></span>|
