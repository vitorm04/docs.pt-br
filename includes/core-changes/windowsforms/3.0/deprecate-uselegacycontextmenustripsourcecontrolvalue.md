---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556123"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="ee14e-101">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="ee14e-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="ee14e-102">A `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.2, não tem suporte no Windows Forms no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="ee14e-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ee14e-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="ee14e-103">Change description</span></span>

<span data-ttu-id="ee14e-104">A partir do .NET Framework 4.7.2, a `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade permite que o desenvolvedor cancele o novo comportamento da <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriedade, que agora retorna uma referência ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ee14e-104">Starting with .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="ee14e-105">O comportamento anterior da propriedade era retornar `null` .</span><span class="sxs-lookup"><span data-stu-id="ee14e-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="ee14e-106">Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="ee14e-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="ee14e-107">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="ee14e-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee14e-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ee14e-108">Version introduced</span></span>

<span data-ttu-id="ee14e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="ee14e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee14e-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ee14e-110">Recommended action</span></span>

<span data-ttu-id="ee14e-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="ee14e-111">Remove the switch.</span></span> <span data-ttu-id="ee14e-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="ee14e-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ee14e-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="ee14e-113">Category</span></span>

<span data-ttu-id="ee14e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee14e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee14e-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ee14e-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
