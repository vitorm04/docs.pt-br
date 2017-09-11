---
title: .NET Core e software livre
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: db4689ee58b48fad2e3696e5e64aa187710f4868
ms.contentlocale: pt-br
ms.lasthandoff: 08/05/2017

---
# <a name="net-core-and-open-source"></a><span data-ttu-id="3180a-102">.NET Core e software livre</span><span class="sxs-lookup"><span data-stu-id="3180a-102">.NET Core and Open-Source</span></span>
<span data-ttu-id="3180a-103">Este tópico fornece uma breve visão geral sobre o que é o .NET Core e mostra como você pode encontrar mais informações.</span><span class="sxs-lookup"><span data-stu-id="3180a-103">This topic provides a brief overview  of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="3180a-104">Para obter a lista completa de tópicos sobre o .NET Core, visite o [Guia do .NET Core](../../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="3180a-104">To find the complete list of topics for .NET Core, visit the [.NET Core Guide](../../core/index.md).</span></span>
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a><span data-ttu-id="3180a-105">O que é o .NET Core?</span><span class="sxs-lookup"><span data-stu-id="3180a-105">What is .NET Core?</span></span>  
 <span data-ttu-id="3180a-106">.NET Core é uma implementação de software livre, modular, de plataforma cruzada e para fins gerais do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3180a-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="3180a-107">Ele contém muitas das mesmas APIs do .NET Framework (mas o .NET Core é um conjunto menor) e inclui componentes de tempo de execução, estrutura, compilador e ferramentas que oferecem suporte a vários sistemas operacionais e destinos de chip.</span><span class="sxs-lookup"><span data-stu-id="3180a-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="3180a-108">A implementação do .NET Core foi conduzida principalmente por cargas de trabalho ASP.NET Core, mas também pela necessidade e desejo de ter uma implementação mais moderna.</span><span class="sxs-lookup"><span data-stu-id="3180a-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="3180a-109">Ele pode ser usado em cenários de dispositivo, nuvem e IoT/incorporado.</span><span class="sxs-lookup"><span data-stu-id="3180a-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
 <span data-ttu-id="3180a-110">Para começar a usar o .NET Core, visite a [Home page do .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="3180a-110">To get started with .NET Core, please visit the [.NET Core homepage](https://www.microsoft.com/net/core).</span></span>  
  
 <span data-ttu-id="3180a-111">Estas são as principais características do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3180a-111">Here are the main characteristics of .NET Core:</span></span>  
  
-   <span data-ttu-id="3180a-112">**Plataforma cruzada:** o .NET Core fornece uma funcionalidade essencial para implementação de recursos de aplicativo necessários, e reutilização desse código independentemente de seu destino de plataforma.</span><span class="sxs-lookup"><span data-stu-id="3180a-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="3180a-113">No momento, ele oferece suporte aos três principais sistemas operacionais (SO): Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="3180a-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="3180a-114">Você pode escrever aplicativos e bibliotecas que são executados sem modificações em sistemas operacionais com suporte.</span><span class="sxs-lookup"><span data-stu-id="3180a-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="3180a-115">Para ver a lista de sistemas operacionais com suporte, visite [Roteiro do .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).</span><span class="sxs-lookup"><span data-stu-id="3180a-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
-   <span data-ttu-id="3180a-116">**Software livre:** o .NET Core é um dos muitos projetos sob a administração do [.NET Foundation](http://www.dotnetfoundation.org/) e está disponível no [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="3180a-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](http://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="3180a-117">Ter o .NET Core como um projeto de código-fonte aberto promove um processo de desenvolvimento mais transparente e uma comunidade ativa e dedicada.</span><span class="sxs-lookup"><span data-stu-id="3180a-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
-   <span data-ttu-id="3180a-118">**Implantação flexível:** há duas maneiras de implantar seu aplicativo: implantação dependente da estrutura ou implantação independente.</span><span class="sxs-lookup"><span data-stu-id="3180a-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="3180a-119">Com a implantação dependente da estrutura, apenas as dependências de seu aplicativo e de terceiros serão instaladas, e seu aplicativo dependerá da presença de uma versão de todo o sistema do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3180a-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="3180a-120">Com a implantação independente, a versão do .NET Core usada para compilar seu aplicativo também será implantada junto com as dependências de seu aplicativo e de terceiros, e poderá ser executada lado a lado com outras versões.</span><span class="sxs-lookup"><span data-stu-id="3180a-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="3180a-121">Para saber mais, confira [Implantação de aplicativos .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="3180a-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

-   <span data-ttu-id="3180a-122">**Modular:** o .NET Core é modular, pois é liberado por meio do NuGet em pacotes de assembly menores.</span><span class="sxs-lookup"><span data-stu-id="3180a-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="3180a-123">Em vez de um grande assembly contendo a maior parte da funcionalidade principal, o .NET Core é disponibilizado como pacotes menores centrados no recurso.</span><span class="sxs-lookup"><span data-stu-id="3180a-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="3180a-124">Isso permite um modelo de desenvolvimento mais ágil para nós, e permite a otimização de seu aplicativo a fim de incluir apenas os pacotes do NuGet necessários.</span><span class="sxs-lookup"><span data-stu-id="3180a-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="3180a-125">Os benefícios de uma área de superfície menor do aplicativo incluem segurança mais rigorosa, manutenção reduzida, desempenho aprimorado e redução dos custos em um modelo de pagamento “pague pelo que usar”.</span><span class="sxs-lookup"><span data-stu-id="3180a-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="3180a-126">A plataforma do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-126">The .NET Core Platform</span></span>  
 <span data-ttu-id="3180a-127">A plataforma do .NET Core é composta por vários componentes, incluindo os compiladores gerenciados, o tempo de execução, as bibliotecas de classes base e vários modelos de aplicativo, como o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3180a-127">The .NET Core platform is made of several components, which includes the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="3180a-128">Saiba mais sobre os diferentes componentes e envolva-se visitando os seguintes repositórios do [GitHub](https://github.com/):</span><span class="sxs-lookup"><span data-stu-id="3180a-128">You can learn more about the different components and get engaged, by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
-   [<span data-ttu-id="3180a-129">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-129">.NET Core</span></span>](https://github.com/dotnet/core)  
  
-   [<span data-ttu-id="3180a-130">CoreFX - bibliotecas fundamentais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-130">CoreFX - .NET Core foundational libraries</span></span>](https://github.com/dotnet/corefx)  
  
-   [<span data-ttu-id="3180a-131">CoreCLR - Tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-131">CoreCLR - .NET Core runtime</span></span>](https://github.com/dotnet/coreclr)  
  
-   [<span data-ttu-id="3180a-132">CLI - Ferramentas da interface de linha de comando do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
-   [<span data-ttu-id="3180a-133">Roslyn - Plataforma do Compilador .NET</span><span class="sxs-lookup"><span data-stu-id="3180a-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
-   [<span data-ttu-id="3180a-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-134">ASP.NET Core</span></span>](https://github.com/aspnet/home)  
  
## <a name="see-also"></a><span data-ttu-id="3180a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3180a-135">See Also</span></span>  
 <span data-ttu-id="3180a-136">[Home page do .NET Core](https://www.microsoft.com/net/core) </span><span class="sxs-lookup"><span data-stu-id="3180a-136">[.NET Core homepage](https://www.microsoft.com/net/core) </span></span>  
 <span data-ttu-id="3180a-137">[Guia do .NET Core](../../core/index.md) </span><span class="sxs-lookup"><span data-stu-id="3180a-137">[.NET Core Guide](../../core/index.md) </span></span>  
 [<span data-ttu-id="3180a-138">Documentação do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3180a-138">ASP.NET Core Documentation</span></span>](/aspnet/core/)

