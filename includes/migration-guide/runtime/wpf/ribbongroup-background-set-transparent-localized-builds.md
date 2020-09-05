---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496673"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="52ae6-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="52ae6-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="52ae6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="52ae6-102">Details</span></span>

<span data-ttu-id="52ae6-103">A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="52ae6-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="52ae6-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="52ae6-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="52ae6-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="52ae6-105">Suggestion</span></span>

<span data-ttu-id="52ae6-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="52ae6-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="52ae6-107">Nome</span><span class="sxs-lookup"><span data-stu-id="52ae6-107">Name</span></span>    | <span data-ttu-id="52ae6-108">Valor</span><span class="sxs-lookup"><span data-stu-id="52ae6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="52ae6-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="52ae6-109">Scope</span></span>   |<span data-ttu-id="52ae6-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="52ae6-110">Edge</span></span>|
|<span data-ttu-id="52ae6-111">Versão</span><span class="sxs-lookup"><span data-stu-id="52ae6-111">Version</span></span>|<span data-ttu-id="52ae6-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="52ae6-112">4.6.2</span></span>|
|<span data-ttu-id="52ae6-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="52ae6-113">Type</span></span>|<span data-ttu-id="52ae6-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="52ae6-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="52ae6-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="52ae6-115">Affected APIs</span></span>

<span data-ttu-id="52ae6-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="52ae6-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
