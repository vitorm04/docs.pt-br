---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617517"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="4af19-101">HttpRuntime.AppDomainAppPath gera NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="4af19-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="4af19-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4af19-102">Details</span></span>

<span data-ttu-id="4af19-103">No .NET Framework 4.6.2, o runtime gera `T:System.NullReferenceException` ao recuperar um valor `P:System.Web.HttpRuntime.AppDomainAppPath` que inclui caracteres nulos. No .NET Framework 4.6.1 e versões anteriores, o runtime gera `T:System.ArgumentNullException`.</span><span class="sxs-lookup"><span data-stu-id="4af19-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4af19-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4af19-104">Suggestion</span></span>

<span data-ttu-id="4af19-105">Você pode fazer o seguinte para responder a essa alteração:</span><span class="sxs-lookup"><span data-stu-id="4af19-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="4af19-106">Identifique o `T:System.NullReferenceException` se o aplicativo estiver sendo executado no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="4af19-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="4af19-107">Atualize para o .NET Framework 4.7, que restaura o comportamento anterior e gera `T:System.ArgumentNullException`.</span><span class="sxs-lookup"><span data-stu-id="4af19-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="4af19-108">Name</span><span class="sxs-lookup"><span data-stu-id="4af19-108">Name</span></span>    | <span data-ttu-id="4af19-109">Valor</span><span class="sxs-lookup"><span data-stu-id="4af19-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4af19-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="4af19-110">Scope</span></span>   | <span data-ttu-id="4af19-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4af19-111">Edge</span></span>        |
| <span data-ttu-id="4af19-112">Versão</span><span class="sxs-lookup"><span data-stu-id="4af19-112">Version</span></span> | <span data-ttu-id="4af19-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4af19-113">4.6.2</span></span>       |
| <span data-ttu-id="4af19-114">Type</span><span class="sxs-lookup"><span data-stu-id="4af19-114">Type</span></span>    | <span data-ttu-id="4af19-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4af19-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4af19-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4af19-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
