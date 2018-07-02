---
title: Diretrizes gerais
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Diretrizes gerais
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: bd654c23cf8a8d0986575642ef25d6864251a4e4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104073"
---
# <a name="general-guidance"></a><span data-ttu-id="a8f5c-103">Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="a8f5c-103">General guidance</span></span>

<span data-ttu-id="a8f5c-104">Esta seção oferece um resumo de quando escolher o .NET Core ou o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="a8f5c-105">Fornecemos mais detalhes sobre essas opções nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="a8f5c-106">Você deverá usar o .NET Core, com contêineres Linux ou do Windows, para seu aplicativo para servidores do Docker em contêineres quando:</span><span class="sxs-lookup"><span data-stu-id="a8f5c-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="a8f5c-107">Você tiver necessidades de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-107">You have cross-platform needs.</span></span> <span data-ttu-id="a8f5c-108">Por exemplo, você desejar usar contêineres Linux e do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-108">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="a8f5c-109">Sua arquitetura de aplicativo for baseada em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-109">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="a8f5c-110">For necessário iniciar contêineres rapidamente e você desejar ocupar um espaço menor por contêiner para obter melhor densidade ou mais contêineres por unidade de hardware a fim de reduzir seus custos.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="a8f5c-111">Em resumo, quando você cria novos aplicativos .NET em contêineres, você deve considerar o .NET Core como a opção padrão.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="a8f5c-112">Ela tem muitos benefícios e se ajusta melhor à filosofia e ao estilo de trabalho dos contêineres.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="a8f5c-113">Um benefício adicional de usar o .NET Core é que você pode executar versões do .NET para aplicativos lado a lado dentro do mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="a8f5c-114">Esse benefício é mais importante para servidores ou VMs que não usam contêineres, porque os contêineres isolam as versões do .NET de que o aplicativo precisa.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="a8f5c-115">(Desde que sejam compatíveis com o sistema operacional subjacente.)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="a8f5c-116">Você deverá usar o .NET Framework, com contêineres do Windows, para seu aplicativo para servidores do Docker em contêineres quando:</span><span class="sxs-lookup"><span data-stu-id="a8f5c-116">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="a8f5c-117">No momento, seu aplicativo usar o .NET Framework e tem fortes dependências no Windows.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="a8f5c-118">For necessário usar APIs do Windows não compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="a8f5c-119">For necessário usar bibliotecas .NET de terceiros ou pacotes NuGet não disponíveis para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="a8f5c-120">Usar o .NET Framework no Docker pode melhorar suas experiências de implantação minimizando os problemas de implantação.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="a8f5c-121">Este [*cenário de "lift-and-shift"*](https://aka.ms/liftandshiftwithcontainersebook) é importante para colocar aplicativos herdados em contêineres que foram desenvolvidos originalmente com o .NET Framework tradicional, como os serviços ASP.NET WebForms, aplicativos Web MVC ou WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="a8f5c-121">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a8f5c-122">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="a8f5c-122">Additional resources</span></span>

-   <span data-ttu-id="a8f5c-123">**Livro eletrônico: Modernizar aplicativos .NET Framework existentes com o Azure e Contêineres do Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-123">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="a8f5c-124">**Aplicativos de exemplo: modernização de aplicativos Web ASP.NET herdados usando Contêineres do Windows**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a8f5c-125">[Anterior](index.md)
[Próximo](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
