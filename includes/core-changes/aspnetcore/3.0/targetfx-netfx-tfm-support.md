---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549612"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="910fe-101">Quadro de destino: o suporte ao framework .NET caiu</span><span class="sxs-lookup"><span data-stu-id="910fe-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="910fe-102">Começando com ASP.NET Core 3.0, o .NET Framework é uma estrutura de destino não suportada.</span><span class="sxs-lookup"><span data-stu-id="910fe-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="910fe-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="910fe-103">Change description</span></span>

<span data-ttu-id="910fe-104">.NET Framework 4.8 é a última versão principal do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="910fe-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="910fe-105">Os novos aplicativos ASP.NET Core devem ser construídos no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="910fe-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="910fe-106">Começando com a versão .NET Core 3.0, você pode pensar em ASP.NET Core 3.0 como sendo parte do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="910fe-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="910fe-107">Os clientes que usam ASP.NET Core com o .NET Framework podem continuar de forma totalmente suportada usando a [versão 2.1 LTS](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="910fe-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="910fe-108">O suporte e a manutenção do 2.1 continua até pelo menos 21 de agosto de 2021.</span><span class="sxs-lookup"><span data-stu-id="910fe-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="910fe-109">Esta data é de três anos após a declaração da liberação do LTS pela [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="910fe-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy).</span></span> <span data-ttu-id="910fe-110">O suporte para ASP.NET pacotes Core 2.1 **no .NET Framework** se estenderá indefinidamente, semelhante à [política de manutenção para outros frameworks de ASP.NET baseados em pacotes.](https://dotnet.microsoft.com/platform/support/policy/aspnet)</span><span class="sxs-lookup"><span data-stu-id="910fe-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="910fe-111">Para obter mais informações sobre a portação do .NET Framework para .NET Core, consulte [Porting to .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="910fe-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="910fe-112">`Microsoft.Extensions`pacotes (como registro, injeção de dependência e configuração) e Entity Framework Core não são afetados.</span><span class="sxs-lookup"><span data-stu-id="910fe-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="910fe-113">Eles continuarão a apoiar o .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="910fe-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="910fe-114">Para obter mais informações sobre a motivação dessa mudança, consulte [o post original do blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="910fe-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="910fe-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="910fe-115">Version introduced</span></span>

<span data-ttu-id="910fe-116">3.0</span><span class="sxs-lookup"><span data-stu-id="910fe-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="910fe-117">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="910fe-117">Old behavior</span></span>

<span data-ttu-id="910fe-118">ASP.NET os aplicativos Core podem ser executados no .NET Core ou no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="910fe-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="910fe-119">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="910fe-119">New behavior</span></span>

<span data-ttu-id="910fe-120">ASP.NET aplicativos Core só podem ser executados no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="910fe-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="910fe-121">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="910fe-121">Recommended action</span></span>

<span data-ttu-id="910fe-122">Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="910fe-122">Take one of the following actions:</span></span>

- <span data-ttu-id="910fe-123">Mantenha seu aplicativo no ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="910fe-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="910fe-124">Migre seu aplicativo e suas dependências para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="910fe-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="910fe-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="910fe-125">Category</span></span>

<span data-ttu-id="910fe-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="910fe-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="910fe-127">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="910fe-127">Affected APIs</span></span>

<span data-ttu-id="910fe-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="910fe-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
