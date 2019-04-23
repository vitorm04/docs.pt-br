---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235990"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="e7e69-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="e7e69-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e7e69-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e7e69-102">Details</span></span>|<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> <span data-ttu-id="e7e69-103">A tela de fundo em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="e7e69-103">background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="e7e69-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="e7e69-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="e7e69-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e7e69-105">Suggestion</span></span>|<span data-ttu-id="e7e69-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e7e69-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="e7e69-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="e7e69-107">Scope</span></span>|<span data-ttu-id="e7e69-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e7e69-108">Edge</span></span>|
|<span data-ttu-id="e7e69-109">Versão</span><span class="sxs-lookup"><span data-stu-id="e7e69-109">Version</span></span>|<span data-ttu-id="e7e69-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e7e69-110">4.6.2</span></span>|
|<span data-ttu-id="e7e69-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="e7e69-111">Type</span></span>|<span data-ttu-id="e7e69-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e7e69-112">Runtime</span></span>|
