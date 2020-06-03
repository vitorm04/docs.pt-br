---
title: Orientação geral
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Diretrizes gerais
ms.date: 09/11/2018
ms.openlocfilehash: 6e63d7804abc1703f17378584d58d66a933022c7
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306871"
---
# <a name="general-guidance"></a><span data-ttu-id="f4f7d-103">Orientação geral</span><span class="sxs-lookup"><span data-stu-id="f4f7d-103">General guidance</span></span>

<span data-ttu-id="f4f7d-104">Esta seção oferece um resumo de quando escolher o .NET Core ou o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="f4f7d-105">Fornecemos mais detalhes sobre essas opções nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="f4f7d-106">Use o .NET Core, com contêineres do Linux ou do Windows, para seu aplicativo de servidor Docker em contêiner quando:</span><span class="sxs-lookup"><span data-stu-id="f4f7d-106">Use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="f4f7d-107">Você tiver necessidades de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-107">You have cross-platform needs.</span></span> <span data-ttu-id="f4f7d-108">Por exemplo, você desejar usar contêineres Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="f4f7d-109">Sua arquitetura de aplicativo for baseada em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="f4f7d-110">For necessário iniciar contêineres rapidamente e você desejar ocupar um espaço menor por contêiner para obter melhor densidade ou mais contêineres por unidade de hardware a fim de reduzir seus custos.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="f4f7d-111">Em resumo, quando você cria novos aplicativos .NET em contêineres, você deve considerar o .NET Core como a opção padrão.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="f4f7d-112">Ela tem muitos benefícios e se ajusta melhor à filosofia e ao estilo de trabalho dos contêineres.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="f4f7d-113">Um benefício adicional de usar o .NET Core é que você pode executar versões do .NET para aplicativos lado a lado dentro do mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="f4f7d-114">Esse benefício é mais importante para servidores ou VMs que não usam contêineres, porque os contêineres isolam as versões do .NET de que o aplicativo precisa.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="f4f7d-115">(Desde que sejam compatíveis com o sistema operacional subjacente.)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="f4f7d-116">Use .NET Framework para seu aplicativo de servidor Docker em contêiner quando:</span><span class="sxs-lookup"><span data-stu-id="f4f7d-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="f4f7d-117">No momento, seu aplicativo usar o .NET Framework e tem fortes dependências no Windows.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="f4f7d-118">For necessário usar APIs do Windows não compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="f4f7d-119">For necessário usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="f4f7d-120">Usar o .NET Framework no Docker pode melhorar suas experiências de implantação minimizando os problemas de implantação.</span><span class="sxs-lookup"><span data-stu-id="f4f7d-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="f4f7d-121">Este [cenário de "lift-and-shift"](https://aka.ms/liftandshiftwithcontainersebook) é importante para colocar aplicativos herdados em contêineres que foram desenvolvidos originalmente com o .NET Framework tradicional, como os serviços ASP.NET WebForms, aplicativos Web MVC ou WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="f4f7d-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f4f7d-122">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f4f7d-122">Additional resources</span></span>

- <span data-ttu-id="f4f7d-123">**Livro eletrônico: modernizar os aplicativos .NET Framework existentes com contêineres do Azure e do Windows**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="f4f7d-124">**Aplicativos de exemplo: modernização de aplicativos Web ASP.NET herdados usando Contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="f4f7d-125">[Anterior](index.md) 
> [Avançar](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
