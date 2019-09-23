---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181835"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="8fa84-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="8fa84-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="8fa84-102">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8fa84-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8fa84-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="8fa84-103">Change description</span></span>

<span data-ttu-id="8fa84-104">No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle.</span><span class="sxs-lookup"><span data-stu-id="8fa84-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="8fa84-105">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.</span><span class="sxs-lookup"><span data-stu-id="8fa84-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="8fa84-106">No .NET Core, não `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="8fa84-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8fa84-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8fa84-107">Version introduced</span></span>

<span data-ttu-id="8fa84-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="8fa84-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8fa84-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8fa84-109">Recommended action</span></span>

<span data-ttu-id="8fa84-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="8fa84-110">Remove the switch.</span></span> <span data-ttu-id="8fa84-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="8fa84-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="8fa84-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="8fa84-112">Category</span></span>

<span data-ttu-id="8fa84-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fa84-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8fa84-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8fa84-114">Affected APIs</span></span>

- <span data-ttu-id="8fa84-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8fa84-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
