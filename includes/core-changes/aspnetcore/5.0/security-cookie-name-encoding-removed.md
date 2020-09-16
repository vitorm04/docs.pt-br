---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401972"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="65396-101">Segurança: codificação de nome de cookie removida</span><span class="sxs-lookup"><span data-stu-id="65396-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="65396-102">O [padrão de cookie http](https://tools.ietf.org/html/rfc6265#section-4.1.1) permite apenas caracteres específicos em valores e nomes de cookie.</span><span class="sxs-lookup"><span data-stu-id="65396-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="65396-103">Para dar suporte a caracteres não permitidos, ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="65396-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="65396-104">Codifica ao criar um cookie de resposta.</span><span class="sxs-lookup"><span data-stu-id="65396-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="65396-105">Decodifica ao ler um cookie de solicitação.</span><span class="sxs-lookup"><span data-stu-id="65396-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="65396-106">No ASP.NET Core 5,0, esse comportamento de codificação mudou em resposta a uma preocupação de segurança.</span><span class="sxs-lookup"><span data-stu-id="65396-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="65396-107">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).</span><span class="sxs-lookup"><span data-stu-id="65396-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="65396-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="65396-108">Version introduced</span></span>

<span data-ttu-id="65396-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="65396-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="65396-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="65396-110">Old behavior</span></span>

<span data-ttu-id="65396-111">Os nomes de cookies de resposta são codificados.</span><span class="sxs-lookup"><span data-stu-id="65396-111">Response cookie names are encoded.</span></span> <span data-ttu-id="65396-112">Os nomes de cookie de solicitação são decodificados.</span><span class="sxs-lookup"><span data-stu-id="65396-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="65396-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="65396-113">New behavior</span></span>

<span data-ttu-id="65396-114">A codificação e a decodificação de nomes de cookies foram removidas.</span><span class="sxs-lookup"><span data-stu-id="65396-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="65396-115">Para [versões anteriores com suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) do ASP.NET Core, a equipe planeja reduzir o problema de decodificação in-loco.</span><span class="sxs-lookup"><span data-stu-id="65396-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="65396-116">Além disso, chamar <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> com um nome de cookie inválido gera uma exceção do tipo <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="65396-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="65396-117">A codificação e a decodificação de valores de cookies permanecem inalteradas.</span><span class="sxs-lookup"><span data-stu-id="65396-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="65396-118">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="65396-118">Reason for change</span></span>

<span data-ttu-id="65396-119">Foi descoberto um problema em [várias estruturas da Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span><span class="sxs-lookup"><span data-stu-id="65396-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="65396-120">A codificação e a decodificação podem permitir que um invasor ignore um recurso de segurança chamado [prefixos de cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) , falsificando prefixos reservados como `__Host-` com valores codificados como `__%48ost-` .</span><span class="sxs-lookup"><span data-stu-id="65396-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="65396-121">O ataque requer uma exploração secundária para injetar os cookies falsificados, como uma vulnerabilidade de XSS (script entre sites), no site.</span><span class="sxs-lookup"><span data-stu-id="65396-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="65396-122">Esses prefixos não são usados por padrão em ASP.NET Core ou `Microsoft.Owin` bibliotecas ou modelos.</span><span class="sxs-lookup"><span data-stu-id="65396-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="65396-123">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="65396-123">Recommended action</span></span>

<span data-ttu-id="65396-124">Se você estiver movendo projetos para ASP.NET Core 5,0 ou posterior, verifique se seus nomes de cookie estão em conformidade com os [requisitos de especificação de token](https://tools.ietf.org/html/rfc2616#section-2.2): caracteres ASCII, excluindo controles e separadores `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` .</span><span class="sxs-lookup"><span data-stu-id="65396-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="65396-125">O uso de caracteres não ASCII em nomes de cookies ou outros cabeçalhos HTTP pode causar uma exceção do servidor ou ser de ida e volta inadequada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="65396-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="65396-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="65396-126">Category</span></span>

<span data-ttu-id="65396-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="65396-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="65396-128">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="65396-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
