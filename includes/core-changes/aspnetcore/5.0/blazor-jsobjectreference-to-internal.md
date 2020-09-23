---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077586"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="d4148-101">Mais de: JSObjectReference e tipos JSInProcessObjectReference alterados para interno</span><span class="sxs-lookup"><span data-stu-id="d4148-101">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="d4148-102">Os novos `Microsoft.JSInterop.JSObjectReference` e os `Microsoft.JSInterop.JSInProcessObjectReference` tipos introduzidos no ASP.NET Core 5,0 RC1 foram marcados como `internal` .</span><span class="sxs-lookup"><span data-stu-id="d4148-102">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d4148-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d4148-103">Version introduced</span></span>

<span data-ttu-id="d4148-104">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="d4148-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d4148-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="d4148-105">Old behavior</span></span>

<span data-ttu-id="d4148-106">Um `JSObjectReference` pode ser obtido de uma chamada de interoperabilidade JavaScript por meio do `IJSRuntime` .</span><span class="sxs-lookup"><span data-stu-id="d4148-106">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="d4148-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4148-107">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a><span data-ttu-id="d4148-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="d4148-108">New behavior</span></span>

<span data-ttu-id="d4148-109">`JSObjectReference` usa o modificador de acesso [interno](../../../../docs/csharp/language-reference/keywords/internal.md) .</span><span class="sxs-lookup"><span data-stu-id="d4148-109">`JSObjectReference` uses the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="d4148-110">A `public` `IJSObjectReference` interface deve ser usada em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="d4148-110">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="d4148-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4148-111">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="d4148-112">`JSInProcessObjectReference` também foi marcado como `internal` e foi substituído por `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="d4148-112">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d4148-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="d4148-113">Reason for change</span></span>

<span data-ttu-id="d4148-114">A alteração torna o recurso de interoperabilidade JavaScript mais consistente com outros padrões no mais baixo.</span><span class="sxs-lookup"><span data-stu-id="d4148-114">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="d4148-115">`IJSObjectReference` é análogo a `IJSRuntime` , pois ele atende a uma finalidade semelhante e tem métodos e extensões semelhantes.</span><span class="sxs-lookup"><span data-stu-id="d4148-115">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d4148-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d4148-116">Recommended action</span></span>

<span data-ttu-id="d4148-117">Substituir ocorrências de `JSObjectReference` e `JSInProcessObjectReference` por `IJSObjectReference` e `IJSInProcessObjectReference` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d4148-117">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

#### <a name="category"></a><span data-ttu-id="d4148-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="d4148-118">Category</span></span>

<span data-ttu-id="d4148-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d4148-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d4148-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d4148-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
