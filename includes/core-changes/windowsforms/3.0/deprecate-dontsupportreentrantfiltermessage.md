---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721144"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="d9590-101">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="d9590-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="d9590-102">A `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d9590-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d9590-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d9590-103">Change description</span></span>

<span data-ttu-id="d9590-104">Começando com o .NET Framework 4.6.1, a `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade resolve as possíveis <xref:System.IndexOutOfRangeException> exceções quando a <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> mensagem é chamada com uma <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d9590-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d9590-105">Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).</span><span class="sxs-lookup"><span data-stu-id="d9590-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="d9590-106">No .NET Core, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="d9590-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d9590-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d9590-107">Version introduced</span></span>

<span data-ttu-id="d9590-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d9590-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d9590-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d9590-109">Recommended action</span></span>

<span data-ttu-id="d9590-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="d9590-110">Remove the switch.</span></span> <span data-ttu-id="d9590-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="d9590-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d9590-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="d9590-112">Category</span></span>

<span data-ttu-id="d9590-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9590-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d9590-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d9590-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
