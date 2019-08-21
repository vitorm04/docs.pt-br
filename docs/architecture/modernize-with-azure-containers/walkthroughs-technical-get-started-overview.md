---
title: Visão geral de tutoriais passo a passo e introduções técnicas
description: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure | Visão geral de orientações técnicas e de introdução técnica
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660892"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="e76a1-103">Visão geral de tutoriais passo a passo e introduções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="e76a1-104">Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e os passo a passos completos foram disponibilizados em um repositório GitHub.</span><span class="sxs-lookup"><span data-stu-id="e76a1-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="e76a1-105">A série online de instruções explicativas descritas neste capítulo aborda a configuração passo a passo dos vários ambientes baseados em contêineres do Windows e a implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="e76a1-106">As seções a seguir explicam o que envolve cada explicação, seus objetivos e visão de alto nível e fornece um diagrama das tarefas envolvidas.</span><span class="sxs-lookup"><span data-stu-id="e76a1-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="e76a1-107">Você pode obter os passo a passos em si no wiki do repositório GitHub de <https://github.com/dotnet-architecture/eShopModernizing/wiki>aplicativos eShopModernizing em.</span><span class="sxs-lookup"><span data-stu-id="e76a1-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="e76a1-108">Lista de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-108">Technical walkthrough list</span></span>

<span data-ttu-id="e76a1-109">Os seguintes passo a passos de introdução fornecem diretrizes técnicas consistentes e abrangentes para aplicativos de exemplo que podem ser movidos e deslocados usando contêineres e, em seguida, se movem usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="e76a1-110">Cada uma das orientações a seguir usa os novos aplicativos de exemplo eShopLegacy e eShopModernizing, que estão disponíveis no GitHub <https://github.com/dotnet-architecture/eShopModernizing>em.</span><span class="sxs-lookup"><span data-stu-id="e76a1-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="e76a1-111">**Tour dos aplicativos herdados eShop (aplicativos de linha de base para modernizar)**</span><span class="sxs-lookup"><span data-stu-id="e76a1-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="e76a1-112">**Colocar em contêineres seus aplicativos Web ASP.NET existentes (WebForms & MVC) com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="e76a1-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="e76a1-113">**Colocar em contêineres seus serviços WCF existentes (aplicativos de N camadas) com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="e76a1-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="e76a1-114">**Implantar seu aplicativo baseado em contêineres do Windows em VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="e76a1-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="e76a1-115">**Implantar seus aplicativos baseados em contêineres do Windows no kubernetes no serviço de contêiner do Azure**</span><span class="sxs-lookup"><span data-stu-id="e76a1-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="e76a1-116">Walkthrough 1: Tour dos aplicativos herdados do eShop</span><span class="sxs-lookup"><span data-stu-id="e76a1-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="e76a1-117">Disponibilidade de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-117">Technical walkthrough availability</span></span>

<span data-ttu-id="e76a1-118">A explicação técnica completa está disponível no wiki do repositório GitHub do eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="e76a1-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="e76a1-119">passo a passos do eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="e76a1-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="e76a1-120">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-120">Overview</span></span>

<span data-ttu-id="e76a1-121">Neste tutorial, você pode explorar a implementação inicial de três aplicativos herdados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="e76a1-122">Os dois primeiros aplicativos Web de exemplo têm uma arquitetura monolítica e foram criados usando ASP.NET clássicas.</span><span class="sxs-lookup"><span data-stu-id="e76a1-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="e76a1-123">Um aplicativo é baseado em ASP.NET 4. x MVC; o segundo aplicativo é baseado em Web Forms ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="e76a1-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="e76a1-124">O terceiro aplicativo é um aplicativo de três camadas composto por um aplicativo WinForms cliente e um serviço de Windows Communication Foundation do lado do servidor [(WCF)](../../framework/wcf/whats-wcf.md) .</span><span class="sxs-lookup"><span data-stu-id="e76a1-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="e76a1-125">Todos esses aplicativos estão disponíveis no [repositório GitHub do eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="e76a1-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-126">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-126">Goals</span></span>

<span data-ttu-id="e76a1-127">A principal meta deste passo a passo é simplesmente se familiarizar com esses aplicativos e com seu código e configuração.</span><span class="sxs-lookup"><span data-stu-id="e76a1-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="e76a1-128">Você pode configurar os aplicativos para que eles gerem e usem dados fictícios, sem usar o banco de dado SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="e76a1-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="e76a1-129">Essa configuração opcional é baseada na injeção de dependência, de forma desacoplada.</span><span class="sxs-lookup"><span data-stu-id="e76a1-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="e76a1-130">Cenário 1: Aplicativos Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e76a1-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="e76a1-131">A figura a seguir mostra o cenário simples dos aplicativos Web ASP.NET herdados originais.</span><span class="sxs-lookup"><span data-stu-id="e76a1-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Cenário de arquitetura simples dos aplicativos Web ASP.NET herdados originais](./media/image5-1.png)

<span data-ttu-id="e76a1-133">De uma perspectiva de domínio de negócios, ambos os aplicativos oferecem os mesmos recursos de gerenciamento de catálogo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="e76a1-134">Os membros da equipe do eShop Enterprise usariam o aplicativo para exibir e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="e76a1-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="e76a1-135">A próxima figura mostra as capturas de tela iniciais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC e ASP.NET Web Forms aplicativos (tecnologias existentes/herdadas)](./media/image5-2.png)

<span data-ttu-id="e76a1-137">Dependências no ASP.NET 4. x ou versões anteriores (para MVC ou para Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código seja totalmente reescrito usando ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="e76a1-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="e76a1-138">Cenário 2: Serviço WCF e aplicativo cliente WinForms (aplicativo de três camadas)</span><span class="sxs-lookup"><span data-stu-id="e76a1-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="e76a1-139">A figura a seguir mostra o cenário simples do aplicativo herdado de três camadas original.</span><span class="sxs-lookup"><span data-stu-id="e76a1-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Cenário de arquitetura simples do aplicativo de três camadas herdado original com um serviço WCF e um aplicativo cliente WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="e76a1-141">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-141">Benefits</span></span>

<span data-ttu-id="e76a1-142">Os benefícios deste passo a passos são simples: Familiarize-se apenas com o código e os aplicativos iniciais.</span><span class="sxs-lookup"><span data-stu-id="e76a1-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="e76a1-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-143">Next steps</span></span>

<span data-ttu-id="e76a1-144">Explore este conteúdo mais detalhadamente no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="e76a1-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="e76a1-145">Tour na linha de base ASP.NET MVC e Web Forms aplicativos "herdados"</span><span class="sxs-lookup"><span data-stu-id="e76a1-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="e76a1-146">Tour no serviço WCF de linha de base e no aplicativo WinForms (3 camadas) "herdado"</span><span class="sxs-lookup"><span data-stu-id="e76a1-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="e76a1-147">Walkthrough 2: Colocar em contêineres seus aplicativos .NET existentes com contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="e76a1-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="e76a1-148">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-148">Overview</span></span>

<span data-ttu-id="e76a1-149">Use contêineres do Windows para aprimorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, Web Forms ou WCF, para ambientes de produção, desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="e76a1-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-150">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-150">Goals</span></span>

<span data-ttu-id="e76a1-151">O objetivo deste passo a passo é mostrar várias opções para o contêiner de um aplicativo .NET Framework existente.</span><span class="sxs-lookup"><span data-stu-id="e76a1-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="e76a1-152">Você pode:</span><span class="sxs-lookup"><span data-stu-id="e76a1-152">You can:</span></span>

- <span data-ttu-id="e76a1-153">Colocar seu aplicativo em contêiner usando as [Ferramentas do visual studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual Studio 2017 ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="e76a1-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="e76a1-154">Colocar seu aplicativo em contêiner Adicionando manualmente um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando a [CLI](https://docs.docker.com/engine/reference/commandline/cli/)do Docker.</span><span class="sxs-lookup"><span data-stu-id="e76a1-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="e76a1-155">Colocar seu aplicativo em contêiner usando a ferramenta [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (uma ferramenta de código-fonte aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="e76a1-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="e76a1-156">Este tutorial explica a abordagem das ferramentas do Visual Studio 2017 para Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso de Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="e76a1-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="e76a1-157">Cenário 1: Aplicativos Web ASP.NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="e76a1-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="e76a1-158">A figura abaixo mostra o cenário para aplicativos de aplicativos Web herdados do eShop em contêineres.</span><span class="sxs-lookup"><span data-stu-id="e76a1-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagrama de arquitetura simplificado de aplicativos ASP.NET em contêineres em um ambiente de desenvolvimento](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="e76a1-160">Cenário 2: Serviço WCF em contêineres</span><span class="sxs-lookup"><span data-stu-id="e76a1-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="e76a1-161">A figura abaixo mostra o cenário para um aplicativo de três camadas com um serviço WCF em contêiner.</span><span class="sxs-lookup"><span data-stu-id="e76a1-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagrama de arquitetura simplificado do serviço WCF em contêineres em um ambiente de desenvolvimento](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="e76a1-163">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-163">Benefits</span></span>

<span data-ttu-id="e76a1-164">Há vantagens em executar seu aplicativo monolítico em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="e76a1-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="e76a1-165">Primeiro, você cria uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-165">First, you create an image for the application.</span></span> <span data-ttu-id="e76a1-166">Desse ponto em diante, cada implantação é executada no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="e76a1-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="e76a1-167">Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instaladas, usa a mesma versão do .NET Framework e é criado usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="e76a1-168">Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="e76a1-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="e76a1-169">As dependências viajam com o aplicativo quando você implanta os contêineres.</span><span class="sxs-lookup"><span data-stu-id="e76a1-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="e76a1-170">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente fornecido pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="e76a1-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="e76a1-171">Os problemas que aparecem apenas com determinadas versões podem ser exibidos imediatamente, em vez de identificando em um ambiente de preparo ou de produção.</span><span class="sxs-lookup"><span data-stu-id="e76a1-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="e76a1-172">As diferenças em ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menos quando os aplicativos são executados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="e76a1-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="e76a1-173">Os aplicativos em contêineres também têm uma curva de expansão Flatter.</span><span class="sxs-lookup"><span data-stu-id="e76a1-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="e76a1-174">Os aplicativos em contêineres permitem que você tenha mais instâncias de aplicativo e de serviço (com base em contêineres) em uma VM ou máquina física em comparação com implantações regulares de aplicativos por máquina.</span><span class="sxs-lookup"><span data-stu-id="e76a1-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="e76a1-175">Isso se traduz em maior densidade e menos recursos necessários, especialmente quando você usa orquestradores como kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e76a1-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="e76a1-176">A criação de contêineres, nas situações ideais, não requer nenhuma alteração no código do aplicativo (\#C).</span><span class="sxs-lookup"><span data-stu-id="e76a1-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="e76a1-177">Na maioria dos cenários, você só precisa dos arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="e76a1-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="e76a1-178">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-178">Next steps</span></span>

<span data-ttu-id="e76a1-179">Explore este conteúdo mais detalhadamente no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="e76a1-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="e76a1-180">Como colocar o .NET Framework aplicativos Web em contêineres com contêineres do Windows e Docker</span><span class="sxs-lookup"><span data-stu-id="e76a1-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="e76a1-181">Adicionando suporte ao Docker a um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="e76a1-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="e76a1-182">Walkthrough 3: Implantar seu aplicativo baseado em contêineres do Windows em VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="e76a1-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="e76a1-183">Disponibilidade de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-183">Technical walkthrough availability</span></span>

<span data-ttu-id="e76a1-184">A explicação técnica completa está disponível no wiki do repositório GitHub do eShopModernizing:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="e76a1-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="e76a1-185">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-185">Overview</span></span>

<span data-ttu-id="e76a1-186">A implantação em um host do Docker em uma VM (máquina virtual) do Windows Server 2016 no Azure permite que você configure rapidamente ambientes de desenvolvimento/teste/preparo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="e76a1-187">Ele também oferece um lugar comum para os testadores ou usuários empresariais validarem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="e76a1-188">As VMs também podem ser ambientes de produção de IaaS (infraestrutura como serviço) válidos.</span><span class="sxs-lookup"><span data-stu-id="e76a1-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-189">Goals</span></span>

<span data-ttu-id="e76a1-190">O objetivo deste passo a passo é mostrar as várias alternativas que você tem ao implantar contêineres do Windows em VMs do Azure baseadas no Windows Server 2016 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="e76a1-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="e76a1-191">Cenários</span><span class="sxs-lookup"><span data-stu-id="e76a1-191">Scenarios</span></span>

<span data-ttu-id="e76a1-192">Vários cenários são abordados neste passo a passos.</span><span class="sxs-lookup"><span data-stu-id="e76a1-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="e76a1-193">Cenário A: Implantar em uma VM do Azure de um PC de desenvolvimento por meio da conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="e76a1-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em uma VM do Azure de um PC de desenvolvimento por meio de uma conexão de mecanismo do Docker](./media/image5-4.png)

<span data-ttu-id="e76a1-195">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="e76a1-195">**Figure 5-4.**</span></span> <span data-ttu-id="e76a1-196">Implantar em uma VM do Azure de um PC de desenvolvimento por meio de uma conexão de mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="e76a1-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="e76a1-197">Cenário B: Implantar em uma VM do Azure por meio de um registro do Docker</span><span class="sxs-lookup"><span data-stu-id="e76a1-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar em uma VM do Azure por meio de um registro do Docker](./media/image5-5.png)

<span data-ttu-id="e76a1-199">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="e76a1-199">**Figure 5-5.**</span></span> <span data-ttu-id="e76a1-200">Implantar em uma VM do Azure por meio de um registro do Docker</span><span class="sxs-lookup"><span data-stu-id="e76a1-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="e76a1-201">Cenário C: Implantar em uma VM do Azure de pipelines de CI/CD no Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e76a1-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em uma VM do Azure de pipelines de CI/CD no Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="e76a1-203">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="e76a1-203">**Figure 5-6.**</span></span> <span data-ttu-id="e76a1-204">Implantar em uma VM do Azure de pipelines de CI/CD no Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e76a1-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="e76a1-205">VMs do Azure para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="e76a1-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="e76a1-206">As VMs do Azure para contêineres do Windows são VMs baseadas no Windows Server 2016, Windows 10 ou versões posteriores, com o mecanismo do Docker configurado.</span><span class="sxs-lookup"><span data-stu-id="e76a1-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="e76a1-207">Na maioria dos casos, o Windows Server 2016 é usado nas VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="e76a1-208">Atualmente, o Azure fornece uma VM chamada **Windows Server 2016 com contêineres**.</span><span class="sxs-lookup"><span data-stu-id="e76a1-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="e76a1-209">Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou o Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="e76a1-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="e76a1-210">As imagens do sistema operacional do contêiner são instaladas e, em seguida, a VM está pronta para ser usada com o Docker.</span><span class="sxs-lookup"><span data-stu-id="e76a1-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="e76a1-211">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-211">Benefits</span></span>

<span data-ttu-id="e76a1-212">Embora os contêineres do Windows possam ser implantados em VMs do Windows Server 2016 locais, quando você implanta no Azure, você obtém uma maneira mais fácil de começar, com VMs de contêiner do Windows Server prontas para uso.</span><span class="sxs-lookup"><span data-stu-id="e76a1-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="e76a1-213">Você também obtém um local online comum que é acessível aos testadores e escalabilidade automática por meio de conjuntos de dimensionamento de máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="e76a1-214">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-214">Next steps</span></span>

<span data-ttu-id="e76a1-215">Explore este conteúdo mais detalhadamente no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="e76a1-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="e76a1-216">Walkthrough 4: Implantar seus aplicativos baseados em contêineres do Windows em ACI (instâncias de contêiner do Azure)</span><span class="sxs-lookup"><span data-stu-id="e76a1-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="e76a1-217">Disponibilidade de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-217">Technical walkthrough availability</span></span>

<span data-ttu-id="e76a1-218">A explicação técnica completa está disponível no wiki do repositório GitHub do eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="e76a1-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="e76a1-219">[Implantando os aplicativos no ACI (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="e76a1-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="e76a1-220">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-220">Overview</span></span>

<span data-ttu-id="e76a1-221">[ACI (instâncias de contêiner do Azure)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida de ter um ambiente de desenvolvimento/teste/preparo de contêineres no qual você pode implantar instâncias únicas de contêineres.</span><span class="sxs-lookup"><span data-stu-id="e76a1-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-222">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-222">Goals</span></span>

<span data-ttu-id="e76a1-223">Este passo a passos mostra os principais cenários ao implantar contêineres do Windows em ACI (instâncias de contêiner do Azure) e como você pode implantar aplicativos eShopModernizing no ACI.</span><span class="sxs-lookup"><span data-stu-id="e76a1-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="e76a1-224">Cenários</span><span class="sxs-lookup"><span data-stu-id="e76a1-224">Scenarios</span></span>

<span data-ttu-id="e76a1-225">Pode haver variações sobre a implantação de aplicativos eShopModernizing em ACI, como a implantação de apenas um ou todos os aplicativos (aplicativo MVC, aplicativo WebForms ou serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="e76a1-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="e76a1-226">No cenário a seguir mostrado abaixo, você pode ver o aplicativo ASP.NET MVC mais o contêiner SQL Server ambos implantados como contêineres em ACI (instâncias de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="e76a1-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Implantar no ACI de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="e76a1-228">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-228">Benefits</span></span>

<span data-ttu-id="e76a1-229">As instâncias de contêiner do Azure facilitam a criação e o gerenciamento de contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais nem de adotar um serviço de nível superior.</span><span class="sxs-lookup"><span data-stu-id="e76a1-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="e76a1-230">Com o ACI, você pode implantar diretamente um contêiner do Windows no Azure e expô-lo à Internet com um FQDN (nome de domínio totalmente qualificado) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro do Docker, como o Hub do Docker ou o contêiner do Azure Registro).</span><span class="sxs-lookup"><span data-stu-id="e76a1-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="e76a1-231">Considerações</span><span class="sxs-lookup"><span data-stu-id="e76a1-231">Considerations</span></span>

<span data-ttu-id="e76a1-232">A implantação de contêineres do Windows com total .NET Framework/ASP.NET ou SQL Server nas instâncias de contêiner do Azure (ACI) não é tão rápida quanto a implantação em um host do Docker regular (como um Windows Server 2016 com contêineres do Windows) porque a imagem do Docker deve ser baixado (extraído do registro do Docker) toda vez e os tamanhos da imagem do contêiner SQL (15,1 GB) e a imagem de contêiner ASP.NET (13,9 GB) são significativamente grandes, no entanto, é muito mais barato do que manter seu próprio host do Docker (permanentemente online O Windows Server 2016 com a VM de contêineres do Windows no Azure) não menciona um orquestrador inteiro como kubernetes no Azure (AKS), que, por outro lado, é uma ótima opção para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="e76a1-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="e76a1-233">Como conclusão principal, o uso de instâncias de contêiner do Azure é uma opção muito atraente para cenários de desenvolvimento/teste e para pipelines de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="e76a1-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e76a1-234">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-234">Next steps</span></span>

<span data-ttu-id="e76a1-235">Explore este conteúdo mais detalhadamente no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="e76a1-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="e76a1-236">Walkthrough 5: Implantar seus aplicativos baseados em contêineres do Windows no kubernetes no serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="e76a1-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="e76a1-237">Disponibilidade de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-237">Technical walkthrough availability</span></span>

<span data-ttu-id="e76a1-238">A explicação técnica completa está disponível no wiki do repositório GitHub do eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="e76a1-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="e76a1-239">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-239">Overview</span></span>

<span data-ttu-id="e76a1-240">Um aplicativo baseado em contêineres do Windows precisará usar rapidamente as plataformas, movendo-se ainda mais longe das VMs IaaS.</span><span class="sxs-lookup"><span data-stu-id="e76a1-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="e76a1-241">Isso é necessário para obter alta escalabilidade e melhor escalabilidade automatizada, e para uma melhoria significativa em implantações e versões automatizadas.</span><span class="sxs-lookup"><span data-stu-id="e76a1-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="e76a1-242">Você pode atingir essas metas usando o Orchestrator [kubernetes](https://kubernetes.io/), disponível nos [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="e76a1-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-243">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-243">Goals</span></span>

<span data-ttu-id="e76a1-244">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows para kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="e76a1-245">A implantação do kubernetes do zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="e76a1-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="e76a1-246">Implante um cluster kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="e76a1-247">Implante o aplicativo e os recursos relacionados ao cluster kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e76a1-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="e76a1-248">Cenários</span><span class="sxs-lookup"><span data-stu-id="e76a1-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="e76a1-249">Cenário A: Implantar diretamente em um cluster kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e76a1-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implantar diretamente em um cluster kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

<span data-ttu-id="e76a1-251">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="e76a1-251">**Figure 5-7.**</span></span> <span data-ttu-id="e76a1-252">Implantar diretamente em um cluster kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="e76a1-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="e76a1-253">Cenário B: Implantar em um cluster kubernetes de pipelines de CI/CD no Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e76a1-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em um cluster kubernetes de pipelines de CI/CD no Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="e76a1-255">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="e76a1-255">**Figure 5-8.**</span></span> <span data-ttu-id="e76a1-256">Implantar em um cluster kubernetes de pipelines de CI/CD no Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e76a1-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="e76a1-257">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-257">Benefits</span></span>

<span data-ttu-id="e76a1-258">Há muitos benefícios em implantar em um cluster no kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e76a1-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="e76a1-259">A maior vantagem é que você obtém um ambiente pronto para produção no qual pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner que deseja usar (escalabilidade interna nos nós existentes) e com base no número de nós ou VMs no cluster ( escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="e76a1-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="e76a1-260">O serviço de contêiner do Azure otimiza ferramentas e tecnologias populares de software livre especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="e76a1-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="e76a1-261">Você Obtém uma solução aberta que oferece portabilidade, tanto para seus contêineres quanto para a configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e76a1-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="e76a1-262">Você seleciona o tamanho, o número de hosts e o serviço de contêiner de ferramentas do Orchestrator lida com todo o resto.</span><span class="sxs-lookup"><span data-stu-id="e76a1-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="e76a1-263">Com o kubernetes, os desenvolvedores podem progredir de pensar em máquinas virtuais e físicas, planejar uma infraestrutura centrada em contêineres que facilite os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="e76a1-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="e76a1-264">Aplicativos baseados em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="e76a1-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="e76a1-265">Replicando instâncias de contêiner e dimensionamento automático horizontal</span><span class="sxs-lookup"><span data-stu-id="e76a1-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="e76a1-266">Nomenclatura e descoberta (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="e76a1-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="e76a1-267">Cargas de balanceamento</span><span class="sxs-lookup"><span data-stu-id="e76a1-267">Balancing loads</span></span>

- <span data-ttu-id="e76a1-268">Atualizações sem interrupção</span><span class="sxs-lookup"><span data-stu-id="e76a1-268">Rolling updates</span></span>

- <span data-ttu-id="e76a1-269">Distribuindo segredos</span><span class="sxs-lookup"><span data-stu-id="e76a1-269">Distributing secrets</span></span>

- <span data-ttu-id="e76a1-270">Verificações de integridade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e76a1-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="e76a1-271">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-271">Next steps</span></span>

<span data-ttu-id="e76a1-272">Explore este conteúdo mais detalhadamente no wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="e76a1-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="e76a1-273">Walkthrough 6: Implantar seus aplicativos baseados em contêineres do Windows no serviço Azure App para contêineres</span><span class="sxs-lookup"><span data-stu-id="e76a1-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="e76a1-274">Disponibilidade de instruções técnicas</span><span class="sxs-lookup"><span data-stu-id="e76a1-274">Technical walkthrough availability</span></span>

<span data-ttu-id="e76a1-275">A explicação técnica completa está disponível no wiki do repositório GitHub do eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="e76a1-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="e76a1-276">Visão geral</span><span class="sxs-lookup"><span data-stu-id="e76a1-276">Overview</span></span>

<span data-ttu-id="e76a1-277">Um aplicativo em contêineres simples usando contêineres do Windows pode ser facilmente implantado para Azure App serviço para contêineres.</span><span class="sxs-lookup"><span data-stu-id="e76a1-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="e76a1-278">Essa é a abordagem recomendada para a maioria dos aplicativos baseados em contêiner do Windows.</span><span class="sxs-lookup"><span data-stu-id="e76a1-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="e76a1-279">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e76a1-279">Goals</span></span>

<span data-ttu-id="e76a1-280">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows para Azure App serviço para contêineres de um registro (Hub do Docker ou registro de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="e76a1-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="e76a1-281">Cenário</span><span class="sxs-lookup"><span data-stu-id="e76a1-281">Scenario</span></span>

![Implantar o aplicativo baseado em contêiner do Windows no serviço Azure App para contêineres](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="e76a1-283">Benefícios</span><span class="sxs-lookup"><span data-stu-id="e76a1-283">Benefits</span></span>

<span data-ttu-id="e76a1-284">A implantação no serviço de Azure App para contêineres oferece os benefícios dos contêineres emparelhados com os benefícios de PaaS do serviço Azure App.</span><span class="sxs-lookup"><span data-stu-id="e76a1-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="e76a1-285">O serviço de aplicativo pode ser facilmente dimensionado vertical e horizontalmente e pode ser configurado para dimensionamento automático para atender às demandas em constante mudança.</span><span class="sxs-lookup"><span data-stu-id="e76a1-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="e76a1-286">As atualizações podem ser executadas com zero tempo de inatividade e a configuração da implantação contínua de um registro também é facilmente configurada.</span><span class="sxs-lookup"><span data-stu-id="e76a1-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e76a1-287">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e76a1-287">Next steps</span></span>

<span data-ttu-id="e76a1-288">Explore este conteúdo mais detalhadamente no wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="e76a1-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e76a1-289">[Anterior](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Próximo](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="e76a1-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
