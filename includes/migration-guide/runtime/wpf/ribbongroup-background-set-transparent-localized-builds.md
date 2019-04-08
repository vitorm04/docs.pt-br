---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760593"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="1fe2a-101">Tela de fundo RibbonGroup é definida como transparente em builds localizados</span><span class="sxs-lookup"><span data-stu-id="1fe2a-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1fe2a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1fe2a-102">Details</span></span>|<span data-ttu-id="1fe2a-103">A tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> em builds localizados sempre foi pintada com um pincel Transparente, o que resultava em uma experiência de interface do usuário ruim.</span><span class="sxs-lookup"><span data-stu-id="1fe2a-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="1fe2a-104">Isso foi corrigido no WPF do .NET Framework 4.7 por meio da atualização dos recursos localizados para <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, que, por sua vez, garante que o pincel correto seja selecionado.</span><span class="sxs-lookup"><span data-stu-id="1fe2a-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="1fe2a-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1fe2a-105">Suggestion</span></span>|<span data-ttu-id="1fe2a-106">Atualizar para o .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1fe2a-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="1fe2a-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="1fe2a-107">Scope</span></span>|<span data-ttu-id="1fe2a-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1fe2a-108">Edge</span></span>|
|<span data-ttu-id="1fe2a-109">Versão</span><span class="sxs-lookup"><span data-stu-id="1fe2a-109">Version</span></span>|<span data-ttu-id="1fe2a-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1fe2a-110">4.6.2</span></span>|
|<span data-ttu-id="1fe2a-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="1fe2a-111">Type</span></span>|<span data-ttu-id="1fe2a-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1fe2a-112">Runtime</span></span>|

