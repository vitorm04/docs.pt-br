---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901763"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="baeeb-101">MVC: Ferramenta de pré-compilação depreciada</span><span class="sxs-lookup"><span data-stu-id="baeeb-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="baeeb-102">Em ASP.NET Core 1.1, o `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote (ferramenta de pré-compilação MVC) foi introduzido para adicionar suporte para compilação em tempo de publicação de arquivos Razor (arquivos *.cshtml).*</span><span class="sxs-lookup"><span data-stu-id="baeeb-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="baeeb-103">Em ASP.NET Core 2.1, o [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) foi introduzido para expandir os recursos da ferramenta de pré-compilação.</span><span class="sxs-lookup"><span data-stu-id="baeeb-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="baeeb-104">O Razor SDK adicionou suporte para compilação de build e publish-time de arquivos Razor.</span><span class="sxs-lookup"><span data-stu-id="baeeb-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="baeeb-105">O SDK verifica a correção de arquivos *.cshtml* no tempo de compilação enquanto melhora no tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baeeb-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="baeeb-106">O Razor SDK está ligado por padrão, e nenhum gesto é necessário para começar a usá-lo.</span><span class="sxs-lookup"><span data-stu-id="baeeb-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="baeeb-107">Em ASP.NET Core 3.0, a ferramenta de pré-compilação MVC do ASP.NET Core 1.1 foi removida.</span><span class="sxs-lookup"><span data-stu-id="baeeb-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="baeeb-108">As versões anteriores do pacote continuarão recebendo correções importantes de bugs e segurança na versão do patch.</span><span class="sxs-lookup"><span data-stu-id="baeeb-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="baeeb-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="baeeb-109">Version introduced</span></span>

<span data-ttu-id="baeeb-110">3.0</span><span class="sxs-lookup"><span data-stu-id="baeeb-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="baeeb-111">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="baeeb-111">Old behavior</span></span>

<span data-ttu-id="baeeb-112">O `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote foi usado para pré-compilar vistas MVC Razor.</span><span class="sxs-lookup"><span data-stu-id="baeeb-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="baeeb-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="baeeb-113">New behavior</span></span>

<span data-ttu-id="baeeb-114">O Razor SDK suporta nativamente essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="baeeb-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="baeeb-115">O `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` pacote não é mais atualizado.</span><span class="sxs-lookup"><span data-stu-id="baeeb-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="baeeb-116">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="baeeb-116">Reason for change</span></span>

<span data-ttu-id="baeeb-117">O Razor SDK fornece mais funcionalidade e verifica a correção de arquivos *.cshtml* no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="baeeb-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="baeeb-118">O SDK também melhora o tempo de inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baeeb-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="baeeb-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="baeeb-119">Recommended action</span></span>

<span data-ttu-id="baeeb-120">Para usuários de ASP.NET Core 2.1 ou posterior, atualize para usar o suporte nativo para pré-compilação no [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="baeeb-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="baeeb-121">Se bugs ou recursos ausentes impedirem a migração para o Razor SDK, abra um problema no [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="baeeb-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="baeeb-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="baeeb-122">Category</span></span>

<span data-ttu-id="baeeb-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="baeeb-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="baeeb-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="baeeb-124">Affected APIs</span></span>

<span data-ttu-id="baeeb-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="baeeb-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
