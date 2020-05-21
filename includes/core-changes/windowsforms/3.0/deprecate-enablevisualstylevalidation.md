---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721064"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="5b79b-101">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="5b79b-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="5b79b-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`Não há suporte para a opção de compatibilidade em Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5b79b-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5b79b-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="5b79b-103">Change description</span></span>

<span data-ttu-id="5b79b-104">No .NET Framework, a `Switch.System.Windows.Forms.EnableVisualStyleValidation` opção de compatibilidade permitia que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico.</span><span class="sxs-lookup"><span data-stu-id="5b79b-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="5b79b-105">No .NET Core, `Switch.System.Windows.Forms.EnableVisualStyleValidation` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="5b79b-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5b79b-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5b79b-106">Version introduced</span></span>

<span data-ttu-id="5b79b-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="5b79b-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5b79b-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5b79b-108">Recommended action</span></span>

<span data-ttu-id="5b79b-109">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="5b79b-109">Remove the switch.</span></span> <span data-ttu-id="5b79b-110">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="5b79b-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="5b79b-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="5b79b-111">Category</span></span>

<span data-ttu-id="5b79b-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b79b-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5b79b-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5b79b-113">Affected APIs</span></span>

- <span data-ttu-id="5b79b-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5b79b-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
