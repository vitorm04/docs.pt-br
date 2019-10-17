---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394401"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="c4e72-101">MVC: Shim de compatibilidade da API Web removido</span><span class="sxs-lookup"><span data-stu-id="c4e72-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="c4e72-102">A partir do ASP.NET Core 3,0, o pacote `Microsoft.AspNetCore.Mvc.WebApiCompatShim` não está mais disponível.</span><span class="sxs-lookup"><span data-stu-id="c4e72-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c4e72-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="c4e72-103">Change description</span></span>

<span data-ttu-id="c4e72-104">O pacote `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) fornece compatibilidade parcial em ASP.NET Core com a API Web do ASP.NET 4. x para simplificar a migração de implementações de API Web existentes para ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4e72-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="c4e72-105">No entanto, os aplicativos que usam o WebApiCompatShim não se beneficiam dos recursos relacionados à API fornecidos em versões recentes de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4e72-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="c4e72-106">Esses recursos incluem geração aprimorada de especificação de API aberta, tratamento de erro padronizado e geração de código de cliente.</span><span class="sxs-lookup"><span data-stu-id="c4e72-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="c4e72-107">Para focar melhor os esforços de API em 3,0, o WebApiCompatShim foi removido.</span><span class="sxs-lookup"><span data-stu-id="c4e72-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="c4e72-108">Os aplicativos existentes que usam o WebApiCompatShim devem migrar para o modelo `[ApiController]` mais recente.</span><span class="sxs-lookup"><span data-stu-id="c4e72-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c4e72-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c4e72-109">Version introduced</span></span>

<span data-ttu-id="c4e72-110">3.0</span><span class="sxs-lookup"><span data-stu-id="c4e72-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c4e72-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="c4e72-111">Reason for change</span></span>

<span data-ttu-id="c4e72-112">O Shim da compatibilidade da API Web era uma ferramenta de migração.</span><span class="sxs-lookup"><span data-stu-id="c4e72-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="c4e72-113">Ele restringe o acesso do usuário à nova funcionalidade adicionada no ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4e72-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c4e72-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c4e72-114">Recommended action</span></span>

<span data-ttu-id="c4e72-115">Remova o uso desse Shim e migre diretamente para a funcionalidade semelhante no ASP.NET Core em si.</span><span class="sxs-lookup"><span data-stu-id="c4e72-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="c4e72-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="c4e72-116">Category</span></span>

<span data-ttu-id="c4e72-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c4e72-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c4e72-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c4e72-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
