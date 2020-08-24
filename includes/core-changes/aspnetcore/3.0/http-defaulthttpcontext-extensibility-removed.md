---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290738"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="b84ea-101">HTTP: extensibilidade defaulthttpcontext removida</span><span class="sxs-lookup"><span data-stu-id="b84ea-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="b84ea-102">Como parte dos aprimoramentos de desempenho do ASP.NET Core 3,0, a extensibilidade do `DefaultHttpContext` foi removida.</span><span class="sxs-lookup"><span data-stu-id="b84ea-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="b84ea-103">A classe agora é `sealed` .</span><span class="sxs-lookup"><span data-stu-id="b84ea-103">The class is now `sealed`.</span></span> <span data-ttu-id="b84ea-104">Para obter mais informações, consulte [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="b84ea-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="b84ea-105">Se os testes de unidade usarem `Mock<DefaultHttpContext>` , use `Mock<HttpContext>` ou `new DefaultHttpContext()` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b84ea-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="b84ea-106">Para obter uma discussão, consulte [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="b84ea-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b84ea-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b84ea-107">Version introduced</span></span>

<span data-ttu-id="b84ea-108">3,0</span><span class="sxs-lookup"><span data-stu-id="b84ea-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b84ea-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="b84ea-109">Old behavior</span></span>

<span data-ttu-id="b84ea-110">Classes podem derivar de `DefaultHttpContext` .</span><span class="sxs-lookup"><span data-stu-id="b84ea-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b84ea-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="b84ea-111">New behavior</span></span>

<span data-ttu-id="b84ea-112">Classes não podem derivar de `DefaultHttpContext` .</span><span class="sxs-lookup"><span data-stu-id="b84ea-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b84ea-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b84ea-113">Reason for change</span></span>

<span data-ttu-id="b84ea-114">A extensibilidade foi inicialmente fornecida para permitir o pooling do `HttpContext` , mas introduziu uma complexidade desnecessária e impedia outras otimizações.</span><span class="sxs-lookup"><span data-stu-id="b84ea-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b84ea-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b84ea-115">Recommended action</span></span>

<span data-ttu-id="b84ea-116">Se você estiver usando `Mock<DefaultHttpContext>` em seus testes de unidade, comece a usar `Mock<HttpContext>` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b84ea-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="b84ea-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="b84ea-117">Category</span></span>

<span data-ttu-id="b84ea-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b84ea-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b84ea-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b84ea-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
