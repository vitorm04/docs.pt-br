---
title: Instruções passo a passo e técnico obtém visão de geral de Introdução
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Instruções passo a passo e técnico obtém visão de geral de Introdução
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: f5a9d0c7c1c45a6afca390e93384af4c8386fe09
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150583"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="ff0b5-103">Instruções passo a passo e técnico obtém visão de geral de Introdução</span><span class="sxs-lookup"><span data-stu-id="ff0b5-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="ff0b5-104">Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório GitHub.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="ff0b5-105">A série online de instruções passo a passo é descrita neste capítulo aborda a configuração passo a passo de vários ambientes em que se baseiam em contêineres do Windows e a implantação do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="ff0b5-106">As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="ff0b5-107">Você pode obter instruções passo a passo de si mesmos na *eShopModernizing* wiki do repositório de GitHub de aplicativos no [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="ff0b5-108">Passo a passo técnico lista</span><span class="sxs-lookup"><span data-stu-id="ff0b5-108">Technical walkthrough list</span></span>

<span data-ttu-id="ff0b5-109">Orientações de Introdução a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo que você pode levantar e deslocar usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="ff0b5-110">Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de exemplo, que estão disponíveis no GitHub em [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="ff0b5-111">**Tour de aplicativos herdados do eShop (aplicativos de linha de base para modernizar)**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="ff0b5-112">**Colocar seus aplicativos web ASP.NET existentes (WebForms e MVC) em um contêiner com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="ff0b5-113">**Colocar em contêineres seus serviços do WCF (aplicativos de N camadas) existentes com contêineres do Windows**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="ff0b5-114">**Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="ff0b5-115">**Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="ff0b5-116">**Implantar seus aplicativos baseados em contêineres do Windows no Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="ff0b5-117">Passo a passo 1: Tour de aplicativos herdados do eShop</span><span class="sxs-lookup"><span data-stu-id="ff0b5-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff0b5-118">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="ff0b5-118">Technical walkthrough availability</span></span>

<span data-ttu-id="ff0b5-119">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="ff0b5-120">instruções passo a passo de wiki de eShopModernizing</span><span class="sxs-lookup"><span data-stu-id="ff0b5-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="ff0b5-121">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-121">Overview</span></span>

<span data-ttu-id="ff0b5-122">Neste passo a passo, você pode explorar a implementação inicial de três amostras de aplicativos herdados.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="ff0b5-123">Os dois primeiros aplicativos de web de exemplo tem uma arquitetura monolítica e foram criados usando ASP.NET clássico.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="ff0b5-124">Um aplicativo se baseia no ASP.NET 4.x MVC; o segundo aplicativo baseia-se nos Web Forms do ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="ff0b5-125">O aplicativo de terceiro é um aplicativo de camada 3 composto por um aplicativo de WinForms de cliente e um servidor [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="ff0b5-126">Todos esses aplicativos estão disponíveis na [repositório do GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-127">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-127">Goals</span></span>

<span data-ttu-id="ff0b5-128">A principal meta deste passo a passo é simplesmente para se familiarizar com esses aplicativos e seu código e a configuração.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="ff0b5-129">Você pode configurar os aplicativos para que eles geram e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="ff0b5-130">Essa configuração opcional se baseia na injeção de dependência, de forma desacoplada.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="ff0b5-131">Cenário 1: Aplicativos Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff0b5-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="ff0b5-132">A figura a seguir mostra o cenário simples dos aplicativos de web ASP.NET herdados originais.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Cenário de arquitetura simples dos aplicativos herdados originais de web do ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="ff0b5-134">De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="ff0b5-135">Membros da equipe do enterprise eShop poderia usar o aplicativo para exibir e editar o catálogo de produtos.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="ff0b5-136">A próxima figura mostra as capturas de tela inicial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-136">The next figure shows the initial app screenshots.</span></span>

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdados)](./media/image5-2.png)

<span data-ttu-id="ff0b5-138">Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="ff0b5-139">Cenário 2: Serviço WCF e o aplicativo de cliente de WinForms (aplicativo de camada 3)</span><span class="sxs-lookup"><span data-stu-id="ff0b5-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="ff0b5-140">A figura a seguir mostra o cenário simples do aplicativo herdado de 3 camadas original.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Cenário de arquitetura simples de aplicativo de camada 3 herdado original com um serviço WCF e um aplicativo de cliente de WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ff0b5-142">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-142">Benefits</span></span>

<span data-ttu-id="ff0b5-143">Os benefícios deste passo a passo são simples: Basta se familiarizar com os aplicativos inicias e o código.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff0b5-144">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-144">Next steps</span></span>

<span data-ttu-id="ff0b5-145">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ff0b5-146">Tour na linha de base ASP.NET MVC e aplicativos de Web Forms "herdados"</span><span class="sxs-lookup"><span data-stu-id="ff0b5-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="ff0b5-147">Tour sobre o serviço do WCF de linha de base e o aplicativo "herdado" do WinForms (camada 3)</span><span class="sxs-lookup"><span data-stu-id="ff0b5-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="ff0b5-148">Passo a passo 2: Colocar em contêineres seus aplicativos .NET existentes com contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="ff0b5-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="ff0b5-149">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-149">Overview</span></span>

<span data-ttu-id="ff0b5-150">Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles com base no MVC, Web Forms ou WCF, para ambientes de teste, desenvolvimento e produção.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-151">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-151">Goals</span></span>

<span data-ttu-id="ff0b5-152">O objetivo deste passo a passo é mostrar a você várias opções para colocar em contêineres um aplicativo existente do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="ff0b5-153">Você pode:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-153">You can:</span></span>

- <span data-ttu-id="ff0b5-154">Colocar o seu aplicativo em contêineres usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="ff0b5-155">Colocar o seu aplicativo em contêineres manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="ff0b5-156">Colocar o seu aplicativo em contêineres usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (uma ferramenta de código-fonte aberto do Docker).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="ff0b5-157">Este passo a passo se concentra nas ferramentas do Visual Studio 2017 para a abordagem de Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="ff0b5-158">Cenário 1: Em contêineres aplicativos web em ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ff0b5-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="ff0b5-159">Figura a seguir mostra o cenário para aplicativos de aplicativos web herdados eShop em contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagrama da arquitetura simplificada de em contêineres aplicativos ASP.NET em um ambiente de desenvolvimento](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="ff0b5-161">Cenário 2: Serviço do WCF em contêineres</span><span class="sxs-lookup"><span data-stu-id="ff0b5-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="ff0b5-162">Figura a seguir mostra o cenário para um aplicativo de camada 3 com um serviço WCF em contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Diagrama da arquitetura do serviço WCF em contêineres em um ambiente de desenvolvimento de simplificado](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ff0b5-164">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-164">Benefits</span></span>

<span data-ttu-id="ff0b5-165">Há vantagens em executar seu aplicativo monolítico em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="ff0b5-166">Primeiro, crie uma imagem para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-166">First, you create an image for the application.</span></span> <span data-ttu-id="ff0b5-167">Daí em diante, cada implantação é executada no mesmo ambiente.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="ff0b5-168">Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instaladas, usa a mesma versão do .NET framework e é criado usando o mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="ff0b5-169">Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="ff0b5-170">As dependências de viagem com o aplicativo quando você implanta os contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="ff0b5-171">Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente, que é fornecido pelos contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="ff0b5-172">Os problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de surgirem em um ambiente de preparo ou produção.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="ff0b5-173">Diferenças em ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="ff0b5-174">Aplicativos em contêineres também têm uma curva de escala horizontal mais simples.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="ff0b5-175">Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo regular por máquina.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="ff0b5-176">Isso resulta em maior densidade e menos necessários recursos, especialmente ao usar orquestradores como Kubernetes ou Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="ff0b5-177">O uso de contêineres, em situações ideais, não requer fazer alterações ao código do aplicativo (C\#).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="ff0b5-178">Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff0b5-179">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-179">Next steps</span></span>

<span data-ttu-id="ff0b5-180">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ff0b5-181">Como colocar em contêineres aplicativos web do .NET Framework com Docker e contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="ff0b5-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="ff0b5-182">Adicionando suporte ao Docker a um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="ff0b5-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="ff0b5-183">Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff0b5-184">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="ff0b5-184">Technical walkthrough availability</span></span>

<span data-ttu-id="ff0b5-185">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="ff0b5-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="ff0b5-186">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-186">Overview</span></span>

<span data-ttu-id="ff0b5-187">Implantando em um host do Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite que você configure rapidamente ambientes de desenvolvimento/teste /.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="ff0b5-188">Ele também fornece um lugar comum para testadores ou usuários de negócios validar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="ff0b5-189">VMs também podem ser infraestrutura da válido como um ambiente de produção do serviço (IaaS).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-190">Goals</span></span>

<span data-ttu-id="ff0b5-191">O objetivo deste passo a passo é mostrar as várias alternativas que você tem quando você implanta os contêineres do Windows para VMs do Azure que são baseados no Windows Server 2016 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff0b5-192">Cenários</span><span class="sxs-lookup"><span data-stu-id="ff0b5-192">Scenarios</span></span>

<span data-ttu-id="ff0b5-193">Vários cenários são abordados neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="ff0b5-194">Cenário a: Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="ff0b5-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

> <span data-ttu-id="ff0b5-196">**Figura 5-4.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-196">**Figure 5-4.**</span></span> <span data-ttu-id="ff0b5-197">Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker</span><span class="sxs-lookup"><span data-stu-id="ff0b5-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="ff0b5-198">Cenário b: Implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="ff0b5-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Implantar em uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

> <span data-ttu-id="ff0b5-200">**Figura 5-5.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-200">**Figure 5-5.**</span></span> <span data-ttu-id="ff0b5-201">Implantar em uma VM do Azure por meio de um registro de Docker</span><span class="sxs-lookup"><span data-stu-id="ff0b5-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ff0b5-202">Cenário de c: Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-6.png)

> <span data-ttu-id="ff0b5-204">**Figura 5-6.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-204">**Figure 5-6.**</span></span> <span data-ttu-id="ff0b5-205">Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-205">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="ff0b5-206">VMs do Azure para contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="ff0b5-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="ff0b5-207">VMs do Azure para contêineres do Windows são VMs com base no Windows Server 2016, Windows 10 ou versões posteriores, tanto com o mecanismo do Docker configurado.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="ff0b5-208">Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="ff0b5-209">Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="ff0b5-210">Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou do Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="ff0b5-211">Imagens de contêiner do sistema operacional são instaladas e, em seguida, a VM está pronta para uso com o Docker.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="ff0b5-212">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-212">Benefits</span></span>

<span data-ttu-id="ff0b5-213">Embora os contêineres do Windows podem ser implantados em VMs locais Windows Server 2016, quando você implanta no Azure, você obtém uma maneira fácil de obter uma introdução, pronto para usar VMs de contêiner do Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="ff0b5-214">Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de dimensionamento de máquina virtual do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff0b5-215">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-215">Next steps</span></span>

<span data-ttu-id="ff0b5-216">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="ff0b5-217">Passo a passo 4: Implantar seus aplicativos baseados em contêineres do Windows para instâncias de contêiner do Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="ff0b5-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff0b5-218">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="ff0b5-218">Technical walkthrough availability</span></span>

<span data-ttu-id="ff0b5-219">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="ff0b5-220">[A implantação dos aplicativos nas Aci (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="ff0b5-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="ff0b5-221">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-221">Overview</span></span>

<span data-ttu-id="ff0b5-222">[Instâncias de contêiner do Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida para ter um ambiente de desenvolvimento/teste/contêineres onde você pode implantar instâncias únicas de contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-223">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-223">Goals</span></span>

<span data-ttu-id="ff0b5-224">Este passo a passo mostra os principais cenários ao implantar contêineres do Windows para instâncias de contêiner do Azure (ACI) e como você pode implantar aplicativos eShopModernizing em ACI.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff0b5-225">Cenários</span><span class="sxs-lookup"><span data-stu-id="ff0b5-225">Scenarios</span></span>

<span data-ttu-id="ff0b5-226">Pode haver variações sobre como implantar os aplicativos eShopModernizing em ACI como implantar apenas um ou todos os aplicativos (aplicativo MVC, o aplicativo de formulários da Web ou serviço WCF).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="ff0b5-227">No cenário a seguir, mostrado abaixo, você pode ver o aplicativo ASP.NET MVC além de contêiner do SQL Server, os dois implantados como contêineres em ACI (instâncias de contêiner do Azure).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Implantar em ACI a partir de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="ff0b5-229">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-229">Benefits</span></span>

<span data-ttu-id="ff0b5-230">As instâncias de contêiner do Azure torna fácil criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="ff0b5-231">Com o ACI, diretamente você pode implantar um contêiner do Windows no Azure e expô-lo à internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro de Docker, como o Hub do Docker ou do contêiner do Azure Registro).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="ff0b5-232">Considerações</span><span class="sxs-lookup"><span data-stu-id="ff0b5-232">Considerations</span></span>

<span data-ttu-id="ff0b5-233">Implantar contêineres do Windows com o .NET Framework completo / ASP.NET ou SQL Server nas instâncias de contêiner do Azure (ACI) não é muito mais rápido implantar em um Host Docker regulares (como um Windows Server 2016 com contêineres do Windows) porque a imagem do Docker deve ser baixados (extraídas do registro do Docker) sempre e os tamanhos da imagem de contêiner do SQL (15.1 GB) e a imagem de contêiner do ASP.NET (13.9 GB) são muito grandes, no entanto, é muito mais barato do que manter seu próprio host do docker (permanentemente on-line Windows Server 2016 com VM de contêineres do Windows no Azure) para não mencionar um orquestrador de inteiro como o Kubernetes no Azure (AKS/ACS) ou Azure Service Fabric que são, por outro lado, excelentes opções para implantações de produção.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="ff0b5-234">Como conclusão principal, usando instâncias de contêiner do Azure é uma opção muito atraente para cenários de desenvolvimento/teste e para os pipelines de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff0b5-235">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-235">Next steps</span></span>

<span data-ttu-id="ff0b5-236">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="ff0b5-237">Passo a passo 5: Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff0b5-238">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="ff0b5-238">Technical walkthrough availability</span></span>

<span data-ttu-id="ff0b5-239">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="ff0b5-240">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-240">Overview</span></span>

<span data-ttu-id="ff0b5-241">Um aplicativo que se baseia em contêineres do Windows rapidamente precisará usar as plataformas, ainda mais se afastando das VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ff0b5-242">Isso é necessário para atingir facilmente alta escalabilidade e melhor automatizada de escalabilidade e para uma melhoria significativa na automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ff0b5-243">Você pode obter essas metas, usando o orquestrador [Kubernetes](https://kubernetes.io/), disponível no [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-244">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-244">Goals</span></span>

<span data-ttu-id="ff0b5-245">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em Windows contêiner no Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="ff0b5-246">Implantar no Kubernetes do zero é um processo em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ff0b5-247">Implante um cluster Kubernetes no serviço de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="ff0b5-248">Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff0b5-249">Cenários</span><span class="sxs-lookup"><span data-stu-id="ff0b5-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="ff0b5-250">Cenário a: Implantar diretamente a um cluster Kubernetes em um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ff0b5-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

> <span data-ttu-id="ff0b5-252">**Figura 5-7.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-252">**Figure 5-7.**</span></span> <span data-ttu-id="ff0b5-253">Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ff0b5-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ff0b5-254">Cenário b: Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-8.png)

> <span data-ttu-id="ff0b5-256">**Figura 5-8.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-256">**Figure 5-8.**</span></span> <span data-ttu-id="ff0b5-257">Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="ff0b5-258">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-258">Benefits</span></span>

<span data-ttu-id="ff0b5-259">Há muitos benefícios para implantar um cluster no Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="ff0b5-260">O maior benefício é que você obtenha um ambiente pronto para produção em que você pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou de VMs em (o cluster escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ff0b5-261">O serviço de contêiner do Azure otimiza as tecnologias e ferramentas de código-fonte aberto populares especialmente para o Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="ff0b5-262">Você obtém uma solução aberta que oferece portabilidade, tanto para os contêineres para sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="ff0b5-263">Selecione o tamanho, o número de hosts, e o contêiner de ferramentas do orchestrator serviço lida com todo o resto.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="ff0b5-264">Com o Kubernetes, os desenvolvedores podem progredir de pensar em máquinas físicas e virtuais, ao planejar uma infraestrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ff0b5-265">Aplicativos com base em vários contêineres</span><span class="sxs-lookup"><span data-stu-id="ff0b5-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="ff0b5-266">Replicação de instâncias de contêiner e o dimensionamento automático horizontal</span><span class="sxs-lookup"><span data-stu-id="ff0b5-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="ff0b5-267">Nomenclatura e descobrindo (por exemplo, DNS interno)</span><span class="sxs-lookup"><span data-stu-id="ff0b5-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="ff0b5-268">Balanceamento de carga</span><span class="sxs-lookup"><span data-stu-id="ff0b5-268">Balancing loads</span></span>

- <span data-ttu-id="ff0b5-269">Atualizações sem interrupção</span><span class="sxs-lookup"><span data-stu-id="ff0b5-269">Rolling updates</span></span>

- <span data-ttu-id="ff0b5-270">Distribuição de segredos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-270">Distributing secrets</span></span>

- <span data-ttu-id="ff0b5-271">Verificações de integridade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff0b5-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff0b5-272">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-272">Next steps</span></span>

<span data-ttu-id="ff0b5-273">Explore este conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="ff0b5-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="ff0b5-274">Passo a passo 6: Implantar seus aplicativos baseados em contêineres do Windows no Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="ff0b5-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ff0b5-275">Disponibilidade de passo a passo técnico</span><span class="sxs-lookup"><span data-stu-id="ff0b5-275">Technical walkthrough availability</span></span>

<span data-ttu-id="ff0b5-276">O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="ff0b5-277">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ff0b5-277">Overview</span></span>

<span data-ttu-id="ff0b5-278">Um aplicativo baseado em contêineres do Windows rapidamente precisa usar as plataformas, ainda mais se afastando das VMs de IaaS.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ff0b5-279">Isso é necessário para atingir facilmente alta escalabilidade e melhor automatizada de escalabilidade e para uma melhoria significativa na automatizada implantações e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ff0b5-280">Para atingir essas metas, usando o orquestrador do Azure Service Fabric, que está disponível na nuvem do Azure, mas também está disponível para uso no local, ou até mesmo em uma nuvem pública diferente.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="ff0b5-281">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ff0b5-281">Goals</span></span>

<span data-ttu-id="ff0b5-282">O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows em um cluster do Service Fabric no Azure.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="ff0b5-283">Implantação do Service Fabric do zero é um processo de duas etapas:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ff0b5-284">Implante um cluster do Service Fabric no Azure (ou em um ambiente diferente).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="ff0b5-285">Implante o aplicativo e os recursos relacionados ao cluster do Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ff0b5-286">Cenários</span><span class="sxs-lookup"><span data-stu-id="ff0b5-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="ff0b5-287">Cenário a: Implantar diretamente em um cluster do Service Fabric de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ff0b5-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Implantar diretamente em um cluster do Service Fabric de um ambiente de desenvolvimento](./media/image5-9.png)

> <span data-ttu-id="ff0b5-289">**Figura 5-9.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-289">**Figure 5-9.**</span></span> <span data-ttu-id="ff0b5-290">Implantar diretamente em um cluster do Service Fabric de um ambiente de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="ff0b5-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="ff0b5-291">Cenário b: Implantar um cluster do Service Fabric de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Implantar um cluster do Service Fabric de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-10.png)

> <span data-ttu-id="ff0b5-293">**Figura 5-10.**</span><span class="sxs-lookup"><span data-stu-id="ff0b5-293">**Figure 5-10.**</span></span> <span data-ttu-id="ff0b5-294">Implantar um cluster do Service Fabric de pipelines de CI/CD nos serviços de DevOps do Azure</span><span class="sxs-lookup"><span data-stu-id="ff0b5-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

## <a name="benefits"></a><span data-ttu-id="ff0b5-295">Benefícios</span><span class="sxs-lookup"><span data-stu-id="ff0b5-295">Benefits</span></span>

<span data-ttu-id="ff0b5-296">Os benefícios de implantar um cluster no Service Fabric são semelhantes aos benefícios de usar o Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="ff0b5-297">Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção mais maduro para aplicativos do Windows em comparação comparada Kubernetes, que está em uma fase beta para contêineres do Windows na versão 1.9 do Kubernetes (dezembro de 2017).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="ff0b5-298">O Kubernetes é um ambiente mais maduro para Linux.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="ff0b5-299">O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção em que você pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ff0b5-300">O Azure Service Fabric oferece portabilidade para seus contêineres e sua configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="ff0b5-301">Você pode ter uma malha de serviço de cluster no Azure, ou instalá-lo no local em seu próprio datacenter.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="ff0b5-302">Você pode até instalar um cluster do Service Fabric em uma nuvem diferente, como [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="ff0b5-303">Com o Service Fabric, os desenvolvedores podem progredir de pensar em máquinas físicas e virtuais para planejar uma infraestrutura centrada no contêiner que facilita os seguintes recursos, entre outros:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ff0b5-304">Aplicativos com base em vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="ff0b5-305">Replicação de instâncias de contêiner e o dimensionamento automático horizontal.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="ff0b5-306">Nomenclatura e descobrindo (por exemplo, DNS interno).</span><span class="sxs-lookup"><span data-stu-id="ff0b5-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="ff0b5-307">Balanceamento de carga.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-307">Balancing loads.</span></span>

- <span data-ttu-id="ff0b5-308">Atualizações sem interrupção.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-308">Rolling updates.</span></span>

- <span data-ttu-id="ff0b5-309">Distribuição de segredos.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-309">Distributing secrets.</span></span>

- <span data-ttu-id="ff0b5-310">Verificações de integridade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-310">Application health checks.</span></span>

<span data-ttu-id="ff0b5-311">Os seguintes recursos são exclusivos no Service Fabric (em comparação com outros orquestradores):</span><span class="sxs-lookup"><span data-stu-id="ff0b5-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="ff0b5-312">Funcionalidade de serviços com estado, por meio do modelo de aplicativo de Reliable Services.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="ff0b5-313">Padrão de atores, por meio do modelo de aplicativo de Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="ff0b5-314">Implante os processos de funções básicas, além de contêineres do Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="ff0b5-315">Atualizações sem interrupção e verificações de integridade avançados.</span><span class="sxs-lookup"><span data-stu-id="ff0b5-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ff0b5-316">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ff0b5-316">Next steps</span></span>

<span data-ttu-id="ff0b5-317">Explore este conteúdo mais detalhado no wiki do GitHub:</span><span class="sxs-lookup"><span data-stu-id="ff0b5-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
><span data-ttu-id="ff0b5-318">[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
>[Próximo](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="ff0b5-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>