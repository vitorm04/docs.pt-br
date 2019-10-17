---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394285"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="9b30f-101">Autenticação: assinatura OAuthHandler ExchangeCodeAsync alterada</span><span class="sxs-lookup"><span data-stu-id="9b30f-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="9b30f-102">No ASP.NET Core 3,0, a assinatura de `OAuthHandler.ExchangeCodeAsync` foi alterada de:</span><span class="sxs-lookup"><span data-stu-id="9b30f-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="9b30f-103">Para:</span><span class="sxs-lookup"><span data-stu-id="9b30f-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="9b30f-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9b30f-104">Version introduced</span></span>

<span data-ttu-id="9b30f-105">3.0</span><span class="sxs-lookup"><span data-stu-id="9b30f-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9b30f-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="9b30f-106">Old behavior</span></span>

<span data-ttu-id="9b30f-107">As cadeias de caracteres `code` e `redirectUri` foram passadas como argumentos separados.</span><span class="sxs-lookup"><span data-stu-id="9b30f-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9b30f-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="9b30f-108">New behavior</span></span>

<span data-ttu-id="9b30f-109">`Code` e `RedirectUri` são propriedades em `OAuthCodeExchangeContext` que podem ser definidas por meio do Construtor `OAuthCodeExchangeContext`.</span><span class="sxs-lookup"><span data-stu-id="9b30f-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="9b30f-110">O novo tipo `OAuthCodeExchangeContext` é o único argumento passado para `OAuthHandler.ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="9b30f-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9b30f-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="9b30f-111">Reason for change</span></span>

<span data-ttu-id="9b30f-112">Essa alteração permite que parâmetros adicionais sejam fornecidos de forma não-significativa.</span><span class="sxs-lookup"><span data-stu-id="9b30f-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="9b30f-113">Não há necessidade de criar novas sobrecargas `ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="9b30f-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b30f-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="9b30f-114">Recommended action</span></span>

<span data-ttu-id="9b30f-115">Construa um `OAuthCodeExchangeContext` com os valores de `code` e `redirectUri` apropriados.</span><span class="sxs-lookup"><span data-stu-id="9b30f-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="9b30f-116">Uma instância <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="9b30f-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="9b30f-117">Essa instância única `OAuthCodeExchangeContext` pode ser passada para `OAuthHandler.ExchangeCodeAsync` em vez de vários argumentos.</span><span class="sxs-lookup"><span data-stu-id="9b30f-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="9b30f-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="9b30f-118">Category</span></span>

<span data-ttu-id="9b30f-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9b30f-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b30f-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9b30f-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
