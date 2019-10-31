---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802544"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="8f13b-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="8f13b-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8f13b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8f13b-102">Details</span></span>|<span data-ttu-id="8f13b-103">A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="8f13b-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="8f13b-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="8f13b-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="8f13b-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8f13b-105">Suggestion</span></span>|<span data-ttu-id="8f13b-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="8f13b-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="8f13b-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="8f13b-107">Scope</span></span>|<span data-ttu-id="8f13b-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8f13b-108">Edge</span></span>|
|<span data-ttu-id="8f13b-109">Versão</span><span class="sxs-lookup"><span data-stu-id="8f13b-109">Version</span></span>|<span data-ttu-id="8f13b-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8f13b-110">4.6.2</span></span>|
|<span data-ttu-id="8f13b-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="8f13b-111">Type</span></span>|<span data-ttu-id="8f13b-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8f13b-112">Runtime</span></span>|

