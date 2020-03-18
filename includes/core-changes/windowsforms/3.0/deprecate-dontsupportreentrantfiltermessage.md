---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937000"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="2509d-101">Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado</span><span class="sxs-lookup"><span data-stu-id="2509d-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="2509d-102">O `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2509d-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2509d-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="2509d-103">Change description</span></span>

<span data-ttu-id="2509d-104">Começando pelo .NET Framework `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 4.6.1, o <xref:System.IndexOutOfRangeException> switch de <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> compatibilidade resolve possíveis <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> exceções quando a mensagem é chamada com uma implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2509d-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="2509d-105">Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).</span><span class="sxs-lookup"><span data-stu-id="2509d-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="2509d-106">No .NET Core, o `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="2509d-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2509d-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2509d-107">Version introduced</span></span>

<span data-ttu-id="2509d-108">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="2509d-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2509d-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2509d-109">Recommended action</span></span>

<span data-ttu-id="2509d-110">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="2509d-110">Remove the switch.</span></span> <span data-ttu-id="2509d-111">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="2509d-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2509d-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="2509d-112">Category</span></span>

<span data-ttu-id="2509d-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2509d-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2509d-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2509d-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
