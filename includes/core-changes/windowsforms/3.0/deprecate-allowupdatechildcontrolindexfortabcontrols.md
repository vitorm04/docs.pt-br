---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721436"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="d3c96-101">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="d3c96-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="d3c96-102">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d3c96-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d3c96-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d3c96-103">Change description</span></span>

<span data-ttu-id="d3c96-104">No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle.</span><span class="sxs-lookup"><span data-stu-id="d3c96-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="d3c96-105">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.</span><span class="sxs-lookup"><span data-stu-id="d3c96-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="d3c96-106">No .NET Core, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="d3c96-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3c96-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d3c96-107">Version introduced</span></span>

<span data-ttu-id="d3c96-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d3c96-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3c96-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d3c96-109">Recommended action</span></span>

<span data-ttu-id="d3c96-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="d3c96-110">Remove the switch.</span></span> <span data-ttu-id="d3c96-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="d3c96-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d3c96-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="d3c96-112">Category</span></span>

<span data-ttu-id="d3c96-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c96-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3c96-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d3c96-114">Affected APIs</span></span>

- <span data-ttu-id="d3c96-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d3c96-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
