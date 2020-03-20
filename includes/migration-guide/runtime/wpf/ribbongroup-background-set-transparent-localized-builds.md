---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802544"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="6b705-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="6b705-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6b705-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6b705-102">Details</span></span>|<span data-ttu-id="6b705-103">A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="6b705-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="6b705-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="6b705-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="6b705-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6b705-105">Suggestion</span></span>|<span data-ttu-id="6b705-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="6b705-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="6b705-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="6b705-107">Scope</span></span>|<span data-ttu-id="6b705-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6b705-108">Edge</span></span>|
|<span data-ttu-id="6b705-109">Versão</span><span class="sxs-lookup"><span data-stu-id="6b705-109">Version</span></span>|<span data-ttu-id="6b705-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6b705-110">4.6.2</span></span>|
|<span data-ttu-id="6b705-111">Type</span><span class="sxs-lookup"><span data-stu-id="6b705-111">Type</span></span>|<span data-ttu-id="6b705-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="6b705-112">Runtime</span></span>|
