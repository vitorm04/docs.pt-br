---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721177"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="1b78d-101">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="1b78d-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="1b78d-102">A `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.2, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="1b78d-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b78d-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1b78d-103">Change description</span></span>

<span data-ttu-id="1b78d-104">Começando com o .NET Framework 4.7.2, a `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade permite que o desenvolvedor cancele o novo comportamento da <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriedade, que agora retorna uma referência ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="1b78d-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="1b78d-105">O comportamento anterior da propriedade era retornar `null` .</span><span class="sxs-lookup"><span data-stu-id="1b78d-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="1b78d-106">Para obter mais informações, consulte [ \< AppContextSwitchOverrides> Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="1b78d-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="1b78d-107">No .NET Core, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="1b78d-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b78d-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1b78d-108">Version introduced</span></span>

<span data-ttu-id="1b78d-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="1b78d-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b78d-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1b78d-110">Recommended action</span></span>

<span data-ttu-id="1b78d-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="1b78d-111">Remove the switch.</span></span> <span data-ttu-id="1b78d-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="1b78d-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1b78d-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="1b78d-113">Category</span></span>

<span data-ttu-id="1b78d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b78d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b78d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1b78d-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
