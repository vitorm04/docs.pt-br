---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556122"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="515f3-101">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="515f3-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="515f3-102">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade tem suporte no Windows Forms no .NET Framework 4,6 e em versões posteriores, mas não tem suporte no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="515f3-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="515f3-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="515f3-103">Change description</span></span>

<span data-ttu-id="515f3-104">No .NET Framework 4,6 e versões posteriores, a seleção de uma guia reordena sua coleção de controle.</span><span class="sxs-lookup"><span data-stu-id="515f3-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="515f3-105">A `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` opção de compatibilidade permite que um aplicativo ignore essa reordenação quando esse comportamento é indesejável.</span><span class="sxs-lookup"><span data-stu-id="515f3-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="515f3-106">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="515f3-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="515f3-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="515f3-107">Version introduced</span></span>

<span data-ttu-id="515f3-108">3.0</span><span class="sxs-lookup"><span data-stu-id="515f3-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="515f3-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="515f3-109">Recommended action</span></span>

<span data-ttu-id="515f3-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="515f3-110">Remove the switch.</span></span> <span data-ttu-id="515f3-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="515f3-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="515f3-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="515f3-112">Category</span></span>

<span data-ttu-id="515f3-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="515f3-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="515f3-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="515f3-114">Affected APIs</span></span>

- <span data-ttu-id="515f3-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="515f3-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
