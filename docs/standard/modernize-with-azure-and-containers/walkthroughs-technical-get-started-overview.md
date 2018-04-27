---
title: Explicações passo a passo e technical obter a visão geral de Introdução
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | explicações passo a passo e technical obter a visão geral de Introdução
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0bad7e3afbdf3e55c447319b3756f2235b9e0a19
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="474c9-103">Explicações passo a passo e technical obter a visão geral de Introdução</span><span class="sxs-lookup"><span data-stu-id="474c9-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="474c9-104">Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="474c9-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="474c9-105">A série online de instruções passo a passo é descrita neste capítulo aborda a instalação passo a passo de vários ambientes baseados em contêineres do Windows e a implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="474c9-106">As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="474c9-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="474c9-107">Você pode obter instruções passo a passo em si no *eShopModernizing* aplicativos wiki de repositório do GitHub em [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="474c9-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="474c9-108">Lista de instruções passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-108">Technical walkthrough list</span></span>

<span data-ttu-id="474c9-109">Orientações iniciada por get a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo de comparação de precisão e shift usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="474c9-110">Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de amostra, que estão disponíveis no GitHub em [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="474c9-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="474c9-111">**Tour de aplicativos herdados eShop**</span><span class="sxs-lookup"><span data-stu-id="474c9-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="474c9-112">**Coloca seus aplicativos existentes do .NET com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="474c9-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="474c9-113">**Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="474c9-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="474c9-114">**Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure**</span><span class="sxs-lookup"><span data-stu-id="474c9-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="474c9-115">**Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="474c9-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="474c9-116">Passo a passo 1: Tour aplicativos herdados eShop</span><span class="sxs-lookup"><span data-stu-id="474c9-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="474c9-117">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-117">Technical walkthrough availability</span></span>

<span data-ttu-id="474c9-118">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="474c9-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="474c9-119">Visão geral</span><span class="sxs-lookup"><span data-stu-id="474c9-119">Overview</span></span>

<span data-ttu-id="474c9-120">Neste passo a passo, você pode explorar a implementação inicial dos dois aplicativos herdados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="474c9-120">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="474c9-121">Os dois aplicativos de exemplo tem uma arquitetura monolítica e foram criados usando o ASP.NET clássico.</span><span class="sxs-lookup"><span data-stu-id="474c9-121">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="474c9-122">Um aplicativo é baseado no ASP.NET 4. x MVC; o segundo aplicativo é baseado em Web Forms do ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="474c9-122">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="474c9-123">Ambos os aplicativos estão no [eShopModernizing do repositório GitHub](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="474c9-123">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="474c9-124">Você pode coloca os dois aplicativos de exemplo, semelhante ao modo coloca um clássico [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) aplicativo (WCF) a serem consumidos como um aplicativo de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="474c9-124">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="474c9-125">Para obter um exemplo, consulte [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="474c9-125">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="474c9-126">Objetivos</span><span class="sxs-lookup"><span data-stu-id="474c9-126">Goals</span></span>

<span data-ttu-id="474c9-127">O objetivo principal deste passo a passo é apenas para se familiarizar com esses aplicativos e seu código e configuração.</span><span class="sxs-lookup"><span data-stu-id="474c9-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="474c9-128">Você pode configurar os aplicativos para que eles gerarem e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="474c9-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="474c9-129">Essa configuração opcional baseia-se na injeção de dependência, de modo separado.</span><span class="sxs-lookup"><span data-stu-id="474c9-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="474c9-130">Cenário</span><span class="sxs-lookup"><span data-stu-id="474c9-130">Scenario</span></span>

<span data-ttu-id="474c9-131">Figura 5-1 mostra um cenário simples de aplicativos herdados originais.</span><span class="sxs-lookup"><span data-stu-id="474c9-131">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Cenário de arquitetura simples dos aplicativos herdados originais](./media/image5-1.png)
>
> <span data-ttu-id="474c9-133">**Figura 5-1.**</span><span class="sxs-lookup"><span data-stu-id="474c9-133">**Figure 5-1.**</span></span> <span data-ttu-id="474c9-134">Cenário de arquitetura simples dos aplicativos herdados originais</span><span class="sxs-lookup"><span data-stu-id="474c9-134">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="474c9-135">De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="474c9-135">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="474c9-136">Membros da equipe do enterprise eShop usaria o aplicativo para exibir e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="474c9-136">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="474c9-137">Figura 5-2 mostra as capturas de tela inicial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-137">Figure 5-2 shows the initial app screenshots.</span></span>

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)](./media/image5-2.png)

> <span data-ttu-id="474c9-139">**Figura 5-2.**</span><span class="sxs-lookup"><span data-stu-id="474c9-139">**Figure 5-2.**</span></span> <span data-ttu-id="474c9-140">Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)</span><span class="sxs-lookup"><span data-stu-id="474c9-140">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="474c9-141">Esses são aplicativos web que são usados para navegar e modificar as entradas do catálogo.</span><span class="sxs-lookup"><span data-stu-id="474c9-141">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="474c9-142">O fato de que ambos os aplicativos fornecem os mesmos recursos funcionais/de negócios é simplesmente para fins de comparação.</span><span class="sxs-lookup"><span data-stu-id="474c9-142">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="474c9-143">Você pode ver um processo modernização semelhante para aplicativos que foram criados usando as estruturas de Web Forms do ASP.NET MVC do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="474c9-143">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="474c9-144">Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET MVC de núcleo.</span><span class="sxs-lookup"><span data-stu-id="474c9-144">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="474c9-145">Isso demonstra que o ponto de se você não deseja refazer a arquitetura ou reescrever o código, você pode coloca os aplicativos existentes e ainda usar as mesmas tecnologias .NET e o mesmo código de erro.</span><span class="sxs-lookup"><span data-stu-id="474c9-145">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="474c9-146">Você pode ver como você pode executar aplicativos como esses contêineres, sem qualquer alteração de código herdado.</span><span class="sxs-lookup"><span data-stu-id="474c9-146">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="474c9-147">Benefícios</span><span class="sxs-lookup"><span data-stu-id="474c9-147">Benefits</span></span>

<span data-ttu-id="474c9-148">Os benefícios deste passo a passo são simples: basta se familiarizar com a configuração do aplicativo e de código, com base em injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="474c9-148">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="474c9-149">Em seguida, você pode fazer experiências com essa abordagem quando você coloca e implanta em vários ambientes no futuro.</span><span class="sxs-lookup"><span data-stu-id="474c9-149">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="474c9-150">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="474c9-150">Next steps</span></span>

<span data-ttu-id="474c9-151">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="474c9-151">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="474c9-152">Passo a passo 2: Coloca seus aplicativos existentes do .NET com contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="474c9-152">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="474c9-153">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-153">Technical walkthrough availability</span></span>

<span data-ttu-id="474c9-154">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="474c9-154">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="474c9-155">Visão geral</span><span class="sxs-lookup"><span data-stu-id="474c9-155">Overview</span></span>

<span data-ttu-id="474c9-156">Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, formulários da Web ou WCF, para ambientes de teste, desenvolvimento e produção.</span><span class="sxs-lookup"><span data-stu-id="474c9-156">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="474c9-157">Objetivos</span><span class="sxs-lookup"><span data-stu-id="474c9-157">Goals</span></span>

<span data-ttu-id="474c9-158">O objetivo deste passo a passo é mostrar a você diversas opções para containerizing um aplicativo existente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="474c9-158">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="474c9-159">Você pode:</span><span class="sxs-lookup"><span data-stu-id="474c9-159">You can:</span></span>

- <span data-ttu-id="474c9-160">Coloca o seu aplicativo usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (2017 do Visual Studio ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="474c9-160">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="474c9-161">Coloca o seu aplicativo manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="474c9-161">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="474c9-162">Coloca o seu aplicativo usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (um código-fonte aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="474c9-162">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="474c9-163">Este passo a passo enfoca o Visual Studio Tools 2017 abordagem Docker, mas as duas abordagens são bastante semelhantes em termos de uso Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="474c9-163">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="474c9-164">Cenário</span><span class="sxs-lookup"><span data-stu-id="474c9-164">Scenario</span></span>

<span data-ttu-id="474c9-165">Figura 5-3 mostra o cenário para aplicativos herdados eShop em contêineres.</span><span class="sxs-lookup"><span data-stu-id="474c9-165">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Diagrama de arquitetura simplificada de aplicativos em contêineres em um ambiente de desenvolvimento](./media/image5-3.png)
>
> <span data-ttu-id="474c9-167">**Figura 5-3.**</span><span class="sxs-lookup"><span data-stu-id="474c9-167">**Figure 5-3.**</span></span> <span data-ttu-id="474c9-168">Diagrama de arquitetura simplificada de aplicativos em contêineres em um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="474c9-168">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="474c9-169">Benefícios</span><span class="sxs-lookup"><span data-stu-id="474c9-169">Benefits</span></span>

<span data-ttu-id="474c9-170">Há vantagens para executar seu aplicativo monolítico em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="474c9-170">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="474c9-171">Primeiro, crie uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-171">First, you create an image for the application.</span></span> <span data-ttu-id="474c9-172">Daí em diante, cada implantação é executado no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="474c9-172">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="474c9-173">Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instalado, usa a mesma versão do framework .NET e é criado usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="474c9-173">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="474c9-174">Basicamente, você deve controlar as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="474c9-174">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="474c9-175">As dependências de viagem com o aplicativo ao implantar os contêineres.</span><span class="sxs-lookup"><span data-stu-id="474c9-175">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="474c9-176">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="474c9-176">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="474c9-177">Problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de ter em um ambiente de preparo ou produção.</span><span class="sxs-lookup"><span data-stu-id="474c9-177">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="474c9-178">Diferenças nos ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="474c9-178">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="474c9-179">Aplicativos em contêineres também têm uma curva mais simples de expansão.</span><span class="sxs-lookup"><span data-stu-id="474c9-179">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="474c9-180">Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo comum por máquina.</span><span class="sxs-lookup"><span data-stu-id="474c9-180">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="474c9-181">Isso resulta em maior densidade e menos necessários recursos, especialmente quando você usar orchestrators como Kubernetes ou do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="474c9-181">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="474c9-182">Enormemente, em situações ideais, não exige a fazer alterações no código do aplicativo (C\#).</span><span class="sxs-lookup"><span data-stu-id="474c9-182">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="474c9-183">Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e compor Docker).</span><span class="sxs-lookup"><span data-stu-id="474c9-183">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="474c9-184">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="474c9-184">Next steps</span></span>

<span data-ttu-id="474c9-185">Explore o conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="474c9-185">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="474c9-186">Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="474c9-186">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="474c9-187">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-187">Technical walkthrough availability</span></span>

<span data-ttu-id="474c9-188">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="474c9-188">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="474c9-189">Visão geral</span><span class="sxs-lookup"><span data-stu-id="474c9-189">Overview</span></span>

<span data-ttu-id="474c9-190">A implantação para um host Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite configurar rapidamente ambientes de teste/desenvolvimento/teste.</span><span class="sxs-lookup"><span data-stu-id="474c9-190">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="474c9-191">Ele também fornece um local comum para testadores ou usuários de negócios validar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-191">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="474c9-192">Máquinas virtuais também podem ser infra-estrutura válida como ambientes de produção de serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="474c9-192">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="474c9-193">Objetivos</span><span class="sxs-lookup"><span data-stu-id="474c9-193">Goals</span></span>

<span data-ttu-id="474c9-194">O objetivo deste passo a passo é mostrar a você as várias alternativas que ao implantar contêineres do Windows em máquinas virtuais do Azure que são baseados no Windows Server 2016 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="474c9-194">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="474c9-195">Cenários</span><span class="sxs-lookup"><span data-stu-id="474c9-195">Scenarios</span></span>

<span data-ttu-id="474c9-196">Vários cenários são abordados neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="474c9-196">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="474c9-197">Cenário a: implantar para uma VM do Azure a partir de um computador de desenvolvimento por meio de conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="474c9-197">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

> <span data-ttu-id="474c9-199">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="474c9-199">**Figure 5-4.**</span></span> <span data-ttu-id="474c9-200">Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="474c9-200">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="474c9-201">Cenário b: implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="474c9-201">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

> <span data-ttu-id="474c9-203">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="474c9-203">**Figure 5-5.**</span></span> <span data-ttu-id="474c9-204">Implantar uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="474c9-204">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="474c9-205">Cenário c: implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-205">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services](./media/image5-6.png)

> <span data-ttu-id="474c9-207">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="474c9-207">**Figure 5-6.**</span></span> <span data-ttu-id="474c9-208">Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-208">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="474c9-209">Máquinas virtuais do Azure para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="474c9-209">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="474c9-210">Máquinas virtuais do Azure para contêineres do Windows são VMs com base no Windows Server 2016, o Windows 10 ou versões posteriores, ambos com o mecanismo do Docker configurado.</span><span class="sxs-lookup"><span data-stu-id="474c9-210">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="474c9-211">Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-211">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="474c9-212">Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**.</span><span class="sxs-lookup"><span data-stu-id="474c9-212">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="474c9-213">Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou Nano Server do Windows.</span><span class="sxs-lookup"><span data-stu-id="474c9-213">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="474c9-214">Imagens de contêiner do sistema operacional estão instaladas e, em seguida, a máquina virtual está pronta para uso com o Docker.</span><span class="sxs-lookup"><span data-stu-id="474c9-214">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="474c9-215">Benefícios</span><span class="sxs-lookup"><span data-stu-id="474c9-215">Benefits</span></span>

<span data-ttu-id="474c9-216">Embora os contêineres do Windows podem ser implantados em VMs do local no Windows Server 2016, quando você implanta no Azure, você obterá uma maneira fácil de começar, prontos para uso VMs de contêiner do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="474c9-216">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="474c9-217">Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de escala de máquina virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-217">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="474c9-218">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="474c9-218">Next steps</span></span>

<span data-ttu-id="474c9-219">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="474c9-219">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="474c9-220">Passo a passo 4: Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="474c9-220">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="474c9-221">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-221">Technical walkthrough availability</span></span>

<span data-ttu-id="474c9-222">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="474c9-222">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="474c9-223">Visão geral</span><span class="sxs-lookup"><span data-stu-id="474c9-223">Overview</span></span>

<span data-ttu-id="474c9-224">Um aplicativo baseado em contêineres do Windows precisará rapidamente usam as plataformas, ainda mais se afastando de VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="474c9-224">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="474c9-225">Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="474c9-225">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="474c9-226">Você pode atingir essas metas, usando o orchestrator [Kubernetes](https://kubernetes.io/), disponível em [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="474c9-226">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="474c9-227">Objetivos</span><span class="sxs-lookup"><span data-stu-id="474c9-227">Goals</span></span>

<span data-ttu-id="474c9-228">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado no contêiner do Windows para Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-228">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="474c9-229">Implantando a Kubernetes de zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="474c9-229">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="474c9-230">Implante um cluster de Kubernetes para serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-230">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="474c9-231">Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="474c9-231">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="474c9-232">Cenários</span><span class="sxs-lookup"><span data-stu-id="474c9-232">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="474c9-233">Cenário a: a implantar diretamente a um cluster de Kubernetes a partir de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="474c9-233">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

> <span data-ttu-id="474c9-235">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="474c9-235">**Figure 5-7.**</span></span> <span data-ttu-id="474c9-236">Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="474c9-236">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="474c9-237">Cenário b: implantar um cluster Kubernetes do CI/CD pipelines no Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-237">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services](./media/image5-8.png)

> <span data-ttu-id="474c9-239">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="474c9-239">**Figure 5-8.**</span></span> <span data-ttu-id="474c9-240">Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-240">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="474c9-241">Benefícios</span><span class="sxs-lookup"><span data-stu-id="474c9-241">Benefits</span></span>

<span data-ttu-id="474c9-242">Há muitos benefícios à implantação em um cluster em Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="474c9-242">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="474c9-243">O maior benefício é que você obtenha um ambiente pronto para produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e com base no número de nós ou VMs no (cluster escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="474c9-243">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="474c9-244">Serviço de contêiner do Azure otimiza tecnologias e ferramentas de código aberto populares especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-244">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="474c9-245">Você obtém uma solução aberta que oferece portabilidade, para os contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-245">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="474c9-246">Selecione o tamanho, o número de hosts, e o contêiner de ferramentas orchestrator serviço controla todo o resto.</span><span class="sxs-lookup"><span data-stu-id="474c9-246">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="474c9-247">Kubernetes, os desenvolvedores podem passam da ideia sobre máquinas físicas e virtuais, para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="474c9-247">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="474c9-248">Aplicativos com base em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="474c9-248">Applications based on multiple containers</span></span>

- <span data-ttu-id="474c9-249">Replicação de instâncias de contêiner e o dimensionamento automático horizontal</span><span class="sxs-lookup"><span data-stu-id="474c9-249">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="474c9-250">Nomenclatura e descobrir (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="474c9-250">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="474c9-251">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="474c9-251">Balancing loads</span></span>

- <span data-ttu-id="474c9-252">Atualizações móveis</span><span class="sxs-lookup"><span data-stu-id="474c9-252">Rolling updates</span></span>

- <span data-ttu-id="474c9-253">Distribuindo segredos</span><span class="sxs-lookup"><span data-stu-id="474c9-253">Distributing secrets</span></span>

- <span data-ttu-id="474c9-254">Verificações de integridade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="474c9-254">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="474c9-255">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="474c9-255">Next steps</span></span>

<span data-ttu-id="474c9-256">Explore o conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="474c9-256">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="474c9-257">Passo a passo 5: Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="474c9-257">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="474c9-258">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="474c9-258">Technical walkthrough availability</span></span>

<span data-ttu-id="474c9-259">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="474c9-259">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="474c9-260">Visão geral</span><span class="sxs-lookup"><span data-stu-id="474c9-260">Overview</span></span>

<span data-ttu-id="474c9-261">Um aplicativo baseado em contêineres do Windows rapidamente precisa usam as plataformas, ainda mais se afastando de VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="474c9-261">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="474c9-262">Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="474c9-262">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="474c9-263">Você pode alcançar essas metas usando o orchestrator Service Fabric do Azure, que está disponível na nuvem do Azure, mas também disponível para uso local, ou até mesmo em uma nuvem pública diferente.</span><span class="sxs-lookup"><span data-stu-id="474c9-263">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="474c9-264">Objetivos</span><span class="sxs-lookup"><span data-stu-id="474c9-264">Goals</span></span>

<span data-ttu-id="474c9-265">É o objetivo deste passo a passo saber como implantar um aplicativo baseado no contêiner do Windows para um cluster do Service Fabric no Azure.</span><span class="sxs-lookup"><span data-stu-id="474c9-265">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="474c9-266">Implantando a malha do serviço do zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="474c9-266">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="474c9-267">Implante um cluster do Service Fabric para o Azure (ou em um ambiente diferente).</span><span class="sxs-lookup"><span data-stu-id="474c9-267">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="474c9-268">Implante o aplicativo e os recursos relacionados ao cluster do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="474c9-268">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="474c9-269">Cenários</span><span class="sxs-lookup"><span data-stu-id="474c9-269">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="474c9-270">Cenário a: implantar diretamente para um cluster do Service Fabric a partir de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="474c9-270">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento](./media/image5-9.png)

> <span data-ttu-id="474c9-272">**Figura 5-9.**</span><span class="sxs-lookup"><span data-stu-id="474c9-272">**Figure 5-9.**</span></span> <span data-ttu-id="474c9-273">Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="474c9-273">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="474c9-274">Cenário b: implantar um cluster do Service Fabric do CI/CD pipelines no Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-274">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="474c9-276">**Figura 5-10.**</span><span class="sxs-lookup"><span data-stu-id="474c9-276">**Figure 5-10.**</span></span> <span data-ttu-id="474c9-277">Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="474c9-277">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="474c9-278">Benefícios</span><span class="sxs-lookup"><span data-stu-id="474c9-278">Benefits</span></span>

<span data-ttu-id="474c9-279">Os benefícios da implantação em um cluster de malha do serviço são semelhantes aos benefícios de usar Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="474c9-279">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="474c9-280">Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção mais maduro para aplicativos do Windows em comparação comparada Kubernetes, que é uma fase de beta para contêineres do Windows em Kubernetes versão 1.9 (de 2017 dezembro).</span><span class="sxs-lookup"><span data-stu-id="474c9-280">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="474c9-281">Kubernetes é um ambiente mais maduro para Linux.</span><span class="sxs-lookup"><span data-stu-id="474c9-281">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="474c9-282">O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="474c9-282">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="474c9-283">Malha do serviço do Azure oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-283">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="474c9-284">Você pode ter uma malha do serviço de cluster no Azure, ou instale-o no local em seu próprio data center.</span><span class="sxs-lookup"><span data-stu-id="474c9-284">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="474c9-285">Até você pode instalar um cluster do Service Fabric em uma nuvem diferente, como [AWS Amazon](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="474c9-285">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="474c9-286">Com o Service Fabric, os desenvolvedores podem progresso da ideia sobre máquinas físicas e virtuais para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="474c9-286">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="474c9-287">Aplicativos com base em vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="474c9-287">Applications based on multiple containers.</span></span>

- <span data-ttu-id="474c9-288">Replicação de instâncias de contêiner e dimensionamento automático horizontal.</span><span class="sxs-lookup"><span data-stu-id="474c9-288">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="474c9-289">Nomenclatura e descoberta (por exemplo, DNS interno).</span><span class="sxs-lookup"><span data-stu-id="474c9-289">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="474c9-290">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="474c9-290">Balancing loads.</span></span>

- <span data-ttu-id="474c9-291">Implantar atualizações.</span><span class="sxs-lookup"><span data-stu-id="474c9-291">Rolling updates.</span></span>

- <span data-ttu-id="474c9-292">Distribuindo segredos.</span><span class="sxs-lookup"><span data-stu-id="474c9-292">Distributing secrets.</span></span>

- <span data-ttu-id="474c9-293">Verifica a integridade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="474c9-293">Application health checks.</span></span>

<span data-ttu-id="474c9-294">Os seguintes recursos são exclusivos na malha do serviço (em comparação com outras orchestrators):</span><span class="sxs-lookup"><span data-stu-id="474c9-294">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="474c9-295">Recurso de serviços com monitoração de estado, por meio do modelo de aplicativo de serviços confiáveis.</span><span class="sxs-lookup"><span data-stu-id="474c9-295">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="474c9-296">Padrão de atores, por meio do modelo de aplicativo de atores confiável.</span><span class="sxs-lookup"><span data-stu-id="474c9-296">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="474c9-297">Implante bare bone processos, além de contêineres do Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="474c9-297">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="474c9-298">Atualizações e verificações de integridade avançadas.</span><span class="sxs-lookup"><span data-stu-id="474c9-298">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="474c9-299">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="474c9-299">Next steps</span></span>

<span data-ttu-id="474c9-300">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="474c9-300">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="474c9-301">[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Próximo](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="474c9-301">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
