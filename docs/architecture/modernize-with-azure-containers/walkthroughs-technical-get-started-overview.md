---
title: Visão geral de tutoriais passo a passo e introduções técnicas
description: Modernizar aplicativos .NET existentes com contêineres Azure Cloud e Windows | Passo a passo e visão técnica começam
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660892"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="baa78-103">Visão geral de tutoriais passo a passo e introduções técnicas</span><span class="sxs-lookup"><span data-stu-id="baa78-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="baa78-104">Para limitar o tamanho deste e-book, documentação técnica adicional e os passoados completos foram disponibilizados em um repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="baa78-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="baa78-105">A série on-line de passo sadia que é descrita neste capítulo abrange a configuração passo a passo dos vários ambientes baseados em contêineres do Windows e a implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="baa78-106">As seções a seguir explicam do que se trata cada passo a passo, seus objetivos e visão de alto nível, e fornece um diagrama das tarefas envolvidas.</span><span class="sxs-lookup"><span data-stu-id="baa78-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="baa78-107">Você pode obter os passo a passo nos aplicativos *eShopModernizing* GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="baa78-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="baa78-108">Lista técnica de passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-108">Technical walkthrough list</span></span>

<span data-ttu-id="baa78-109">Os passoados iniciais a seguir fornecem orientação técnica consistente e abrangente para aplicativos de amostra que você pode levantar e mudar usando contêineres e, em seguida, mover-se usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="baa78-110">Cada um dos passoados a seguir usa os novos aplicativos eShopLegacy e eShopModernizing, que estão disponíveis no GitHub em <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="baa78-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="baa78-111">**Tour pelos aplicativos legados do eShop (aplicativos de base para modernizar)**</span><span class="sxs-lookup"><span data-stu-id="baa78-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="baa78-112">**Contêiner seus aplicativos web ASP.NET existentes (WebForms & MVC) com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="baa78-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="baa78-113">**Contêiner seus serviços WCF existentes (aplicativos N-Tier) com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="baa78-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="baa78-114">**Implante seu aplicativo baseado em contêineres do Windows para as VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="baa78-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="baa78-115">**Implante seus aplicativos baseados em contêineres do Windows para kubernetes no Serviço de Contêineres Do Azure**</span><span class="sxs-lookup"><span data-stu-id="baa78-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="baa78-116">Passo a passo 1: Tour pelos aplicativos legados do eShop</span><span class="sxs-lookup"><span data-stu-id="baa78-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="baa78-117">Disponibilidade técnica do passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-117">Technical walkthrough availability</span></span>

<span data-ttu-id="baa78-118">O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="baa78-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="baa78-119">eShopModernizando os passoados da wiki</span><span class="sxs-lookup"><span data-stu-id="baa78-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="baa78-120">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-120">Overview</span></span>

<span data-ttu-id="baa78-121">Neste passo a passo, você pode explorar a implementação inicial de três aplicativos legados de amostra.</span><span class="sxs-lookup"><span data-stu-id="baa78-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="baa78-122">Os dois primeiros aplicativos web de amostra têm uma arquitetura monolítica, e foram criados usando ASP.NET clássicos.</span><span class="sxs-lookup"><span data-stu-id="baa78-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="baa78-123">Um aplicativo é baseado em ASP.NET 4.x MVC; o segundo aplicativo é baseado em ASP.NET Formulários web 4.x.</span><span class="sxs-lookup"><span data-stu-id="baa78-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="baa78-124">O terceiro app é um aplicativo de 3 níveis composto por um aplicativo WinForms cliente e um serviço [de WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="baa78-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="baa78-125">Todos esses aplicativos estão disponíveis no [repo gitHub do eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="baa78-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-126">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-126">Goals</span></span>

<span data-ttu-id="baa78-127">O objetivo principal deste passo a passo é simplesmente se familiarizar com esses aplicativos, e com seu código e configuração.</span><span class="sxs-lookup"><span data-stu-id="baa78-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="baa78-128">Você pode configurar os aplicativos para que eles gerem e usem dados simulados, sem usar o banco de dados SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="baa78-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="baa78-129">Esta configuração opcional é baseada na injeção de dependência, de forma dissociada.</span><span class="sxs-lookup"><span data-stu-id="baa78-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="baa78-130">Cenário 1: ASP.NET aplicativos web</span><span class="sxs-lookup"><span data-stu-id="baa78-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="baa78-131">A figura abaixo mostra o cenário simples do legado original ASP.NET aplicações web.</span><span class="sxs-lookup"><span data-stu-id="baa78-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Cenário de arquitetura simples do legado original ASP.NET aplicações web](./media/image5-1.png)

<span data-ttu-id="baa78-133">Do ponto de vista do domínio de negócios, ambos os aplicativos oferecem os mesmos recursos de gerenciamento de catálogo.</span><span class="sxs-lookup"><span data-stu-id="baa78-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="baa78-134">Os membros da equipe corporativa da eShop usariam o aplicativo para visualizar e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="baa78-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="baa78-135">A próxima figura mostra as capturas de tela iniciais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baa78-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET aplicativos MVC e ASP.NET Web Forms (tecnologias existentes/legados)](./media/image5-2.png)

<span data-ttu-id="baa78-137">Dependências em ASP.NET versões 4.x ou anteriores (seja para MVC ou para Formulários Web) significa que esses aplicativos não serão executados no .NET Core, a menos que o código seja totalmente reescrito usando ASP.NET MVC core.</span><span class="sxs-lookup"><span data-stu-id="baa78-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="baa78-138">Cenário 2: serviço WCF e aplicativo cliente WinForms (aplicativo de 3 níveis)</span><span class="sxs-lookup"><span data-stu-id="baa78-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="baa78-139">A figura abaixo mostra o cenário simples do aplicativo legado original de 3 níveis.</span><span class="sxs-lookup"><span data-stu-id="baa78-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Cenário de arquitetura simples do aplicativo original legado de 3 níveis com um serviço WCF e um aplicativo cliente WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="baa78-141">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-141">Benefits</span></span>

<span data-ttu-id="baa78-142">Os benefícios deste passo a passo são simples: basta se familiarizar com o código e os aplicativos iniciais.</span><span class="sxs-lookup"><span data-stu-id="baa78-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="baa78-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-143">Next steps</span></span>

<span data-ttu-id="baa78-144">Explore este conteúdo mais aprofundado na wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="baa78-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="baa78-145">Tour na linha de base ASP.NET aplicativos "legados" de MVC e Web Forms</span><span class="sxs-lookup"><span data-stu-id="baa78-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="baa78-146">Tour no serviço wcf de linha de base e no aplicativo "legado" WinForms (3-Tier)</span><span class="sxs-lookup"><span data-stu-id="baa78-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="baa78-147">Passo a passo 2: Contêiner seus aplicativos .NET existentes com contêineres windows</span><span class="sxs-lookup"><span data-stu-id="baa78-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="baa78-148">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-148">Overview</span></span>

<span data-ttu-id="baa78-149">Use os contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, Formulários web ou WCF, para ambientes de produção, desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="baa78-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-150">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-150">Goals</span></span>

<span data-ttu-id="baa78-151">O objetivo deste passo a passo é mostrar várias opções para contêiner um aplicativo .NET Framework existente.</span><span class="sxs-lookup"><span data-stu-id="baa78-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="baa78-152">Você pode:</span><span class="sxs-lookup"><span data-stu-id="baa78-152">You can:</span></span>

- <span data-ttu-id="baa78-153">Contêiner seu aplicativo usando [o Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="baa78-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="baa78-154">Contêiner seu aplicativo adicionando manualmente um [arquivo Docker](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [Cli Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="baa78-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="baa78-155">Contêiner seu aplicativo usando a ferramenta [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (uma ferramenta de código aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="baa78-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="baa78-156">Este passo a passo se concentra na abordagem Visual Studio 2017 Tools for Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso de Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="baa78-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="baa78-157">Cenário 1: Aplicativos web ASP.NET contêiner</span><span class="sxs-lookup"><span data-stu-id="baa78-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="baa78-158">A figura abaixo mostra o cenário para aplicativos web legados do eShop contêiner.</span><span class="sxs-lookup"><span data-stu-id="baa78-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagrama de arquitetura simplificado de aplicações ASP.NET contêiner em um ambiente de desenvolvimento](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="baa78-160">Cenário 2: Serviço de CfFC containerizado</span><span class="sxs-lookup"><span data-stu-id="baa78-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="baa78-161">A figura abaixo mostra o cenário de um aplicativo de 3 níveis com um serviço WCF contêiner.</span><span class="sxs-lookup"><span data-stu-id="baa78-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagrama de arquitetura simplificado do serviço WCF contêiner em um ambiente de desenvolvimento](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="baa78-163">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-163">Benefits</span></span>

<span data-ttu-id="baa78-164">Há vantagens em executar sua aplicação monolítica em um recipiente.</span><span class="sxs-lookup"><span data-stu-id="baa78-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="baa78-165">Primeiro, você cria uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baa78-165">First, you create an image for the application.</span></span> <span data-ttu-id="baa78-166">A partir daí, todas as implantações são executadas no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="baa78-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="baa78-167">Cada contêiner usa a mesma versão do SISTEMA OPERACIONAL, tem a mesma versão de dependências instaladas, usa a mesma versão de framework .NET e é construído usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="baa78-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="baa78-168">Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="baa78-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="baa78-169">As dependências viajam com o aplicativo quando você implanta os contêineres.</span><span class="sxs-lookup"><span data-stu-id="baa78-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="baa78-170">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelo Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="baa78-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="baa78-171">Problemas que aparecem apenas com determinadas versões podem ser detectados imediatamente, em vez de aparecer em um ambiente de encenação ou produção.</span><span class="sxs-lookup"><span data-stu-id="baa78-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="baa78-172">As diferenças nos ambientes de desenvolvimento usados pelos membros da equipe de desenvolvimento importam menos quando as aplicações são executadas em contêineres.</span><span class="sxs-lookup"><span data-stu-id="baa78-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="baa78-173">Aplicações conteificadas também têm uma curva de escala mais plana.</span><span class="sxs-lookup"><span data-stu-id="baa78-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="baa78-174">Os aplicativos em contêiner permitem que você tenha mais instâncias de aplicação e serviço (baseadas em contêineres) em uma VM ou máquina física em comparação com implantações regulares de aplicativos por máquina.</span><span class="sxs-lookup"><span data-stu-id="baa78-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="baa78-175">Isso se traduz em maior densidade e menos recursos necessários, especialmente quando você usa orquestradores como Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="baa78-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="baa78-176">A containerização, em situações ideais, não requer\#qualquer alteração no código do aplicativo (C ).</span><span class="sxs-lookup"><span data-stu-id="baa78-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="baa78-177">Na maioria dos cenários, você só precisa dos arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="baa78-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="baa78-178">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-178">Next steps</span></span>

<span data-ttu-id="baa78-179">Explore este conteúdo mais aprofundado na wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="baa78-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="baa78-180">Como contêiner os aplicativos web .NET Framework com Contêineres Windows e Docker</span><span class="sxs-lookup"><span data-stu-id="baa78-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="baa78-181">Adicionando suporte ao Docker a um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="baa78-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="baa78-182">Passo a passo 3: implante seu aplicativo baseado em contêineres do Windows para as VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="baa78-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="baa78-183">Disponibilidade técnica do passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-183">Technical walkthrough availability</span></span>

<span data-ttu-id="baa78-184">O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="baa78-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="baa78-185">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-185">Overview</span></span>

<span data-ttu-id="baa78-186">A implantação em um host Docker em uma Máquina Virtual (VM) do Windows Server 2016 no Azure permite configurar rapidamente ambientes de desenvolvimento/teste/estágio.</span><span class="sxs-lookup"><span data-stu-id="baa78-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="baa78-187">Ele também lhe dá um lugar comum para testadores ou usuários de negócios validarem o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baa78-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="baa78-188">As VMs também podem ser ambientes de produção de infra-estrutura como serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="baa78-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-189">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-189">Goals</span></span>

<span data-ttu-id="baa78-190">O objetivo deste passo a passo é mostrar as múltiplas alternativas que você tem ao implantar o Windows Containers para As VMs do Azure que são baseadas nas versões windows server 2016 ou posteriores.</span><span class="sxs-lookup"><span data-stu-id="baa78-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="baa78-191">Cenários</span><span class="sxs-lookup"><span data-stu-id="baa78-191">Scenarios</span></span>

<span data-ttu-id="baa78-192">Vários cenários estão cobertos neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="baa78-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="baa78-193">Cenário A: Implantar em um VM Azure a partir de um PC dev através da conexão Docker Engine</span><span class="sxs-lookup"><span data-stu-id="baa78-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em um Azure VM a partir de um PC dev através de uma conexão Docker Engine](./media/image5-4.png)

<span data-ttu-id="baa78-195">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="baa78-195">**Figure 5-4.**</span></span> <span data-ttu-id="baa78-196">Implantar em um Azure VM a partir de um PC dev através de uma conexão Docker Engine</span><span class="sxs-lookup"><span data-stu-id="baa78-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="baa78-197">Cenário B: Implantar em uma VM Azure através de um Registro Docker</span><span class="sxs-lookup"><span data-stu-id="baa78-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar em uma VM Azure através de um Registro Docker](./media/image5-5.png)

<span data-ttu-id="baa78-199">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="baa78-199">**Figure 5-5.**</span></span> <span data-ttu-id="baa78-200">Implantar em uma VM Azure através de um Registro Docker</span><span class="sxs-lookup"><span data-stu-id="baa78-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="baa78-201">Cenário C: Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="baa78-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps](./media/image5-6.png)

<span data-ttu-id="baa78-203">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="baa78-203">**Figure 5-6.**</span></span> <span data-ttu-id="baa78-204">Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="baa78-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="baa78-205">VMs do Azure para Contêineres Windows</span><span class="sxs-lookup"><span data-stu-id="baa78-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="baa78-206">As VMs do Azure para Contêineres Windows são VMs baseadas no Windows Server 2016, Windows 10 ou versões posteriores, ambas com o Docker Engine configurado.</span><span class="sxs-lookup"><span data-stu-id="baa78-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="baa78-207">Na maioria dos casos, o Windows Server 2016 é usado nas VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="baa78-208">Atualmente, o Azure fornece uma VM chamada **Windows Server 2016 com Contêineres**.</span><span class="sxs-lookup"><span data-stu-id="baa78-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="baa78-209">Você pode usar este VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou o Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="baa78-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="baa78-210">As imagens do sistema operacional de contêiner são instaladas e, em seguida, a VM está pronta para usar com o Docker.</span><span class="sxs-lookup"><span data-stu-id="baa78-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="baa78-211">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-211">Benefits</span></span>

<span data-ttu-id="baa78-212">Embora os contêineres do Windows possam ser implantados em VMs do Windows Server 2016, quando você for implantado no Azure, você tem uma maneira mais fácil de começar, com VMs de contêiner do Windows Server prontos para uso.</span><span class="sxs-lookup"><span data-stu-id="baa78-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="baa78-213">Você também tem um local on-line comum que é acessível aos testadores e escalabilidade automática através de conjuntos de escala de máquinas virtuais do Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="baa78-214">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-214">Next steps</span></span>

<span data-ttu-id="baa78-215">Explore este conteúdo mais aprofundado na wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="baa78-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="baa78-216">Passo a passo 4: implante seus aplicativos baseados em contêineres do Windows para a ACI (ACI)</span><span class="sxs-lookup"><span data-stu-id="baa78-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="baa78-217">Disponibilidade técnica do passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-217">Technical walkthrough availability</span></span>

<span data-ttu-id="baa78-218">O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="baa78-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="baa78-219">[Implantação dos aplicativos para ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="baa78-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="baa78-220">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-220">Overview</span></span>

<span data-ttu-id="baa78-221">[A ACI (Azure Container Instances, instâncias de contêiner do Azure)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida de ter um ambiente de dev/teste/estágio de contêineres onde você pode implantar instâncias únicas de contêineres.</span><span class="sxs-lookup"><span data-stu-id="baa78-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-222">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-222">Goals</span></span>

<span data-ttu-id="baa78-223">Este passo a passo mostra os principais cenários ao implantar os contêineres do Windows no ACI (ACI) e como você pode implantar aplicativos de eShopModernizando em ACI.</span><span class="sxs-lookup"><span data-stu-id="baa78-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="baa78-224">Cenários</span><span class="sxs-lookup"><span data-stu-id="baa78-224">Scenarios</span></span>

<span data-ttu-id="baa78-225">Pode haver variações sobre a implantação dos aplicativos eShopModernizando em ACI, como a implantação de apenas um ou todos os aplicativos (aplicativo MVC, aplicativo WebForms ou serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="baa78-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="baa78-226">No cenário a seguir mostrado abaixo, você pode ver o aplicativo mvc ASP.NET mais o contêiner SQL Server, ambos implantados como contêineres em ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="baa78-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Implantar na ACI a partir de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="baa78-228">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-228">Benefits</span></span>

<span data-ttu-id="baa78-229">As Instâncias de Contêiner do Azure facilitam criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior.</span><span class="sxs-lookup"><span data-stu-id="baa78-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="baa78-230">Com a ACI, você pode implantar diretamente um contêiner do Windows no Azure e expô-lo à internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem do Contêiner do Windows pronta em um registro docker como Docker Hub ou Azure Container Registro).</span><span class="sxs-lookup"><span data-stu-id="baa78-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="baa78-231">Considerações</span><span class="sxs-lookup"><span data-stu-id="baa78-231">Considerations</span></span>

<span data-ttu-id="baa78-232">Implantar contêineres windows com o Framework /ASP.NET ou o SQL Server completos no Azure Container Instances (ACI) não é tão rápido quanto implantar em um Host Docker normal (como um Windows Server 2016 com contêineres windows) porque a imagem do Docker tem que ser baixada (retirada do registro docker) todas as vezes e os tamanhos da imagem do contêiner SQL (15,1 GB) e da imagem do contêiner ASP.NET (13,9 GB) são significativamente significativamente no entanto, é muito mais barato do que manter seu próprio host docker (permanentemente on-line Windows Servidor 2016 com Windows Containers VM no Azure) sem mencionar um orquestrador inteiro como Kubernetes in Azure (AKS) que é, por outro lado, uma ótima escolha para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="baa78-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="baa78-233">Como conclusão principal, o uso do Azure Container Instances é uma opção muito atraente para cenários de Dev/Teste e para pipelines de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="baa78-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="baa78-234">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-234">Next steps</span></span>

<span data-ttu-id="baa78-235">Explore este conteúdo mais aprofundado na wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="baa78-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="baa78-236">Passo a passo 5: implante seus aplicativos baseados em contêineres do Windows para kubernetes no Serviço de Contêineres Azure</span><span class="sxs-lookup"><span data-stu-id="baa78-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="baa78-237">Disponibilidade técnica do passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-237">Technical walkthrough availability</span></span>

<span data-ttu-id="baa78-238">O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="baa78-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="baa78-239">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-239">Overview</span></span>

<span data-ttu-id="baa78-240">Um aplicativo baseado em Contêineres Windows precisará rapidamente usar plataformas, afastando-se ainda mais das VMs IaaS.</span><span class="sxs-lookup"><span data-stu-id="baa78-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="baa78-241">Isso é necessário para alcançar facilmente alta escalabilidade e melhor escalabilidade automatizada, e para uma melhoria significativa nas implantações e versões automatizadas.</span><span class="sxs-lookup"><span data-stu-id="baa78-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="baa78-242">Você pode alcançar esses objetivos usando o orquestrador [Kubernetes](https://kubernetes.io/), disponível no [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="baa78-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-243">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-243">Goals</span></span>

<span data-ttu-id="baa78-244">O objetivo deste passo a passo é aprender a implantar um aplicativo baseado em contêiner do Windows no Kubernetes (também chamado *k8s)* no Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="baa78-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="baa78-245">Implantar no Kubernetes a partir do zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="baa78-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="baa78-246">Implante um cluster Kubernetes para o Serviço de Contêineres Do Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="baa78-247">Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="baa78-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="baa78-248">Cenários</span><span class="sxs-lookup"><span data-stu-id="baa78-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="baa78-249">Cenário A: Implante diretamente em um cluster Kubernetes a partir de um ambiente de vérme</span><span class="sxs-lookup"><span data-stu-id="baa78-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implante diretamente em um cluster Kubernetes a partir de um ambiente de desenvolvimento](./media/image5-7.png)

<span data-ttu-id="baa78-251">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="baa78-251">**Figure 5-7.**</span></span> <span data-ttu-id="baa78-252">Implante diretamente em um cluster Kubernetes a partir de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="baa78-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="baa78-253">Cenário B: Implantar em um cluster Kubernetes a partir de gasodutos CI/CD nos Serviços Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="baa78-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em um cluster Kubernetes a partir de pipelines CI/CD nos Serviços Azure DevOps](./media/image5-8.png)

<span data-ttu-id="baa78-255">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="baa78-255">**Figure 5-8.**</span></span> <span data-ttu-id="baa78-256">Implantar em um cluster Kubernetes a partir de pipelines CI/CD nos Serviços Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="baa78-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="baa78-257">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-257">Benefits</span></span>

<span data-ttu-id="baa78-258">Há muitos benefícios para implantar em um cluster em Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="baa78-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="baa78-259">O maior benefício é que você obtenha um ambiente pronto para a produção no qual você pode dimensionar o aplicativo com base no número de instâncias de contêiner que deseja usar (escalabilidade interna nos ádeis existentes) e com base no número de nódulos ou VMs no cluster ( escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="baa78-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="baa78-260">O Azure Container Service otimiza as populares ferramentas e tecnologias de código aberto especificamente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="baa78-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="baa78-261">Você recebe uma solução aberta que oferece portabilidade, tanto para seus contêineres quanto para a configuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="baa78-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="baa78-262">Você seleciona o tamanho, o número de hosts e o orchestrator tools-Container Service lida com todo o resto.</span><span class="sxs-lookup"><span data-stu-id="baa78-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="baa78-263">Com o Kubernetes, os desenvolvedores podem progredir desde pensar em máquinas físicas e virtuais, até planejar uma infra-estrutura centrada em contêineres que facilite os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="baa78-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="baa78-264">Aplicações baseadas em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="baa78-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="baa78-265">Replicando instâncias de contêiner e autodimensionamento horizontal</span><span class="sxs-lookup"><span data-stu-id="baa78-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="baa78-266">Nomeação e descoberta (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="baa78-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="baa78-267">Equilibrando cargas</span><span class="sxs-lookup"><span data-stu-id="baa78-267">Balancing loads</span></span>

- <span data-ttu-id="baa78-268">Atualizações de rolamento</span><span class="sxs-lookup"><span data-stu-id="baa78-268">Rolling updates</span></span>

- <span data-ttu-id="baa78-269">Distribuindo segredos</span><span class="sxs-lookup"><span data-stu-id="baa78-269">Distributing secrets</span></span>

- <span data-ttu-id="baa78-270">Verificações de saúde de aplicativos</span><span class="sxs-lookup"><span data-stu-id="baa78-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="baa78-271">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-271">Next steps</span></span>

<span data-ttu-id="baa78-272">Explore este conteúdo mais aprofundado na wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="baa78-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="baa78-273">Passo a passo 6: implante seus aplicativos baseados em contêineres do Windows para o Serviço de Aplicativos do Azure para Contêineres</span><span class="sxs-lookup"><span data-stu-id="baa78-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="baa78-274">Disponibilidade técnica do passo a passo</span><span class="sxs-lookup"><span data-stu-id="baa78-274">Technical walkthrough availability</span></span>

<span data-ttu-id="baa78-275">O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="baa78-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="baa78-276">Visão geral</span><span class="sxs-lookup"><span data-stu-id="baa78-276">Overview</span></span>

<span data-ttu-id="baa78-277">Um aplicativo simples contêiner usando o Windows Containers pode ser facilmente implantado no Azure App Service for Containers.</span><span class="sxs-lookup"><span data-stu-id="baa78-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="baa78-278">Esta é a abordagem recomendada para a maioria dos aplicativos baseados em contêiner do Windows.</span><span class="sxs-lookup"><span data-stu-id="baa78-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="baa78-279">Metas</span><span class="sxs-lookup"><span data-stu-id="baa78-279">Goals</span></span>

<span data-ttu-id="baa78-280">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows no Azure App Service for Containers a partir de um registro (Docker Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="baa78-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="baa78-281">Cenário</span><span class="sxs-lookup"><span data-stu-id="baa78-281">Scenario</span></span>

![Implantar aplicativo baseado em contêiner do Windows para o serviço de aplicativos do Azure para contêineres](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="baa78-283">Benefícios</span><span class="sxs-lookup"><span data-stu-id="baa78-283">Benefits</span></span>

<span data-ttu-id="baa78-284">A implantação do Azure App Service for Containers oferece os benefícios dos contêineres associados aos benefícios paaS do Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="baa78-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="baa78-285">O serviço de aplicativo pode ser facilmente dimensionado tanto verticalmente quanto horizontalmente, e pode ser configurado em escala automática para atender às demandas em mudança.</span><span class="sxs-lookup"><span data-stu-id="baa78-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="baa78-286">As atualizações podem ser realizadas com zero tempo de inatividade e a configuração da implantação contínua de um registro também é facilmente configurada.</span><span class="sxs-lookup"><span data-stu-id="baa78-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="baa78-287">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="baa78-287">Next steps</span></span>

<span data-ttu-id="baa78-288">Explore este conteúdo mais aprofundado na wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="baa78-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="baa78-289">[Próximo](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [anterior](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="baa78-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
