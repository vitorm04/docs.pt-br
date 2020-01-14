---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937060"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="40868-101">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="40868-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="40868-102">A opção de compatibilidade `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no Windows Forms a partir do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="40868-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="40868-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="40868-103">Change description</span></span>

<span data-ttu-id="40868-104">No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle.</span><span class="sxs-lookup"><span data-stu-id="40868-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="40868-105">A opção de compatibilidade `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.</span><span class="sxs-lookup"><span data-stu-id="40868-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="40868-106">No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`.</span><span class="sxs-lookup"><span data-stu-id="40868-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40868-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="40868-107">Version introduced</span></span>

<span data-ttu-id="40868-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="40868-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40868-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="40868-109">Recommended action</span></span>

<span data-ttu-id="40868-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="40868-110">Remove the switch.</span></span> <span data-ttu-id="40868-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="40868-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="40868-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="40868-112">Category</span></span>

<span data-ttu-id="40868-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40868-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40868-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="40868-114">Affected APIs</span></span>

- <span data-ttu-id="40868-115">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="40868-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
