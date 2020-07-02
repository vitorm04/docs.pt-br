---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619899"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="265ad-101">O padrão da Caixa de Texto do WPF é o limite de 100 na ação desfazer</span><span class="sxs-lookup"><span data-stu-id="265ad-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="265ad-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="265ad-102">Details</span></span>

<span data-ttu-id="265ad-103">No .NET Framework 4.5, o limite padrão de desfazer para uma caixa de texto do WPF é 100 (em vez de ser ilimitado como no .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="265ad-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="265ad-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="265ad-104">Suggestion</span></span>

<span data-ttu-id="265ad-105">Se um limite de 100 da ação desfazer for muito baixo, o limite poderá ser definido explicitamente com <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>.</span><span class="sxs-lookup"><span data-stu-id="265ad-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="265ad-106">Name</span><span class="sxs-lookup"><span data-stu-id="265ad-106">Name</span></span>    | <span data-ttu-id="265ad-107">Valor</span><span class="sxs-lookup"><span data-stu-id="265ad-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="265ad-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="265ad-108">Scope</span></span>   |<span data-ttu-id="265ad-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="265ad-109">Edge</span></span>|
|<span data-ttu-id="265ad-110">Versão</span><span class="sxs-lookup"><span data-stu-id="265ad-110">Version</span></span>|<span data-ttu-id="265ad-111">4.5</span><span class="sxs-lookup"><span data-stu-id="265ad-111">4.5</span></span>|
|<span data-ttu-id="265ad-112">Type</span><span class="sxs-lookup"><span data-stu-id="265ad-112">Type</span></span>|<span data-ttu-id="265ad-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="265ad-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="265ad-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="265ad-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
