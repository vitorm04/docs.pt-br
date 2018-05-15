---
title: Explicações passo a passo e technical obter a visão geral de Introdução
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Explicações passo a passo e technical obter a visão geral de Introdução
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="736fd-103">Explicações passo a passo e technical obter a visão geral de Introdução</span><span class="sxs-lookup"><span data-stu-id="736fd-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="736fd-104">Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="736fd-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="736fd-105">A série online de instruções passo a passo é descrita neste capítulo aborda a instalação passo a passo de vários ambientes baseados em contêineres do Windows e a implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="736fd-106">As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="736fd-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="736fd-107">Você pode obter instruções passo a passo em si no *eShopModernizing* aplicativos wiki de repositório do GitHub em [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="736fd-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="736fd-108">Lista de instruções passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-108">Technical walkthrough list</span></span>

<span data-ttu-id="736fd-109">Orientações iniciada por get a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo de comparação de precisão e shift usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="736fd-110">Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de amostra, que estão disponíveis no GitHub em [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="736fd-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="736fd-111">**Tour de eShop herdados aplicativos (aplicativos de linha de base para modernizar)**</span><span class="sxs-lookup"><span data-stu-id="736fd-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="736fd-112">**Coloca seus aplicativos web ASP.NET existentes (WebForms & MVC) com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="736fd-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="736fd-113">**Coloca os serviços do WCF (aplicativos de N camadas) existentes com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="736fd-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="736fd-114">**Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="736fd-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="736fd-115">**Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure**</span><span class="sxs-lookup"><span data-stu-id="736fd-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="736fd-116">**Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="736fd-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="736fd-117">Passo a passo 1: Tour aplicativos herdados eShop</span><span class="sxs-lookup"><span data-stu-id="736fd-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="736fd-118">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-118">Technical walkthrough availability</span></span>

<span data-ttu-id="736fd-119">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="736fd-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="736fd-120">explicações passo a passo do eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="736fd-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="736fd-121">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-121">Overview</span></span>

<span data-ttu-id="736fd-122">Neste passo a passo, você pode explorar a implementação inicial de três aplicativos herdados de exemplo.</span><span class="sxs-lookup"><span data-stu-id="736fd-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="736fd-123">Os aplicativos de web de exemplo dois primeiros têm uma arquitetura monolítica e foram criados usando o ASP.NET clássico.</span><span class="sxs-lookup"><span data-stu-id="736fd-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="736fd-124">Um aplicativo é baseado no ASP.NET 4. x MVC; o segundo aplicativo é baseado em Web Forms do ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="736fd-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="736fd-125">O aplicativo de terceiro é um aplicativo de camada 3 composto por um aplicativo de WinForms de cliente e um servidor [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) serviço.</span><span class="sxs-lookup"><span data-stu-id="736fd-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="736fd-126">Todos esses aplicativos estão disponíveis no [eShopModernizing do repositório GitHub](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="736fd-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-127">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-127">Goals</span></span>

<span data-ttu-id="736fd-128">O objetivo principal deste passo a passo é apenas para se familiarizar com esses aplicativos e seu código e configuração.</span><span class="sxs-lookup"><span data-stu-id="736fd-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="736fd-129">Você pode configurar os aplicativos para que eles gerarem e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="736fd-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="736fd-130">Essa configuração opcional baseia-se na injeção de dependência, de modo separado.</span><span class="sxs-lookup"><span data-stu-id="736fd-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="736fd-131">Cenário 1: Aplicativos da Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="736fd-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="736fd-132">A figura a seguir mostra um cenário simples que aplicativos herdados original de web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="736fd-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Cenário de arquitetura simples aplicativos herdados original de web do ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="736fd-134">De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="736fd-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="736fd-135">Membros da equipe do enterprise eShop usaria o aplicativo para exibir e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="736fd-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="736fd-136">A figura a seguir mostra as capturas de tela inicial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-136">The next figure shows the initial app screenshots.</span></span>

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)](./media/image5-2.png)

<span data-ttu-id="736fd-138">Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET MVC de núcleo.</span><span class="sxs-lookup"><span data-stu-id="736fd-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="736fd-139">Cenário 2: Serviço do WCF e o aplicativo cliente do WinForms (aplicativo da camada 3)</span><span class="sxs-lookup"><span data-stu-id="736fd-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="736fd-140">A figura a seguir mostra um cenário simples com o aplicativo herdado de 3 camadas original.</span><span class="sxs-lookup"><span data-stu-id="736fd-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Cenário de arquitetura simples do aplicativo de camada 3 herdado original com um serviço WCF e um aplicativo cliente do WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="736fd-142">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-142">Benefits</span></span>

<span data-ttu-id="736fd-143">Os benefícios deste passo a passo são simples: basta se familiarizar com o código e aplicativos inicias.</span><span class="sxs-lookup"><span data-stu-id="736fd-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="736fd-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-144">Next steps</span></span>

<span data-ttu-id="736fd-145">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="736fd-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="736fd-146">Tour na linha de base ASP.NET MVC e aplicativos "herdados" do Web Forms</span><span class="sxs-lookup"><span data-stu-id="736fd-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="736fd-147">Tour sobre o serviço do WCF de linha de base e o aplicativo "herdado" do WinForms (camada 3)</span><span class="sxs-lookup"><span data-stu-id="736fd-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="736fd-148">Passo a passo 2: Coloca seus aplicativos existentes do .NET com contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="736fd-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="736fd-149">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-149">Overview</span></span>

<span data-ttu-id="736fd-150">Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, formulários da Web ou WCF, para ambientes de teste, desenvolvimento e produção.</span><span class="sxs-lookup"><span data-stu-id="736fd-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-151">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-151">Goals</span></span>

<span data-ttu-id="736fd-152">O objetivo deste passo a passo é mostrar a você diversas opções para containerizing um aplicativo existente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="736fd-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="736fd-153">Você pode:</span><span class="sxs-lookup"><span data-stu-id="736fd-153">You can:</span></span>

- <span data-ttu-id="736fd-154">Coloca o seu aplicativo usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (2017 do Visual Studio ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="736fd-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="736fd-155">Coloca o seu aplicativo manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="736fd-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="736fd-156">Coloca o seu aplicativo usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (um código-fonte aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="736fd-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="736fd-157">Este passo a passo enfoca o Visual Studio Tools 2017 abordagem Docker, mas as duas abordagens são bastante semelhantes em termos de uso Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="736fd-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="736fd-158">Cenário 1: Aplicativos de web do ASP.NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="736fd-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="736fd-159">A figura abaixo mostra o cenário para os aplicativos de aplicativos web herdados eShop em contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagrama de arquitetura simplificada de em contêineres de aplicativos ASP.NET em um ambiente de desenvolvimento](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="736fd-161">Cenário 2: Serviço do WCF em contêineres</span><span class="sxs-lookup"><span data-stu-id="736fd-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="736fd-162">A figura abaixo mostra o cenário para um aplicativo de camada 3 com um serviço WCF em contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Diagrama da arquitetura do serviço do WCF em contêineres em um ambiente de desenvolvimento de simplificado](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="736fd-164">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-164">Benefits</span></span>

<span data-ttu-id="736fd-165">Há vantagens para executar seu aplicativo monolítico em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="736fd-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="736fd-166">Primeiro, crie uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-166">First, you create an image for the application.</span></span> <span data-ttu-id="736fd-167">Daí em diante, cada implantação é executado no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="736fd-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="736fd-168">Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instalado, usa a mesma versão do framework .NET e é criado usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="736fd-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="736fd-169">Basicamente, você deve controlar as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="736fd-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="736fd-170">As dependências de viagem com o aplicativo ao implantar os contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="736fd-171">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="736fd-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="736fd-172">Problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de ter em um ambiente de preparo ou produção.</span><span class="sxs-lookup"><span data-stu-id="736fd-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="736fd-173">Diferenças nos ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="736fd-174">Aplicativos em contêineres também têm uma curva mais simples de expansão.</span><span class="sxs-lookup"><span data-stu-id="736fd-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="736fd-175">Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo comum por máquina.</span><span class="sxs-lookup"><span data-stu-id="736fd-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="736fd-176">Isso resulta em maior densidade e menos necessários recursos, especialmente quando você usar orchestrators como Kubernetes ou do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="736fd-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="736fd-177">Enormemente, em situações ideais, não exige a fazer alterações no código do aplicativo (C\#).</span><span class="sxs-lookup"><span data-stu-id="736fd-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="736fd-178">Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e compor Docker).</span><span class="sxs-lookup"><span data-stu-id="736fd-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="736fd-179">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-179">Next steps</span></span>

<span data-ttu-id="736fd-180">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="736fd-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="736fd-181">Como coloca os aplicativos da web do .NET Framework com contêineres do Windows e o Docker</span><span class="sxs-lookup"><span data-stu-id="736fd-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="736fd-182">Adicionando suporte de Docker para um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="736fd-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="736fd-183">Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="736fd-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="736fd-184">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-184">Technical walkthrough availability</span></span>

<span data-ttu-id="736fd-185">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="736fd-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="736fd-186">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-186">Overview</span></span>

<span data-ttu-id="736fd-187">A implantação para um host Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite configurar rapidamente ambientes de teste/desenvolvimento/teste.</span><span class="sxs-lookup"><span data-stu-id="736fd-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="736fd-188">Ele também fornece um local comum para testadores ou usuários de negócios validar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="736fd-189">Máquinas virtuais também podem ser infra-estrutura válida como ambientes de produção de serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="736fd-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-190">Goals</span></span>

<span data-ttu-id="736fd-191">O objetivo deste passo a passo é mostrar a você as várias alternativas que ao implantar contêineres do Windows em máquinas virtuais do Azure que são baseados no Windows Server 2016 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="736fd-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="736fd-192">Cenários</span><span class="sxs-lookup"><span data-stu-id="736fd-192">Scenarios</span></span>

<span data-ttu-id="736fd-193">Vários cenários são abordados neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="736fd-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="736fd-194">Cenário a: implantar para uma VM do Azure a partir de um computador de desenvolvimento por meio de conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="736fd-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

> <span data-ttu-id="736fd-196">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="736fd-196">**Figure 5-4.**</span></span> <span data-ttu-id="736fd-197">Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="736fd-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="736fd-198">Cenário b: implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="736fd-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

> <span data-ttu-id="736fd-200">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="736fd-200">**Figure 5-5.**</span></span> <span data-ttu-id="736fd-201">Implantar uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="736fd-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="736fd-202">Cenário c: implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services](./media/image5-6.png)

> <span data-ttu-id="736fd-204">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="736fd-204">**Figure 5-6.**</span></span> <span data-ttu-id="736fd-205">Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-205">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="736fd-206">Máquinas virtuais do Azure para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="736fd-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="736fd-207">Máquinas virtuais do Azure para contêineres do Windows são VMs com base no Windows Server 2016, o Windows 10 ou versões posteriores, ambos com o mecanismo do Docker configurado.</span><span class="sxs-lookup"><span data-stu-id="736fd-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="736fd-208">Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="736fd-209">Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**.</span><span class="sxs-lookup"><span data-stu-id="736fd-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="736fd-210">Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou Nano Server do Windows.</span><span class="sxs-lookup"><span data-stu-id="736fd-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="736fd-211">Imagens de contêiner do sistema operacional estão instaladas e, em seguida, a máquina virtual está pronta para uso com o Docker.</span><span class="sxs-lookup"><span data-stu-id="736fd-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="736fd-212">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-212">Benefits</span></span>

<span data-ttu-id="736fd-213">Embora os contêineres do Windows podem ser implantados em VMs do local no Windows Server 2016, quando você implanta no Azure, você obterá uma maneira fácil de começar, prontos para uso VMs de contêiner do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="736fd-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="736fd-214">Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de escala de máquina virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="736fd-215">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-215">Next steps</span></span>

<span data-ttu-id="736fd-216">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="736fd-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="736fd-217">Passo a passo 4: Implantar seus aplicativos com base em contêineres do Windows para instâncias de contêiner do Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="736fd-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="736fd-218">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-218">Technical walkthrough availability</span></span>

<span data-ttu-id="736fd-219">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="736fd-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="736fd-220">[Implantar os aplicativos para ACI (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="736fd-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="736fd-221">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-221">Overview</span></span>

<span data-ttu-id="736fd-222">[Instâncias de contêiner do Azure (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) é a maneira mais rápida para ter um ambiente de teste/desenvolvimento/teste contêineres onde você pode implantar instâncias únicas de contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-223">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-223">Goals</span></span>

<span data-ttu-id="736fd-224">Este passo a passo mostra os cenários principais ao implantar contêineres do Windows para instâncias de contêiner do Azure (ACI) e como você pode implantar aplicativos eShopModernizing em ACI.</span><span class="sxs-lookup"><span data-stu-id="736fd-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="736fd-225">Cenários</span><span class="sxs-lookup"><span data-stu-id="736fd-225">Scenarios</span></span>

<span data-ttu-id="736fd-226">Pode haver variações sobre como implantar os aplicativos eShopModernizing em ACI como implantar um ou todos os aplicativos (aplicativo MVC, o aplicativo de formulários da Web ou serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="736fd-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="736fd-227">No cenário a seguir mostrado abaixo, você pode ver o aplicativo ASP.NET MVC e o contêiner do SQL Server deles implantadas como contêineres para ACI (instâncias de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="736fd-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Implantar em ACI de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="736fd-229">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-229">Benefits</span></span>

<span data-ttu-id="736fd-230">Instâncias de contêiner do Azure torna fácil criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior.</span><span class="sxs-lookup"><span data-stu-id="736fd-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="736fd-231">Com ACI, diretamente você pode implantar um contêiner do Windows Azure e expô-lo com a internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro de Docker como o Hub do Docker ou do contêiner do Azure Registro).</span><span class="sxs-lookup"><span data-stu-id="736fd-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="736fd-232">Considerações</span><span class="sxs-lookup"><span data-stu-id="736fd-232">Considerations</span></span>

<span data-ttu-id="736fd-233">Implantar contêineres do Windows com o .NET Framework completo não é muito mais rápido implantando em um Host Docker regular (como um Windows Server 2016 com contêineres do Windows) como a imagem do Docker precisa ser ASP.NET ou do SQL Server em instâncias de contêiner do Azure (ACI) baixados (desconectado do registro do Docker) sempre e os tamanhos de imagem de contêiner SQL (15.1 GB) e a imagem de contêiner do ASP.NET (13.9 GB) são muito grandes, no entanto, é muito mais barato do que manter seu próprio host docker (permanentemente on-line Windows Server 2016 com a VM de contêineres do Windows no Azure) para não mencionar um orquestrador de inteiro como Kubernetes no Azure (AKS/ACS) ou Service Fabric do Azure que são, por outro lado, excelentes opções para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="736fd-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="736fd-234">Como principal conclusão, usando as instâncias de contêiner do Azure é uma opção muito convincente para cenários de desenvolvimento/teste em pipelines de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="736fd-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="736fd-235">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-235">Next steps</span></span>

<span data-ttu-id="736fd-236">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="736fd-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="736fd-237">Passo a passo 5: Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="736fd-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="736fd-238">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-238">Technical walkthrough availability</span></span>

<span data-ttu-id="736fd-239">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="736fd-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="736fd-240">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-240">Overview</span></span>

<span data-ttu-id="736fd-241">Um aplicativo baseado em contêineres do Windows precisará rapidamente usam as plataformas, ainda mais se afastando de VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="736fd-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="736fd-242">Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="736fd-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="736fd-243">Você pode atingir essas metas, usando o orchestrator [Kubernetes](https://kubernetes.io/), disponível em [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="736fd-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-244">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-244">Goals</span></span>

<span data-ttu-id="736fd-245">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado no contêiner do Windows para Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="736fd-246">Implantando a Kubernetes de zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="736fd-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="736fd-247">Implante um cluster de Kubernetes para serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="736fd-248">Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="736fd-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="736fd-249">Cenários</span><span class="sxs-lookup"><span data-stu-id="736fd-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="736fd-250">Cenário a: a implantar diretamente a um cluster de Kubernetes a partir de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="736fd-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

> <span data-ttu-id="736fd-252">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="736fd-252">**Figure 5-7.**</span></span> <span data-ttu-id="736fd-253">Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="736fd-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="736fd-254">Cenário b: implantar um cluster Kubernetes do CI/CD pipelines no Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services](./media/image5-8.png)

> <span data-ttu-id="736fd-256">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="736fd-256">**Figure 5-8.**</span></span> <span data-ttu-id="736fd-257">Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="736fd-258">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-258">Benefits</span></span>

<span data-ttu-id="736fd-259">Há muitos benefícios à implantação em um cluster em Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="736fd-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="736fd-260">O maior benefício é que você obtenha um ambiente pronto para produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e com base no número de nós ou VMs no (cluster escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="736fd-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="736fd-261">Serviço de contêiner do Azure otimiza tecnologias e ferramentas de código aberto populares especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="736fd-262">Você obtém uma solução aberta que oferece portabilidade, para os contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="736fd-263">Selecione o tamanho, o número de hosts, e o contêiner de ferramentas orchestrator serviço controla todo o resto.</span><span class="sxs-lookup"><span data-stu-id="736fd-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="736fd-264">Kubernetes, os desenvolvedores podem passam da ideia sobre máquinas físicas e virtuais, para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="736fd-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="736fd-265">Aplicativos com base em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="736fd-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="736fd-266">Replicação de instâncias de contêiner e o dimensionamento automático horizontal</span><span class="sxs-lookup"><span data-stu-id="736fd-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="736fd-267">Nomenclatura e descobrir (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="736fd-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="736fd-268">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="736fd-268">Balancing loads</span></span>

- <span data-ttu-id="736fd-269">Atualizações móveis</span><span class="sxs-lookup"><span data-stu-id="736fd-269">Rolling updates</span></span>

- <span data-ttu-id="736fd-270">Distribuindo segredos</span><span class="sxs-lookup"><span data-stu-id="736fd-270">Distributing secrets</span></span>

- <span data-ttu-id="736fd-271">Verificações de integridade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="736fd-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="736fd-272">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-272">Next steps</span></span>

<span data-ttu-id="736fd-273">Explore o conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="736fd-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="736fd-274">Passo a passo 6: Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="736fd-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="736fd-275">Disponibilidade do passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="736fd-275">Technical walkthrough availability</span></span>

<span data-ttu-id="736fd-276">Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="736fd-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="736fd-277">Visão geral</span><span class="sxs-lookup"><span data-stu-id="736fd-277">Overview</span></span>

<span data-ttu-id="736fd-278">Um aplicativo baseado em contêineres do Windows rapidamente precisa usam as plataformas, ainda mais se afastando de VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="736fd-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="736fd-279">Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="736fd-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="736fd-280">Você pode alcançar essas metas usando o orchestrator Service Fabric do Azure, que está disponível na nuvem do Azure, mas também disponível para uso local, ou até mesmo em uma nuvem pública diferente.</span><span class="sxs-lookup"><span data-stu-id="736fd-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="736fd-281">Objetivos</span><span class="sxs-lookup"><span data-stu-id="736fd-281">Goals</span></span>

<span data-ttu-id="736fd-282">É o objetivo deste passo a passo saber como implantar um aplicativo baseado no contêiner do Windows para um cluster do Service Fabric no Azure.</span><span class="sxs-lookup"><span data-stu-id="736fd-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="736fd-283">Implantando a malha do serviço do zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="736fd-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="736fd-284">Implante um cluster do Service Fabric para o Azure (ou em um ambiente diferente).</span><span class="sxs-lookup"><span data-stu-id="736fd-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="736fd-285">Implante o aplicativo e os recursos relacionados ao cluster do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="736fd-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="736fd-286">Cenários</span><span class="sxs-lookup"><span data-stu-id="736fd-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="736fd-287">Cenário a: implantar diretamente para um cluster do Service Fabric a partir de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="736fd-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento](./media/image5-9.png)

> <span data-ttu-id="736fd-289">**Figura 5-9.**</span><span class="sxs-lookup"><span data-stu-id="736fd-289">**Figure 5-9.**</span></span> <span data-ttu-id="736fd-290">Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="736fd-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="736fd-291">Cenário b: implantar um cluster do Service Fabric do CI/CD pipelines no Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="736fd-293">**Figura 5-10.**</span><span class="sxs-lookup"><span data-stu-id="736fd-293">**Figure 5-10.**</span></span> <span data-ttu-id="736fd-294">Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="736fd-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="736fd-295">Benefícios</span><span class="sxs-lookup"><span data-stu-id="736fd-295">Benefits</span></span>

<span data-ttu-id="736fd-296">Os benefícios da implantação em um cluster de malha do serviço são semelhantes aos benefícios de usar Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="736fd-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="736fd-297">Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção mais maduro para aplicativos do Windows em comparação comparada Kubernetes, que é uma fase de beta para contêineres do Windows em Kubernetes versão 1.9 (de 2017 dezembro).</span><span class="sxs-lookup"><span data-stu-id="736fd-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="736fd-298">Kubernetes é um ambiente mais maduro para Linux.</span><span class="sxs-lookup"><span data-stu-id="736fd-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="736fd-299">O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="736fd-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="736fd-300">Malha do serviço do Azure oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="736fd-301">Você pode ter uma malha do serviço de cluster no Azure, ou instale-o no local em seu próprio data center.</span><span class="sxs-lookup"><span data-stu-id="736fd-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="736fd-302">Até você pode instalar um cluster do Service Fabric em uma nuvem diferente, como [AWS Amazon](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="736fd-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="736fd-303">Com o Service Fabric, os desenvolvedores podem progresso da ideia sobre máquinas físicas e virtuais para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="736fd-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="736fd-304">Aplicativos com base em vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="736fd-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="736fd-305">Replicação de instâncias de contêiner e dimensionamento automático horizontal.</span><span class="sxs-lookup"><span data-stu-id="736fd-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="736fd-306">Nomenclatura e descoberta (por exemplo, DNS interno).</span><span class="sxs-lookup"><span data-stu-id="736fd-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="736fd-307">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="736fd-307">Balancing loads.</span></span>

- <span data-ttu-id="736fd-308">Implantar atualizações.</span><span class="sxs-lookup"><span data-stu-id="736fd-308">Rolling updates.</span></span>

- <span data-ttu-id="736fd-309">Distribuindo segredos.</span><span class="sxs-lookup"><span data-stu-id="736fd-309">Distributing secrets.</span></span>

- <span data-ttu-id="736fd-310">Verifica a integridade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="736fd-310">Application health checks.</span></span>

<span data-ttu-id="736fd-311">Os seguintes recursos são exclusivos na malha do serviço (em comparação com outras orchestrators):</span><span class="sxs-lookup"><span data-stu-id="736fd-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="736fd-312">Recurso de serviços com monitoração de estado, por meio do modelo de aplicativo de serviços confiáveis.</span><span class="sxs-lookup"><span data-stu-id="736fd-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="736fd-313">Padrão de atores, por meio do modelo de aplicativo de atores confiável.</span><span class="sxs-lookup"><span data-stu-id="736fd-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="736fd-314">Implante bare bone processos, além de contêineres do Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="736fd-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="736fd-315">Atualizações e verificações de integridade avançadas.</span><span class="sxs-lookup"><span data-stu-id="736fd-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="736fd-316">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="736fd-316">Next steps</span></span>

<span data-ttu-id="736fd-317">Explore o conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="736fd-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="736fd-318">[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Próximo](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="736fd-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
