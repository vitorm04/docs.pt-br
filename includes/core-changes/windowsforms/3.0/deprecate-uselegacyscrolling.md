---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720960"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="8aa08-101">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="8aa08-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="8aa08-102">A `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8aa08-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8aa08-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="8aa08-103">Change description</span></span>

<span data-ttu-id="8aa08-104">Começando com o .NET Framework 4.7.1, a `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade permitia que os desenvolvedores desautorizassem as <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ações e independentes <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8aa08-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="8aa08-105">A opção restaurou o comportamento herdado, no qual <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> será ignorada se o texto do contexto estiver presente e o desenvolvedor for solicitado a usar a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ação no controle antes da <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ação.</span><span class="sxs-lookup"><span data-stu-id="8aa08-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="8aa08-106">Para obter mais informações, consulte [ \< AppContextSwitchOverrides> Element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="8aa08-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="8aa08-107">No .NET Core, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="8aa08-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8aa08-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8aa08-108">Version introduced</span></span>

<span data-ttu-id="8aa08-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="8aa08-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8aa08-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8aa08-110">Recommended action</span></span>

<span data-ttu-id="8aa08-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="8aa08-111">Remove the switch.</span></span> <span data-ttu-id="8aa08-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="8aa08-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="8aa08-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="8aa08-113">Category</span></span>

<span data-ttu-id="8aa08-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8aa08-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8aa08-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8aa08-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
