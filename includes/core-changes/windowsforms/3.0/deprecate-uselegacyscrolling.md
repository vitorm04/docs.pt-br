---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937024"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="6526c-101">DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado</span><span class="sxs-lookup"><span data-stu-id="6526c-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="6526c-102">O `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6526c-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6526c-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="6526c-103">Change description</span></span>

<span data-ttu-id="6526c-104">Começando com o .NET Framework 4.7.1, o `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch de compatibilidade <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> permitiu que os desenvolvedores optassem por desativar ações e independentes.</span><span class="sxs-lookup"><span data-stu-id="6526c-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="6526c-105">O switch restaurou o comportamento <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> legado, no qual o texto de contexto <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> é ignorado, e <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> o desenvolvedor é obrigado a usar a ação no controle antes da ação.</span><span class="sxs-lookup"><span data-stu-id="6526c-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="6526c-106">Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="6526c-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="6526c-107">No .NET Core, o `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="6526c-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6526c-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6526c-108">Version introduced</span></span>

<span data-ttu-id="6526c-109">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="6526c-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6526c-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6526c-110">Recommended action</span></span>

<span data-ttu-id="6526c-111">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="6526c-111">Remove the switch.</span></span> <span data-ttu-id="6526c-112">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="6526c-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6526c-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="6526c-113">Category</span></span>

<span data-ttu-id="6526c-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6526c-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6526c-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6526c-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
