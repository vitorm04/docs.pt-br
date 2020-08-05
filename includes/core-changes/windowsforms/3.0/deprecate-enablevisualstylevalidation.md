---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556119"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="952c3-101">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="952c3-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="952c3-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`Não há suporte para a opção de compatibilidade no Windows Forms no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="952c3-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="952c3-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="952c3-103">Change description</span></span>

<span data-ttu-id="952c3-104">No .NET Framework, a `Switch.System.Windows.Forms.EnableVisualStyleValidation` opção de compatibilidade permitia que um aplicativo recusasse a validação de estilos visuais fornecidos em um formato numérico.</span><span class="sxs-lookup"><span data-stu-id="952c3-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="952c3-105">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.EnableVisualStyleValidation` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="952c3-105">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="952c3-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="952c3-106">Version introduced</span></span>

<span data-ttu-id="952c3-107">3.0</span><span class="sxs-lookup"><span data-stu-id="952c3-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="952c3-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="952c3-108">Recommended action</span></span>

<span data-ttu-id="952c3-109">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="952c3-109">Remove the switch.</span></span> <span data-ttu-id="952c3-110">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="952c3-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="952c3-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="952c3-111">Category</span></span>

<span data-ttu-id="952c3-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="952c3-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="952c3-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="952c3-113">Affected APIs</span></span>

- <span data-ttu-id="952c3-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="952c3-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
