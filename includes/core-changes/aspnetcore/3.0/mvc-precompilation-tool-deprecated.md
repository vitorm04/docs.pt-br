---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394100"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="4ce57-101">MVC: ferramenta de pré-compilação preterida</span><span class="sxs-lookup"><span data-stu-id="4ce57-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="4ce57-102">No ASP.NET Core 1,1, o pacote `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (ferramenta de pré-compilação MVC) foi introduzido para adicionar suporte à compilação de tempo de publicação de arquivos Razor (arquivos *. cshtml* ).</span><span class="sxs-lookup"><span data-stu-id="4ce57-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="4ce57-103">No ASP.NET Core 2,1, o [SDK do Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) foi introduzido para expandir os recursos da ferramenta de pré-compilação.</span><span class="sxs-lookup"><span data-stu-id="4ce57-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="4ce57-104">O SDK do Razor adicionou suporte para compilação de compilação e tempo de publicação de arquivos Razor.</span><span class="sxs-lookup"><span data-stu-id="4ce57-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="4ce57-105">O SDK verifica a exatidão dos arquivos *. cshtml* no momento da compilação, ao mesmo tempo em que melhora o tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ce57-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="4ce57-106">O SDK do Razor está ativado por padrão e nenhum gesto é necessário para começar a usá-lo.</span><span class="sxs-lookup"><span data-stu-id="4ce57-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="4ce57-107">No ASP.NET Core 3,0, a ferramenta de pré-compilação MVC ASP.NET Core 1,1 de era removida.</span><span class="sxs-lookup"><span data-stu-id="4ce57-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="4ce57-108">Versões anteriores do pacote continuarão recebendo correções importantes de bugs e de segurança na versão do patch.</span><span class="sxs-lookup"><span data-stu-id="4ce57-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="4ce57-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="4ce57-109">Version introduced</span></span>

<span data-ttu-id="4ce57-110">3.0</span><span class="sxs-lookup"><span data-stu-id="4ce57-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4ce57-111">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="4ce57-111">Old behavior</span></span>

<span data-ttu-id="4ce57-112">O pacote `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` foi usado para pré-compilar exibições do Razor do MVC.</span><span class="sxs-lookup"><span data-stu-id="4ce57-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4ce57-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="4ce57-113">New behavior</span></span>

<span data-ttu-id="4ce57-114">O SDK do Razor oferece suporte nativo a essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="4ce57-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="4ce57-115">O pacote `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` não é mais atualizado.</span><span class="sxs-lookup"><span data-stu-id="4ce57-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4ce57-116">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="4ce57-116">Reason for change</span></span>

<span data-ttu-id="4ce57-117">O SDK do Razor fornece mais funcionalidade e verifica a exatidão dos arquivos *. cshtml* no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="4ce57-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="4ce57-118">O SDK também melhora o tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ce57-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4ce57-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="4ce57-119">Recommended action</span></span>

<span data-ttu-id="4ce57-120">Para usuários do ASP.NET Core 2,1 ou posterior, atualize para usar o suporte nativo para pré-compilação no SDK do [Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="4ce57-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="4ce57-121">Se os bugs ou os recursos ausentes impedirem a migração para o SDK do Razor, abra um problema em [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="4ce57-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="4ce57-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="4ce57-122">Category</span></span>

<span data-ttu-id="4ce57-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4ce57-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ce57-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4ce57-124">Affected APIs</span></span>

<span data-ttu-id="4ce57-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4ce57-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
