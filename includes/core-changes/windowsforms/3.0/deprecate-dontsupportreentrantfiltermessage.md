---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644001"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="ac2af-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="ac2af-101">Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="ac2af-102">O `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ac2af-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ac2af-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="ac2af-103">Change description</span></span>

<span data-ttu-id="ac2af-104">A partir do .NET Framework 4.6.1, a opção de compatibilidade de `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` resolve possíveis exceções de <xref:System.IndexOutOfRangeException> quando a mensagem de <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> é chamada com uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personalizada.</span><span class="sxs-lookup"><span data-stu-id="ac2af-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="ac2af-105">Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).</span><span class="sxs-lookup"><span data-stu-id="ac2af-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="ac2af-106">No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.</span><span class="sxs-lookup"><span data-stu-id="ac2af-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ac2af-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ac2af-107">Version introduced</span></span>

<span data-ttu-id="ac2af-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="ac2af-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ac2af-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ac2af-109">Recommended action</span></span>

<span data-ttu-id="ac2af-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="ac2af-110">Remove the switch.</span></span> <span data-ttu-id="ac2af-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="ac2af-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ac2af-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="ac2af-112">Category</span></span>

<span data-ttu-id="ac2af-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac2af-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ac2af-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ac2af-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
