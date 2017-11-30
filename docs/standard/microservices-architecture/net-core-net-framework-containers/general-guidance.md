---
title: Diretrizes gerais
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Diretrizes gerais"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a><span data-ttu-id="7a6b6-104">Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="7a6b6-104">General guidance</span></span>

<span data-ttu-id="7a6b6-105">Esta seção fornece um resumo de quando escolher .NET Core ou do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="7a6b6-106">Podemos fornecer mais detalhes sobre essas opções nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="7a6b6-107">Você deve usar o .NET Core com contêineres do Windows, ou Linux para o aplicativo de servidor em contêineres do Docker quando:</span><span class="sxs-lookup"><span data-stu-id="7a6b6-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="7a6b6-108">Você tiver necessidades de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-108">You have cross-platform needs.</span></span> <span data-ttu-id="7a6b6-109">Por exemplo, você deseja usar ambos os contêineres do Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="7a6b6-110">A arquitetura do aplicativo é baseada em microservices.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="7a6b6-111">Você precisa iniciar contêineres rápida e desejar uma superfície pequena por contêiner para obter melhor densidade ou mais contêineres por unidade de hardware para reduzir os custos.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="7a6b6-112">Em resumo, quando você cria novos aplicativos .NET em contêineres, você deve considerar o núcleo do .NET como a opção padrão.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="7a6b6-113">Ela tem muitos benefícios e se ajuste melhor com o estilo de trabalho e filosofia de contêineres.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="7a6b6-114">Um benefício adicional de usar o .NET Core é que você pode executar as versões do .NET lado a lado para aplicativos no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="7a6b6-115">Esse benefício é mais importante para servidores ou máquinas virtuais que não usam contêineres, como contêineres isolar as versões do .NET que o aplicativo precisa.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="7a6b6-116">(Desde que eles sejam compatíveis com o sistema operacional subjacente.)</span><span class="sxs-lookup"><span data-stu-id="7a6b6-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="7a6b6-117">Você deve usar o .NET Framework, com contêineres do Windows para o aplicativo de servidor em contêineres do Docker quando:</span><span class="sxs-lookup"><span data-stu-id="7a6b6-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="7a6b6-118">Seu aplicativo usa o .NET Framework e tem dependências fortes no Windows.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="7a6b6-119">Você precisa usar APIs do Windows que não são suportados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="7a6b6-120">Você precisa usar bibliotecas .NET de terceiros ou pacotes do NuGet que não estão disponíveis para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="7a6b6-121">Usando o .NET Framework no Docker pode melhorar sua experiência de implantação, minimizar os problemas de implantação.</span><span class="sxs-lookup"><span data-stu-id="7a6b6-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="7a6b6-122">Isso [ *cenário "comparar e deslocar"* ](https://aka.ms/liftandshiftwithcontainersebook) é importante para aplicativos herdados que foram desenvolvidos originalmente com o .NET Framework tradicionais, como formulários da Web do ASP.NET, MVC web WCF (ou aplicativos de containerizing Serviços do Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="7a6b6-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7a6b6-123">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="7a6b6-123">Additional resources</span></span>

-   <span data-ttu-id="7a6b6-124">**livro eletrônico: modernizar aplicativos existentes do .NET Framework com o Azure e os contêineres do Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="7a6b6-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="7a6b6-125">**Aplicativos de exemplo: modernização aplicativos herdados de web do ASP.NET usando contêineres do Windows**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="7a6b6-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7a6b6-126">[Anterior] (index.md) [Avançar] (net-core-contêiner-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="7a6b6-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>
