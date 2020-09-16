---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557953"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="024da-101">MulticastOption. Group não aceita um valor nulo</span><span class="sxs-lookup"><span data-stu-id="024da-101">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="024da-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Não aceita mais um valor de `null` .</span><span class="sxs-lookup"><span data-stu-id="024da-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="024da-103">Se você definir a propriedade como `null` , um <xref:System.ArgumentNullException> será gerado.</span><span class="sxs-lookup"><span data-stu-id="024da-103">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="024da-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="024da-104">Version introduced</span></span>

<span data-ttu-id="024da-105">5,0</span><span class="sxs-lookup"><span data-stu-id="024da-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="024da-106">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="024da-106">Change description</span></span>

<span data-ttu-id="024da-107">Nas versões anteriores do .NET, você pode definir a <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> propriedade como `null` .</span><span class="sxs-lookup"><span data-stu-id="024da-107">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="024da-108">Se o <xref:System.Net.Sockets.MulticastOption> for passado posteriormente para <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , o tempo de execução lançará um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="024da-108">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="024da-109">No .NET 5,0 e posterior, um <xref:System.ArgumentNullException> será gerado se você definir a propriedade como `null` .</span><span class="sxs-lookup"><span data-stu-id="024da-109">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="024da-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="024da-110">Reason for change</span></span>

<span data-ttu-id="024da-111">Para ser consistente com as diretrizes de design de estrutura, a propriedade foi atualizada para lançar um <xref:System.ArgumentNullException> se o valor for `null` .</span><span class="sxs-lookup"><span data-stu-id="024da-111">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="024da-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="024da-112">Recommended action</span></span>

<span data-ttu-id="024da-113">Certifique-se de que você não definiu <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> como `null` .</span><span class="sxs-lookup"><span data-stu-id="024da-113">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="024da-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="024da-114">Category</span></span>

<span data-ttu-id="024da-115">Rede</span><span class="sxs-lookup"><span data-stu-id="024da-115">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="024da-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="024da-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
