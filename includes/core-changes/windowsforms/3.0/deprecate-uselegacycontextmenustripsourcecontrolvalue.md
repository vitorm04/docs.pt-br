---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936994"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="b6ff2-101">UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado</span><span class="sxs-lookup"><span data-stu-id="b6ff2-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="b6ff2-102">O `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.2, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b6ff2-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="b6ff2-103">Change description</span></span>

<span data-ttu-id="b6ff2-104">Começando pelo .NET Framework 4.7.2, o `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch de compatibilidade permite que <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> o desenvolvedor opte por sair do novo comportamento da propriedade, que agora retorna uma referência ao controle de origem.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="b6ff2-105">O comportamento anterior da propriedade `null`era retornar.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="b6ff2-106">Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="b6ff2-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="b6ff2-107">No .NET Core, o `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b6ff2-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b6ff2-108">Version introduced</span></span>

<span data-ttu-id="b6ff2-109">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="b6ff2-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b6ff2-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b6ff2-110">Recommended action</span></span>

<span data-ttu-id="b6ff2-111">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-111">Remove the switch.</span></span> <span data-ttu-id="b6ff2-112">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="b6ff2-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="b6ff2-113">Category</span></span>

<span data-ttu-id="b6ff2-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6ff2-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b6ff2-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b6ff2-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
