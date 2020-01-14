---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936994"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="2b784-101">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="2b784-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="2b784-102">O `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` opção de compatibilidade, que foi introduzido no .NET Framework 4.7.2, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2b784-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2b784-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="2b784-103">Change description</span></span>

<span data-ttu-id="2b784-104">A partir do .NET Framework 4.7.2, a opção de compatibilidade `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` permite que o desenvolvedor recuse o novo comportamento da propriedade <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, que agora retorna uma referência ao controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2b784-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="2b784-105">O comportamento anterior da propriedade era retornar `null`.</span><span class="sxs-lookup"><span data-stu-id="2b784-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="2b784-106">Para obter mais informações, consulte [\<elemento > AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="2b784-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="2b784-107">No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.</span><span class="sxs-lookup"><span data-stu-id="2b784-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b784-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2b784-108">Version introduced</span></span>

<span data-ttu-id="2b784-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="2b784-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b784-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2b784-110">Recommended action</span></span>

<span data-ttu-id="2b784-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="2b784-111">Remove the switch.</span></span> <span data-ttu-id="2b784-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="2b784-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2b784-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="2b784-113">Category</span></span>

<span data-ttu-id="2b784-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2b784-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b784-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2b784-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
