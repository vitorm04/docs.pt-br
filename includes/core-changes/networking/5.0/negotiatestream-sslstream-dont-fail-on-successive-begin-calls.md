---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050502"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="724b5-101">NegotiateStream e SslStream permitem operações de início sucessivas</span><span class="sxs-lookup"><span data-stu-id="724b5-101">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="724b5-102">Casos de erro em fluxos de segurança são tratados de forma diferente e chamadas sucessivas para `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` podem não falhar mais.</span><span class="sxs-lookup"><span data-stu-id="724b5-102">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="724b5-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="724b5-103">Version introduced</span></span>

<span data-ttu-id="724b5-104">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="724b5-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="724b5-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="724b5-105">Change description</span></span>

<span data-ttu-id="724b5-106">Nas versões anteriores do .NET, chamando `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` sucessivamente sem primeiro chamar `EndAuthenticateAsServer` ou `EndAuthenticateAsClient` resultar em um <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="724b5-106">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="724b5-107">A partir do .NET 5,0, as chamadas sucessivas `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` não resultam mais em um <xref:System.NotSupportedException> , pois essas APIs são apoiadas por uma <xref:System.Threading.Tasks.Task> implementação baseada em.</span><span class="sxs-lookup"><span data-stu-id="724b5-107">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="724b5-108">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="724b5-108">Reason for change</span></span>

<span data-ttu-id="724b5-109">Alternar a implementação interna do modelo de programação assíncrona (APM) para <xref:System.Threading.Tasks.Task> com base melhora o desempenho e diminui a complexidade do código.</span><span class="sxs-lookup"><span data-stu-id="724b5-109">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="724b5-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="724b5-110">Recommended action</span></span>

<span data-ttu-id="724b5-111">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="724b5-111">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="724b5-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="724b5-112">Category</span></span>

<span data-ttu-id="724b5-113">Rede</span><span class="sxs-lookup"><span data-stu-id="724b5-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="724b5-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="724b5-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
