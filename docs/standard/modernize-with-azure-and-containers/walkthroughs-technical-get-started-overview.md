---
title: Visão geral de tutoriais passo a passo e introduções técnicas
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Instruções passo a passo e técnico obtém visão de geral de Introdução
ms.date: 04/28/2018
ms.openlocfilehash: 0b0dbae999e31150a55368d669f718eea0925d51
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758792"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="3a75e-103">Visão geral de tutoriais passo a passo e introduções técnicas</span><span class="sxs-lookup"><span data-stu-id="3a75e-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="3a75e-104">Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a75e-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="3a75e-105">A série online de instruções passo a passo é descrita neste capítulo aborda a configuração passo a passo de vários ambientes em que se baseiam em contêineres do Windows e a implantação do Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="3a75e-106">As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="3a75e-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="3a75e-107">Você pode obter instruções passo a passo de si mesmos na *eShopModernizing* wiki do repositório de GitHub de aplicativos em <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="3a75e-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="3a75e-108">Passo a passo técnico lista</span><span class="sxs-lookup"><span data-stu-id="3a75e-108">Technical walkthrough list</span></span>

<span data-ttu-id="3a75e-109">Orientações de Introdução a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo que você pode levantar e deslocar usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="3a75e-110">Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de exemplo, que estão disponíveis no GitHub em <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="3a75e-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="3a75e-111">**Tour de aplicativos herdados do eShop (aplicativos de linha de base para modernizar)**</span><span class="sxs-lookup"><span data-stu-id="3a75e-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="3a75e-112">**Colocar seus aplicativos web ASP.NET existentes (WebForms e MVC) em um contêiner com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="3a75e-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="3a75e-113">**Colocar em contêineres seus serviços do WCF (aplicativos de N camadas) existentes com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="3a75e-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="3a75e-114">**Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="3a75e-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="3a75e-115">**Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure**</span><span class="sxs-lookup"><span data-stu-id="3a75e-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="3a75e-116">Passo a passo 1: Tour de aplicativos herdados do eShop</span><span class="sxs-lookup"><span data-stu-id="3a75e-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3a75e-117">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="3a75e-117">Technical walkthrough availability</span></span>

<span data-ttu-id="3a75e-118">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="3a75e-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="3a75e-119">instruções passo a passo de wiki de eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="3a75e-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="3a75e-120">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a75e-120">Overview</span></span>

<span data-ttu-id="3a75e-121">Neste passo a passo, você pode explorar a implementação inicial de três amostras de aplicativos herdados.</span><span class="sxs-lookup"><span data-stu-id="3a75e-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="3a75e-122">Os dois primeiros aplicativos de web de exemplo tem uma arquitetura monolítica e foram criados usando ASP.NET clássico.</span><span class="sxs-lookup"><span data-stu-id="3a75e-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="3a75e-123">Um aplicativo se baseia no ASP.NET 4.x MVC; o segundo aplicativo baseia-se nos Web Forms do ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="3a75e-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="3a75e-124">O aplicativo de terceiro é um aplicativo de camada 3 composto por um aplicativo de WinForms de cliente e um servidor [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span><span class="sxs-lookup"><span data-stu-id="3a75e-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="3a75e-125">Todos esses aplicativos estão disponíveis na [repositório do GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="3a75e-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="3a75e-126">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3a75e-126">Goals</span></span>

<span data-ttu-id="3a75e-127">A principal meta deste passo a passo é simplesmente para se familiarizar com esses aplicativos e seu código e a configuração.</span><span class="sxs-lookup"><span data-stu-id="3a75e-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="3a75e-128">Você pode configurar os aplicativos para que eles geram e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="3a75e-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="3a75e-129">Essa configuração opcional se baseia na injeção de dependência, de forma desacoplada.</span><span class="sxs-lookup"><span data-stu-id="3a75e-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="3a75e-130">Cenário 1: Aplicativos Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3a75e-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="3a75e-131">A figura a seguir mostra o cenário simples dos aplicativos de web ASP.NET herdados originais.</span><span class="sxs-lookup"><span data-stu-id="3a75e-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Cenário de arquitetura simples dos aplicativos herdados originais de web do ASP.NET](./media/image5-1.png)

<span data-ttu-id="3a75e-133">De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="3a75e-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="3a75e-134">Membros da equipe do enterprise eShop poderia usar o aplicativo para exibir e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="3a75e-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="3a75e-135">A próxima figura mostra as capturas de tela inicial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-135">The next figure shows the initial app screenshots.</span></span>

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdados)](./media/image5-2.png)

<span data-ttu-id="3a75e-137">Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="3a75e-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="3a75e-138">Cenário 2: Serviço WCF e o aplicativo de cliente de WinForms (aplicativo de camada 3)</span><span class="sxs-lookup"><span data-stu-id="3a75e-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="3a75e-139">A figura a seguir mostra o cenário simples do aplicativo herdado de 3 camadas original.</span><span class="sxs-lookup"><span data-stu-id="3a75e-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Cenário de arquitetura simples de aplicativo de camada 3 herdado original com um serviço WCF e um aplicativo de cliente de WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="3a75e-141">Benefícios</span><span class="sxs-lookup"><span data-stu-id="3a75e-141">Benefits</span></span>

<span data-ttu-id="3a75e-142">Os benefícios deste passo a passo são simples: Basta se familiarizar com os aplicativos inicias e o código.</span><span class="sxs-lookup"><span data-stu-id="3a75e-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="3a75e-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a75e-143">Next steps</span></span>

<span data-ttu-id="3a75e-144">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="3a75e-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="3a75e-145">Tour na linha de base ASP.NET MVC e aplicativos de Web Forms "herdados"</span><span class="sxs-lookup"><span data-stu-id="3a75e-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="3a75e-146">Tour sobre o serviço do WCF de linha de base e o aplicativo "herdado" do WinForms (camada 3)</span><span class="sxs-lookup"><span data-stu-id="3a75e-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="3a75e-147">Passo a passo 2: Colocar em contêineres seus aplicativos .NET existentes com contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="3a75e-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="3a75e-148">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a75e-148">Overview</span></span>

<span data-ttu-id="3a75e-149">Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles com base no MVC, Web Forms ou WCF, para ambientes de teste, desenvolvimento e produção.</span><span class="sxs-lookup"><span data-stu-id="3a75e-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="3a75e-150">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3a75e-150">Goals</span></span>

<span data-ttu-id="3a75e-151">O objetivo deste passo a passo é mostrar a você várias opções para colocar em contêineres um aplicativo existente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a75e-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="3a75e-152">Você pode:</span><span class="sxs-lookup"><span data-stu-id="3a75e-152">You can:</span></span>

- <span data-ttu-id="3a75e-153">Colocar o seu aplicativo em contêineres usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="3a75e-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="3a75e-154">Colocar o seu aplicativo em contêineres manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="3a75e-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="3a75e-155">Colocar o seu aplicativo em contêineres usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (uma ferramenta de código-fonte aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="3a75e-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="3a75e-156">Este passo a passo se concentra nas ferramentas do Visual Studio 2017 para a abordagem de Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="3a75e-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="3a75e-157">Cenário 1: Em contêineres aplicativos web em ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3a75e-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="3a75e-158">Figura a seguir mostra o cenário para aplicativos de aplicativos web herdados eShop em contêineres.</span><span class="sxs-lookup"><span data-stu-id="3a75e-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagrama da arquitetura simplificada de em contêineres aplicativos ASP.NET em um ambiente de desenvolvimento](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="3a75e-160">Cenário 2: Serviço do WCF em contêineres</span><span class="sxs-lookup"><span data-stu-id="3a75e-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="3a75e-161">Figura a seguir mostra o cenário para um aplicativo de camada 3 com um serviço WCF em contêineres.</span><span class="sxs-lookup"><span data-stu-id="3a75e-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagrama da arquitetura do serviço WCF em contêineres em um ambiente de desenvolvimento de simplificado](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="3a75e-163">Benefícios</span><span class="sxs-lookup"><span data-stu-id="3a75e-163">Benefits</span></span>

<span data-ttu-id="3a75e-164">Há vantagens em executar seu aplicativo monolítico em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="3a75e-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="3a75e-165">Primeiro, crie uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-165">First, you create an image for the application.</span></span> <span data-ttu-id="3a75e-166">Daí em diante, cada implantação é executada no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="3a75e-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="3a75e-167">Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instaladas, usa a mesma versão do .NET framework e é criado usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="3a75e-168">Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="3a75e-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="3a75e-169">As dependências de viagem com o aplicativo quando você implanta os contêineres.</span><span class="sxs-lookup"><span data-stu-id="3a75e-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="3a75e-170">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente, que é fornecido pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="3a75e-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="3a75e-171">Os problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de surgirem em um ambiente de preparo ou produção.</span><span class="sxs-lookup"><span data-stu-id="3a75e-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="3a75e-172">Diferenças em ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="3a75e-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="3a75e-173">Aplicativos em contêineres também têm uma curva de escala horizontal mais simples.</span><span class="sxs-lookup"><span data-stu-id="3a75e-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="3a75e-174">Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo regular por máquina.</span><span class="sxs-lookup"><span data-stu-id="3a75e-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="3a75e-175">Isso resulta em maior densidade e menos necessários recursos, especialmente ao usar orquestradores como Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3a75e-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="3a75e-176">O uso de contêineres, em situações ideais, não requer fazer alterações ao código do aplicativo (C\#).</span><span class="sxs-lookup"><span data-stu-id="3a75e-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="3a75e-177">Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="3a75e-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="3a75e-178">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a75e-178">Next steps</span></span>

<span data-ttu-id="3a75e-179">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="3a75e-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="3a75e-180">Como colocar em contêineres aplicativos web do .NET Framework com Docker e contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="3a75e-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="3a75e-181">Adicionando suporte ao Docker a um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="3a75e-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="3a75e-182">Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3a75e-183">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="3a75e-183">Technical walkthrough availability</span></span>

<span data-ttu-id="3a75e-184">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing: <https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="3a75e-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="3a75e-185">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a75e-185">Overview</span></span>

<span data-ttu-id="3a75e-186">Implantando em um host do Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite que você configure rapidamente ambientes de desenvolvimento/teste /.</span><span class="sxs-lookup"><span data-stu-id="3a75e-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="3a75e-187">Ele também fornece um lugar comum para testadores ou usuários de negócios validar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="3a75e-188">VMs também podem ser válida infraestrutura como um ambiente de produção do serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="3a75e-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="3a75e-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3a75e-189">Goals</span></span>

<span data-ttu-id="3a75e-190">O objetivo deste passo a passo é mostrar as várias alternativas que você tem quando você implanta os contêineres do Windows para VMs do Azure que são baseados no Windows Server 2016 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="3a75e-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3a75e-191">Cenários</span><span class="sxs-lookup"><span data-stu-id="3a75e-191">Scenarios</span></span>

<span data-ttu-id="3a75e-192">Vários cenários são abordados neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="3a75e-193">Cenário a: Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="3a75e-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

<span data-ttu-id="3a75e-195">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="3a75e-195">**Figure 5-4.**</span></span> <span data-ttu-id="3a75e-196">Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="3a75e-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="3a75e-197">Cenário b: Implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="3a75e-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar em uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

<span data-ttu-id="3a75e-199">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="3a75e-199">**Figure 5-5.**</span></span> <span data-ttu-id="3a75e-200">Implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="3a75e-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="3a75e-201">Cenário de c: Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-6.png)

<span data-ttu-id="3a75e-203">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="3a75e-203">**Figure 5-6.**</span></span> <span data-ttu-id="3a75e-204">Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="3a75e-205">VMs do Azure para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="3a75e-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="3a75e-206">VMs do Azure para contêineres do Windows são VMs com base no Windows Server 2016, Windows 10 ou versões posteriores, tanto com o mecanismo do Docker configurado.</span><span class="sxs-lookup"><span data-stu-id="3a75e-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="3a75e-207">Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="3a75e-208">Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**.</span><span class="sxs-lookup"><span data-stu-id="3a75e-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="3a75e-209">Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou do Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="3a75e-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="3a75e-210">Imagens de contêiner do sistema operacional são instaladas e, em seguida, a VM está pronta para uso com o Docker.</span><span class="sxs-lookup"><span data-stu-id="3a75e-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="3a75e-211">Benefícios</span><span class="sxs-lookup"><span data-stu-id="3a75e-211">Benefits</span></span>

<span data-ttu-id="3a75e-212">Embora os contêineres do Windows podem ser implantados em VMs locais Windows Server 2016, quando você implanta no Azure, você obtém uma maneira fácil de obter uma introdução, pronto para usar VMs de contêiner do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="3a75e-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="3a75e-213">Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de dimensionamento de máquina virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="3a75e-214">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a75e-214">Next steps</span></span>

<span data-ttu-id="3a75e-215">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="3a75e-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="3a75e-216">Passo a passo 4: Implantar seus aplicativos baseados em contêineres do Windows para instâncias de contêiner do Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="3a75e-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3a75e-217">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="3a75e-217">Technical walkthrough availability</span></span>

<span data-ttu-id="3a75e-218">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="3a75e-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="3a75e-219">[A implantação dos aplicativos nas Aci (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="3a75e-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="3a75e-220">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a75e-220">Overview</span></span>

<span data-ttu-id="3a75e-221">[Instâncias de contêiner do Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida para ter um ambiente de desenvolvimento/teste/contêineres onde você pode implantar instâncias únicas de contêineres.</span><span class="sxs-lookup"><span data-stu-id="3a75e-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="3a75e-222">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3a75e-222">Goals</span></span>

<span data-ttu-id="3a75e-223">Este passo a passo mostra os principais cenários ao implantar contêineres do Windows para instâncias de contêiner do Azure (ACI) e como você pode implantar aplicativos eShopModernizing em ACI.</span><span class="sxs-lookup"><span data-stu-id="3a75e-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3a75e-224">Cenários</span><span class="sxs-lookup"><span data-stu-id="3a75e-224">Scenarios</span></span>

<span data-ttu-id="3a75e-225">Pode haver variações sobre como implantar os aplicativos eShopModernizing em ACI como implantar apenas um ou todos os aplicativos (aplicativo MVC, o aplicativo de formulários da Web ou serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="3a75e-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="3a75e-226">No cenário a seguir, mostrado abaixo, você pode ver o aplicativo ASP.NET MVC além de contêiner do SQL Server, os dois implantados como contêineres em ACI (instâncias de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="3a75e-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Implantar em ACI a partir de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="3a75e-228">Benefícios</span><span class="sxs-lookup"><span data-stu-id="3a75e-228">Benefits</span></span>

<span data-ttu-id="3a75e-229">As instâncias de contêiner do Azure torna fácil criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior.</span><span class="sxs-lookup"><span data-stu-id="3a75e-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="3a75e-230">Com o ACI, diretamente você pode implantar um contêiner do Windows no Azure e expô-lo à internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro de Docker, como o Hub do Docker ou do contêiner do Azure Registro).</span><span class="sxs-lookup"><span data-stu-id="3a75e-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="3a75e-231">Considerações</span><span class="sxs-lookup"><span data-stu-id="3a75e-231">Considerations</span></span>

<span data-ttu-id="3a75e-232">Implantar contêineres do Windows com o .NET Framework completo / ASP.NET ou SQL Server nas instâncias de contêiner do Azure (ACI) não é muito mais rápido implantar em um Host Docker regulares (como um Windows Server 2016 com contêineres do Windows) porque a imagem do Docker deve ser baixados (extraídas do registro do Docker) sempre e os tamanhos da imagem de contêiner do SQL (15.1 GB) e a imagem de contêiner do ASP.NET (13.9 GB) são muito grandes, no entanto, é muito mais barato do que manter seu próprio host do docker (permanentemente on-line Windows Server 2016 com VM de contêineres do Windows no Azure) para não mencionar um orquestrador de inteiro, como Kubernetes no Azure (AKS) que é, por outro lado, uma ótima opção para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="3a75e-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="3a75e-233">Como conclusão principal, usando instâncias de contêiner do Azure é uma opção muito atraente para cenários de desenvolvimento/teste e para os pipelines de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="3a75e-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a75e-234">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a75e-234">Next steps</span></span>

<span data-ttu-id="3a75e-235">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="3a75e-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="3a75e-236">Passo a passo 5: Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="3a75e-237">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="3a75e-237">Technical walkthrough availability</span></span>

<span data-ttu-id="3a75e-238">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="3a75e-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)>

### <a name="overview"></a><span data-ttu-id="3a75e-239">Visão geral</span><span class="sxs-lookup"><span data-stu-id="3a75e-239">Overview</span></span>

<span data-ttu-id="3a75e-240">Um aplicativo que se baseia em contêineres do Windows rapidamente precisará usar as plataformas, ainda mais se afastando das VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="3a75e-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="3a75e-241">Isso é necessário para atingir facilmente alta escalabilidade e melhor automatizada de escalabilidade e para uma melhoria significativa na automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="3a75e-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="3a75e-242">Você pode obter essas metas, usando o orquestrador [Kubernetes](https://kubernetes.io/), disponível no [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="3a75e-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="3a75e-243">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3a75e-243">Goals</span></span>

<span data-ttu-id="3a75e-244">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em Windows contêiner no Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="3a75e-245">Implantar no Kubernetes do zero é um processo em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="3a75e-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="3a75e-246">Implante um cluster Kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="3a75e-247">Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3a75e-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="3a75e-248">Cenários</span><span class="sxs-lookup"><span data-stu-id="3a75e-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="3a75e-249">Cenário a: Implantar diretamente a um cluster Kubernetes em um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3a75e-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

<span data-ttu-id="3a75e-251">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="3a75e-251">**Figure 5-7.**</span></span> <span data-ttu-id="3a75e-252">Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="3a75e-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="3a75e-253">Cenário b: Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-8.png)

<span data-ttu-id="3a75e-255">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="3a75e-255">**Figure 5-8.**</span></span> <span data-ttu-id="3a75e-256">Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="3a75e-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="3a75e-257">Benefícios</span><span class="sxs-lookup"><span data-stu-id="3a75e-257">Benefits</span></span>

<span data-ttu-id="3a75e-258">Há muitos benefícios para implantar um cluster no Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3a75e-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="3a75e-259">O maior benefício é que você obtenha um ambiente pronto para produção em que você pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou de VMs em (o cluster escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="3a75e-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="3a75e-260">O serviço de contêiner do Azure otimiza as tecnologias e ferramentas de código-fonte aberto populares especialmente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="3a75e-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="3a75e-261">Você obtém uma solução aberta que oferece portabilidade, tanto para os contêineres para sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a75e-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="3a75e-262">Selecione o tamanho, o número de hosts, e o contêiner de ferramentas do orchestrator serviço lida com todo o resto.</span><span class="sxs-lookup"><span data-stu-id="3a75e-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="3a75e-263">Com o Kubernetes, os desenvolvedores podem progredir de pensar em máquinas físicas e virtuais, ao planejar uma infraestrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="3a75e-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="3a75e-264">Aplicativos com base em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="3a75e-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="3a75e-265">Replicação de instâncias de contêiner e o dimensionamento automático horizontal</span><span class="sxs-lookup"><span data-stu-id="3a75e-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="3a75e-266">Nomenclatura e descobrindo (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="3a75e-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="3a75e-267">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="3a75e-267">Balancing loads</span></span>

- <span data-ttu-id="3a75e-268">Atualizações sem interrupção</span><span class="sxs-lookup"><span data-stu-id="3a75e-268">Rolling updates</span></span>

- <span data-ttu-id="3a75e-269">Distribuição de segredos</span><span class="sxs-lookup"><span data-stu-id="3a75e-269">Distributing secrets</span></span>

- <span data-ttu-id="3a75e-270">Verificações de integridade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a75e-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a75e-271">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a75e-271">Next steps</span></span>

<span data-ttu-id="3a75e-272">Explore este conteúdo mais detalhado no wiki do GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)></span><span class="sxs-lookup"><span data-stu-id="3a75e-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="3a75e-273">[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [Próximo](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="3a75e-273">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
