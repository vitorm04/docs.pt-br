---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619896"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="29579-101">Elementos DataTemplate do WPF agora são visíveis à UIA</span><span class="sxs-lookup"><span data-stu-id="29579-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="29579-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="29579-102">Details</span></span>

<span data-ttu-id="29579-103">Anteriormente, os elementos <xref:System.Windows.DataTemplate?displayProperty=fullName> eram invisíveis à Automação da Interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="29579-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="29579-104">A partir da versão 4.5, a Automação da Interface do Usuário detectar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="29579-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="29579-105">Isso é útil em muitos casos, mas pode arruinar os testes que dependem das árvores UIA que não contêm elementos <xref:System.Windows.DataTemplate?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="29579-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="29579-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="29579-106">Suggestion</span></span>

<span data-ttu-id="29579-107">Os testes de Automação da Interface do Usuário para esse aplicativo talvez precisem ser atualizados para contabilizar a árvore UIA agora, incluindo elementos <xref:System.Windows.DataTemplate?displayProperty=fullName> anteriormente invisíveis.</span><span class="sxs-lookup"><span data-stu-id="29579-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="29579-108">Por exemplo, os testes que esperam que alguns elementos fiquem próximos uns dos outros agora podem precisar esperar elementos UIA anteriormente invisíveis entre eles.</span><span class="sxs-lookup"><span data-stu-id="29579-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="29579-109">Ou os testes que dependem de determinadas contagens ou de índices para elementos UIA talvez precisem ser atualizados com novos valores.</span><span class="sxs-lookup"><span data-stu-id="29579-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="29579-110">Name</span><span class="sxs-lookup"><span data-stu-id="29579-110">Name</span></span>    | <span data-ttu-id="29579-111">Valor</span><span class="sxs-lookup"><span data-stu-id="29579-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="29579-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="29579-112">Scope</span></span>   |<span data-ttu-id="29579-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="29579-113">Edge</span></span>|
|<span data-ttu-id="29579-114">Versão</span><span class="sxs-lookup"><span data-stu-id="29579-114">Version</span></span>|<span data-ttu-id="29579-115">4.5</span><span class="sxs-lookup"><span data-stu-id="29579-115">4.5</span></span>|
|<span data-ttu-id="29579-116">Type</span><span class="sxs-lookup"><span data-stu-id="29579-116">Type</span></span>|<span data-ttu-id="29579-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="29579-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29579-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="29579-118">Affected APIs</span></span>

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
