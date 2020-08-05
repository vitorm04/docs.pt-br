---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556125"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="61fef-101">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="61fef-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="61fef-102">A `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core e no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="61fef-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="61fef-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="61fef-103">Change description</span></span>

<span data-ttu-id="61fef-104">Começando com o .NET Framework 4.6.1, a `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` opção de compatibilidade resolve as possíveis <xref:System.IndexOutOfRangeException> exceções quando a <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> mensagem é chamada com uma <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementação personalizada.</span><span class="sxs-lookup"><span data-stu-id="61fef-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="61fef-105">Para saber mais, confira [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md) (Mitigação: implementações personalizadas de IMessageFilter.PreFilterMessage).</span><span class="sxs-lookup"><span data-stu-id="61fef-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="61fef-106">No .NET Core e no .NET 5,0 e posterior, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="61fef-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="61fef-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="61fef-107">Version introduced</span></span>

<span data-ttu-id="61fef-108">3.0</span><span class="sxs-lookup"><span data-stu-id="61fef-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="61fef-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="61fef-109">Recommended action</span></span>

<span data-ttu-id="61fef-110">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="61fef-110">Remove the switch.</span></span> <span data-ttu-id="61fef-111">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="61fef-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="61fef-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="61fef-112">Category</span></span>

<span data-ttu-id="61fef-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="61fef-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="61fef-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="61fef-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
