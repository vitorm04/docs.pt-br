---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496109"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="8d1fb-101">O padrão da Caixa de Texto do WPF é o limite de 100 na ação desfazer</span><span class="sxs-lookup"><span data-stu-id="8d1fb-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="8d1fb-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8d1fb-102">Details</span></span>

<span data-ttu-id="8d1fb-103">No .NET Framework 4.5, o limite padrão de desfazer para uma caixa de texto do WPF é 100 (em vez de ser ilimitado como no .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="8d1fb-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8d1fb-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8d1fb-104">Suggestion</span></span>

<span data-ttu-id="8d1fb-105">Se um limite de 100 da ação desfazer for muito baixo, o limite poderá ser definido explicitamente com <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>.</span><span class="sxs-lookup"><span data-stu-id="8d1fb-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="8d1fb-106">Nome</span><span class="sxs-lookup"><span data-stu-id="8d1fb-106">Name</span></span>    | <span data-ttu-id="8d1fb-107">Valor</span><span class="sxs-lookup"><span data-stu-id="8d1fb-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8d1fb-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="8d1fb-108">Scope</span></span>   |<span data-ttu-id="8d1fb-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8d1fb-109">Edge</span></span>|
|<span data-ttu-id="8d1fb-110">Versão</span><span class="sxs-lookup"><span data-stu-id="8d1fb-110">Version</span></span>|<span data-ttu-id="8d1fb-111">4.5</span><span class="sxs-lookup"><span data-stu-id="8d1fb-111">4.5</span></span>|
|<span data-ttu-id="8d1fb-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d1fb-112">Type</span></span>|<span data-ttu-id="8d1fb-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="8d1fb-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8d1fb-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8d1fb-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
