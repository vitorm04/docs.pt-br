---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621024"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="718d2-101">Pop-ups encadeados com StaysOpen=False</span><span class="sxs-lookup"><span data-stu-id="718d2-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="718d2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="718d2-102">Details</span></span>

<span data-ttu-id="718d2-103">Um pop-up com StaysOpen=False deve fechar quando você clica fora dele.</span><span class="sxs-lookup"><span data-stu-id="718d2-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="718d2-104">Quando dois ou mais pop-ups do tipo estão encadeados (por exemplo, quando um contém o outro), há muitos problemas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="718d2-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="718d2-105">Abra dois níveis, clique fora do P2, mas dentro do P1.</span><span class="sxs-lookup"><span data-stu-id="718d2-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="718d2-106">Nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="718d2-106">Nothing happens.</span></span></li><li><span data-ttu-id="718d2-107">Abra dois níveis, clique fora do P1.</span><span class="sxs-lookup"><span data-stu-id="718d2-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="718d2-108">Ambos pop-ups serão fechados.</span><span class="sxs-lookup"><span data-stu-id="718d2-108">Both popups close.</span></span></li><li><span data-ttu-id="718d2-109">Abra e feche dois níveis.</span><span class="sxs-lookup"><span data-stu-id="718d2-109">Open and close two levels.</span></span>  <span data-ttu-id="718d2-110">Em seguida, tente abrir novamente o P2.</span><span class="sxs-lookup"><span data-stu-id="718d2-110">Then try to open P2 again.</span></span>  <span data-ttu-id="718d2-111">Nada acontecerá.</span><span class="sxs-lookup"><span data-stu-id="718d2-111">Nothing happens.</span></span></li><li><span data-ttu-id="718d2-112">Tente abrir três níveis.</span><span class="sxs-lookup"><span data-stu-id="718d2-112">Try to open three levels.</span></span>  <span data-ttu-id="718d2-113">Você não pode.</span><span class="sxs-lookup"><span data-stu-id="718d2-113">You can't.</span></span>  <span data-ttu-id="718d2-114">(Nada acontece ou os dois primeiros níveis fecham, dependendo de onde você clica.) Esses casos (e outras variantes) agora funcionam conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="718d2-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="718d2-115">Name</span><span class="sxs-lookup"><span data-stu-id="718d2-115">Name</span></span>    | <span data-ttu-id="718d2-116">Valor</span><span class="sxs-lookup"><span data-stu-id="718d2-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="718d2-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="718d2-117">Scope</span></span>   |<span data-ttu-id="718d2-118">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="718d2-118">Edge</span></span>|
|<span data-ttu-id="718d2-119">Versão</span><span class="sxs-lookup"><span data-stu-id="718d2-119">Version</span></span>|<span data-ttu-id="718d2-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="718d2-120">4.7.1</span></span>|
|<span data-ttu-id="718d2-121">Type</span><span class="sxs-lookup"><span data-stu-id="718d2-121">Type</span></span>|<span data-ttu-id="718d2-122">Runtime</span><span class="sxs-lookup"><span data-stu-id="718d2-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="718d2-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="718d2-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
