---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394401"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="e0875-101">MVC: Shim de compatibilidade da API web removido</span><span class="sxs-lookup"><span data-stu-id="e0875-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="e0875-102">A partir de ASP.NET Core `Microsoft.AspNetCore.Mvc.WebApiCompatShim` 3.0, o pacote não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="e0875-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e0875-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="e0875-103">Change description</span></span>

<span data-ttu-id="e0875-104">O `Microsoft.AspNetCore.Mvc.WebApiCompatShim` pacote (WebApiCompatShim) fornece compatibilidade parcial no ASP.NET Core com ASP.NET API 2 da Web para simplificar as implementações de API da Web existentes migratórias para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0875-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="e0875-105">No entanto, os aplicativos que usam o WebApiCompatShim não se beneficiam dos recursos relacionados à API enviados nos últimos lançamentos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0875-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="e0875-106">Esses recursos incluem uma melhor geração de especificação de API Aberta, manipulação padronizada de erros e geração de código do cliente.</span><span class="sxs-lookup"><span data-stu-id="e0875-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="e0875-107">Para melhor concentrar os esforços da API no 3.0, o WebApiCompatShim foi removido.</span><span class="sxs-lookup"><span data-stu-id="e0875-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="e0875-108">Os aplicativos existentes que usam o WebApiCompatShim devem migrar para o modelo mais `[ApiController]` novo.</span><span class="sxs-lookup"><span data-stu-id="e0875-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e0875-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e0875-109">Version introduced</span></span>

<span data-ttu-id="e0875-110">3.0</span><span class="sxs-lookup"><span data-stu-id="e0875-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e0875-111">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="e0875-111">Reason for change</span></span>

<span data-ttu-id="e0875-112">O shim de compatibilidade da API da Web era uma ferramenta de migração.</span><span class="sxs-lookup"><span data-stu-id="e0875-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="e0875-113">Ele restringe o acesso do usuário a novas funcionalidades adicionadas no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0875-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e0875-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e0875-114">Recommended action</span></span>

<span data-ttu-id="e0875-115">Remova o uso deste shim e migre diretamente para a funcionalidade semelhante no próprio ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0875-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="e0875-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="e0875-116">Category</span></span>

<span data-ttu-id="e0875-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e0875-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0875-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e0875-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
