---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181751"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="37b53-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="37b53-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="37b53-102">A `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="37b53-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="37b53-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="37b53-103">Change description</span></span>

<span data-ttu-id="37b53-104">Começando com o .NET Framework 4.6.1, a `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade resolve <xref:System.IndexOutOfRangeException> as possíveis exceções <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> quando a mensagem é chamada com <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="37b53-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="37b53-105">Para obter mais informações, confira [Mitigação: Implementações](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)personalizadas de IMessageFilter. PreFilterMessage.</span><span class="sxs-lookup"><span data-stu-id="37b53-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="37b53-106">No .NET Core, não `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="37b53-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="37b53-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="37b53-107">Version introduced</span></span>

<span data-ttu-id="37b53-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="37b53-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="37b53-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="37b53-109">Recommended action</span></span>

<span data-ttu-id="37b53-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="37b53-110">Remove the switch.</span></span> <span data-ttu-id="37b53-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="37b53-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="37b53-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="37b53-112">Category</span></span>

<span data-ttu-id="37b53-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37b53-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="37b53-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="37b53-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
