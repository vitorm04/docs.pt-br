---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937062"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="cb1f0-101">Ativaro switch de compatibilidade DoVisualStyleValidation não suportado</span><span class="sxs-lookup"><span data-stu-id="cb1f0-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="cb1f0-102">O `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch de compatibilidade não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="cb1f0-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cb1f0-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="cb1f0-103">Change description</span></span>

<span data-ttu-id="cb1f0-104">No .NET Framework, o `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch de compatibilidade permitiu que um aplicativo optasse por não validar os estilos visuais fornecidos de forma numérica.</span><span class="sxs-lookup"><span data-stu-id="cb1f0-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="cb1f0-105">No .NET Core, o `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="cb1f0-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cb1f0-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="cb1f0-106">Version introduced</span></span>

<span data-ttu-id="cb1f0-107">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="cb1f0-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cb1f0-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="cb1f0-108">Recommended action</span></span>

<span data-ttu-id="cb1f0-109">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="cb1f0-109">Remove the switch.</span></span> <span data-ttu-id="cb1f0-110">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="cb1f0-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="cb1f0-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="cb1f0-111">Category</span></span>

<span data-ttu-id="cb1f0-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb1f0-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cb1f0-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cb1f0-113">Affected APIs</span></span>

- <span data-ttu-id="cb1f0-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cb1f0-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
