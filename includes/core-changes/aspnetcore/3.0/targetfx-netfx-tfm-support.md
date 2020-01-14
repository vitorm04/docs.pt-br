---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937276"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="6a156-101">Estrutura de destino: suporte a .NET Framework Descartado</span><span class="sxs-lookup"><span data-stu-id="6a156-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="6a156-102">A partir do ASP.NET Core 3,0, .NET Framework é uma estrutura de destino sem suporte.</span><span class="sxs-lookup"><span data-stu-id="6a156-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6a156-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="6a156-103">Change description</span></span>

<span data-ttu-id="6a156-104">.NET Framework 4,8 é a última versão principal do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a156-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="6a156-105">Novos aplicativos de ASP.NET Core devem ser criados no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a156-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="6a156-106">A partir da versão 3,0 do .NET Core, você pode considerar ASP.NET Core 3,0 como parte do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a156-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="6a156-107">Os clientes que usam ASP.NET Core com .NET Framework podem continuar de uma maneira totalmente compatível usando a [versão 2,1 do LTS](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="6a156-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="6a156-108">O suporte e serviço para 2,1 continua até, pelo menos, 21 de agosto de 2021.</span><span class="sxs-lookup"><span data-stu-id="6a156-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="6a156-109">Essa data é de três anos após a declaração da versão do LTS de acordo com a [política de suporte do .net](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="6a156-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="6a156-110">O suporte para pacotes ASP.NET Core 2,1 **em .NET Framework** será estendido indefinidamente, semelhante à [política de serviço para outras estruturas ASP.net baseadas em pacote](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="6a156-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="6a156-111">Para obter mais informações sobre como portar do .NET Framework para o .NET Core, consulte [portando para o .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a156-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="6a156-112">`Microsoft.Extensions` pacotes (como registro em log, injeção de dependência e configuração) e Entity Framework Core não são afetados.</span><span class="sxs-lookup"><span data-stu-id="6a156-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="6a156-113">Eles continuarão a dar suporte a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6a156-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="6a156-114">Para obter mais informações sobre a motivação para essa alteração, consulte [a postagem do blog original](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="6a156-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6a156-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6a156-115">Version introduced</span></span>

<span data-ttu-id="6a156-116">3.0</span><span class="sxs-lookup"><span data-stu-id="6a156-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6a156-117">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="6a156-117">Old behavior</span></span>

<span data-ttu-id="6a156-118">ASP.NET Core aplicativos podem ser executados no .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a156-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6a156-119">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="6a156-119">New behavior</span></span>

<span data-ttu-id="6a156-120">ASP.NET Core aplicativos só podem ser executados no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a156-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6a156-121">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6a156-121">Recommended action</span></span>

<span data-ttu-id="6a156-122">Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="6a156-122">Take one of the following actions:</span></span>

- <span data-ttu-id="6a156-123">Mantenha seu aplicativo no ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6a156-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="6a156-124">Migre seu aplicativo e as dependências para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a156-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="6a156-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="6a156-125">Category</span></span>

<span data-ttu-id="6a156-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6a156-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6a156-127">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6a156-127">Affected APIs</span></span>

<span data-ttu-id="6a156-128">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6a156-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
