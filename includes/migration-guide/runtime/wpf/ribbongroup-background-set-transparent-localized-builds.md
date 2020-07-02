---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622336"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="8fc7a-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="8fc7a-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="8fc7a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8fc7a-102">Details</span></span>

<span data-ttu-id="8fc7a-103">A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="8fc7a-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="8fc7a-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="8fc7a-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8fc7a-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8fc7a-105">Suggestion</span></span>

<span data-ttu-id="8fc7a-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="8fc7a-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="8fc7a-107">Name</span><span class="sxs-lookup"><span data-stu-id="8fc7a-107">Name</span></span>    | <span data-ttu-id="8fc7a-108">Valor</span><span class="sxs-lookup"><span data-stu-id="8fc7a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8fc7a-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="8fc7a-109">Scope</span></span>   |<span data-ttu-id="8fc7a-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8fc7a-110">Edge</span></span>|
|<span data-ttu-id="8fc7a-111">Versão</span><span class="sxs-lookup"><span data-stu-id="8fc7a-111">Version</span></span>|<span data-ttu-id="8fc7a-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8fc7a-112">4.6.2</span></span>|
|<span data-ttu-id="8fc7a-113">Type</span><span class="sxs-lookup"><span data-stu-id="8fc7a-113">Type</span></span>|<span data-ttu-id="8fc7a-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="8fc7a-114">Runtime</span></span>|
