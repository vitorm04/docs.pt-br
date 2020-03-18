---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937060"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="7a878-101">AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="7a878-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="7a878-102">O `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch de compatibilidade é suportado no Windows Forms em versões .NET Framework 4.6 e posteriores, mas não é suportado no Windows Forms a partir do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7a878-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7a878-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="7a878-103">Change description</span></span>

<span data-ttu-id="7a878-104">Nas versões .NET Framework 4.6 e posteriores, selecionando uma guia reordena sua coleção de controles.</span><span class="sxs-lookup"><span data-stu-id="7a878-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="7a878-105">O `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch de compatibilidade permite que um aplicativo pule esse reordenamento quando esse comportamento é indesejável.</span><span class="sxs-lookup"><span data-stu-id="7a878-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="7a878-106">No .NET Core, o `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="7a878-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a878-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="7a878-107">Version introduced</span></span>

<span data-ttu-id="7a878-108">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="7a878-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a878-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="7a878-109">Recommended action</span></span>

<span data-ttu-id="7a878-110">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="7a878-110">Remove the switch.</span></span> <span data-ttu-id="7a878-111">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="7a878-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="7a878-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="7a878-112">Category</span></span>

<span data-ttu-id="7a878-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a878-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a878-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7a878-114">Affected APIs</span></span>

- <span data-ttu-id="7a878-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7a878-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
