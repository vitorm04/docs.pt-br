---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022955"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="8b7f5-101">Middleware: o middleware do manipulador de exceção lança a exceção original se o manipulador não for encontrado</span><span class="sxs-lookup"><span data-stu-id="8b7f5-101">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="8b7f5-102">Antes de ASP.NET Core 5,0, o [middleware do manipulador de exceção](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executa o manipulador de exceção configurado quando uma exceção ocorreu.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-102">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="8b7f5-103">Se o manipulador de exceção, configurado via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> , não puder ser encontrado, uma resposta HTTP 404 será produzida.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-103">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="8b7f5-104">A resposta é enganosa, pois:</span><span class="sxs-lookup"><span data-stu-id="8b7f5-104">The response is misleading in that it:</span></span>

* <span data-ttu-id="8b7f5-105">Parece ser um erro de usuário.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-105">Seems to be a user error.</span></span>
* <span data-ttu-id="8b7f5-106">Obscurece o fato de que uma exceção ocorreu no servidor.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-106">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="8b7f5-107">Para resolver o erro enganoso no ASP.NET Core 5,0, o `ExceptionHandlerMiddleware` lançará a exceção original se o manipulador de exceção não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-107">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="8b7f5-108">Como resultado, uma resposta HTTP 500 é produzida pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-108">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="8b7f5-109">A resposta será mais fácil de examinar nos logs do servidor ao depurar o erro ocorrido.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-109">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="8b7f5-110">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="8b7f5-110">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8b7f5-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8b7f5-111">Version introduced</span></span>

<span data-ttu-id="8b7f5-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="8b7f5-112">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8b7f5-113">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="8b7f5-113">Old behavior</span></span>

<span data-ttu-id="8b7f5-114">O middleware do manipulador de exceção produz uma resposta HTTP 404 se o manipulador de exceção configurado não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-114">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8b7f5-115">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="8b7f5-115">New behavior</span></span>

<span data-ttu-id="8b7f5-116">O middleware do manipulador de exceção lançará a exceção original se o manipulador de exceção configurado não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-116">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8b7f5-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="8b7f5-117">Reason for change</span></span>

<span data-ttu-id="8b7f5-118">O erro HTTP 404 não torna óbvio que ocorreu uma exceção no servidor.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-118">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="8b7f5-119">Essa alteração produz um erro HTTP 500 para deixá-lo óbvio que:</span><span class="sxs-lookup"><span data-stu-id="8b7f5-119">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="8b7f5-120">O problema não é causado por um erro do usuário.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-120">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="8b7f5-121">Exceção encontrada no servidor.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-121">An exception was encountered on the server.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8b7f5-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8b7f5-122">Recommended action</span></span>

<span data-ttu-id="8b7f5-123">Não há nenhuma alteração de API.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-123">There are no API changes.</span></span> <span data-ttu-id="8b7f5-124">Todos os aplicativos existentes continuarão a ser compilados e executados.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-124">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="8b7f5-125">A exceção gerada é tratada pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="8b7f5-125">The exception thrown is handled by the server.</span></span> <span data-ttu-id="8b7f5-126">Por exemplo, a exceção é convertida em uma resposta de erro HTTP 500 por [Kestrel](/aspnet/core/fundamentals/servers/kestrel) ou [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span><span class="sxs-lookup"><span data-stu-id="8b7f5-126">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

#### <a name="category"></a><span data-ttu-id="8b7f5-127">Categoria</span><span class="sxs-lookup"><span data-stu-id="8b7f5-127">Category</span></span>

<span data-ttu-id="8b7f5-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8b7f5-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8b7f5-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8b7f5-129">Affected APIs</span></span>

<span data-ttu-id="8b7f5-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8b7f5-130">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
