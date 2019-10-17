---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393918"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="ab872-101">HTTP: extensibilidade defaulthttpcontext removida</span><span class="sxs-lookup"><span data-stu-id="ab872-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="ab872-102">Como parte dos aprimoramentos de desempenho do ASP.NET Core 3,0, a extensibilidade do `DefaultHttpContext` foi removida.</span><span class="sxs-lookup"><span data-stu-id="ab872-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="ab872-103">Agora, a classe é `sealed`.</span><span class="sxs-lookup"><span data-stu-id="ab872-103">The class is now `sealed`.</span></span> <span data-ttu-id="ab872-104">Para obter mais informações, consulte [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="ab872-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="ab872-105">Se os testes de unidade usarem `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ab872-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span> 

<span data-ttu-id="ab872-106">Para obter uma discussão, consulte [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="ab872-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ab872-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ab872-107">Version introduced</span></span>

<span data-ttu-id="ab872-108">3.0</span><span class="sxs-lookup"><span data-stu-id="ab872-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ab872-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ab872-109">Old behavior</span></span>

<span data-ttu-id="ab872-110">Classes podem derivar de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="ab872-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ab872-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ab872-111">New behavior</span></span>

<span data-ttu-id="ab872-112">Classes não podem derivar de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="ab872-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ab872-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ab872-113">Reason for change</span></span>

<span data-ttu-id="ab872-114">A extensibilidade foi inicialmente fornecida para permitir o pooling do `HttpContext`, mas introduziu uma complexidade desnecessária e impedia outras otimizações.</span><span class="sxs-lookup"><span data-stu-id="ab872-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ab872-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ab872-115">Recommended action</span></span>

<span data-ttu-id="ab872-116">Se você estiver usando `Mock<DefaultHttpContext>` em seus testes de unidade, comece a usar `Mock<HttpContext>` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ab872-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span> 

#### <a name="category"></a><span data-ttu-id="ab872-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="ab872-117">Category</span></span>

<span data-ttu-id="ab872-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab872-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab872-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ab872-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
