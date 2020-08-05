---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556124"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="1f4a1-101">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="1f4a1-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="1f4a1-102">A `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1f4a1-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1f4a1-103">Change description</span></span>

<span data-ttu-id="1f4a1-104">A partir do .NET Framework 4.7.1, a `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` opção de compatibilidade permitia que os desenvolvedores desaceitem <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ações e independentes <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1f4a1-104">Starting with .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="1f4a1-105">A opção restaurou o comportamento herdado, no qual <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> será ignorada se o texto do contexto estiver presente e o desenvolvedor for solicitado a usar a <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> ação no controle antes da <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ação.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="1f4a1-106">Para obter mais informações, consulte [ \<AppContextSwitchOverrides> elemento](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="1f4a1-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="1f4a1-107">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f4a1-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1f4a1-108">Version introduced</span></span>

<span data-ttu-id="1f4a1-109">3.0</span><span class="sxs-lookup"><span data-stu-id="1f4a1-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f4a1-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1f4a1-110">Recommended action</span></span>

<span data-ttu-id="1f4a1-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-111">Remove the switch.</span></span> <span data-ttu-id="1f4a1-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="1f4a1-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="1f4a1-113">Category</span></span>

<span data-ttu-id="1f4a1-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f4a1-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f4a1-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1f4a1-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
