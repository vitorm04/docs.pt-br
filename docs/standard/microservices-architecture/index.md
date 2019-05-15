---
title: Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres
description: Arquitetura de microsserviços do .NET para aplicativos do .NET em contêineres | Microsserviços são serviços implantáveis de maneira modular e independente. Os contêineres do Docker (para Linux e Windows) simplificam a implantação e o teste ao agrupar um serviço e suas dependências em uma única unidade, que será executada em um ambiente isolado.
ms.date: 01/07/2019
ms.openlocfilehash: bbd72b02ae446bbd0df31889679023d3b5040db8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644403"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="60e4d-105">Microsserviços do .NET: Arquitetura de aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="60e4d-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Capa do livro](./media/cover-small.png)

<span data-ttu-id="60e4d-107">**EDIÇÃO v2.2.00** – atualizada para o ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="60e4d-107">**EDITION v2.2.00** - Updated to ASP.NET Core 2.2</span></span>

<span data-ttu-id="60e4d-108">Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres.</span><span class="sxs-lookup"><span data-stu-id="60e4d-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="60e4d-109">Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="60e4d-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> 

<span data-ttu-id="60e4d-110">Para facilitar a introdução, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar.</span><span class="sxs-lookup"><span data-stu-id="60e4d-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="60e4d-111">O aplicativo de referência está disponível no repositório GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="60e4d-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="60e4d-112">Links de ação</span><span class="sxs-lookup"><span data-stu-id="60e4d-112">Action links</span></span>

* <span data-ttu-id="60e4d-113">Baixe este livro eletrônico no seu formato de escolha: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="60e4d-113">Download this eBook in your format of choice: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

* <span data-ttu-id="60e4d-114">Clone/Crie fork do aplicativo de referência [eShopOnContainers no GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="60e4d-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>
 
* <span data-ttu-id="60e4d-115">Assista ao [vídeo introdutório no Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="60e4d-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

* <span data-ttu-id="60e4d-116">Conheça a [Arquitetura de Microsserviços](https://aka.ms/MicroservicesArchitecture) agora mesmo</span><span class="sxs-lookup"><span data-stu-id="60e4d-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="60e4d-117">Introdução</span><span class="sxs-lookup"><span data-stu-id="60e4d-117">Introduction</span></span>

<span data-ttu-id="60e4d-118">As empresas estão cada vez mais percebendo a economia de custo, resolvendo problemas de implantação e melhorando as operações de produção e de DevOps usando os contêineres.</span><span class="sxs-lookup"><span data-stu-id="60e4d-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="60e4d-119">A Microsoft tem lançando inovações de contêiner para Windows e Linux com a criação de produtos como o Serviço de Contêiner do Azure e o Azure Service Fabric e por meio de parcerias com líderes do setor como a Docker, a Mesosphere e a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="60e4d-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="60e4d-120">Esses produtos oferecem soluções de contêiner que ajudam as empresas a criar e implantar aplicativos com a velocidade e a escala da nuvem, seja qual for a escolha de plataformas ou de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="60e4d-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="60e4d-121">O Docker está se tornando o verdadeiro padrão no setor de contêineres, com suporte dos fornecedores mais significativos nos ecossistemas do Windows e do Linux.</span><span class="sxs-lookup"><span data-stu-id="60e4d-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="60e4d-122">(A Microsoft é um dos principais fornecedores de nuvem com suporte para o Docker). No futuro, o Docker provavelmente será onipresente em qualquer datacenter na nuvem ou local.</span><span class="sxs-lookup"><span data-stu-id="60e4d-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="60e4d-123">Além disso, a arquitetura de [microsserviços](https://martinfowler.com/articles/microservices.html) está despontando como uma abordagem importante para aplicativos críticos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="60e4d-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="60e4d-124">Em uma arquitetura baseada em microsserviço, o aplicativo é criado em uma coleção de serviços que podem ser desenvolvidos, testados, implantados e ter as versões controladas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="60e4d-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="60e4d-125">Sobre este guia</span><span class="sxs-lookup"><span data-stu-id="60e4d-125">About this guide</span></span>

<span data-ttu-id="60e4d-126">Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres.</span><span class="sxs-lookup"><span data-stu-id="60e4d-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="60e4d-127">Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="60e4d-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="60e4d-128">Para facilitar a introdução aos contêineres e microsserviços, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar.</span><span class="sxs-lookup"><span data-stu-id="60e4d-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="60e4d-129">O aplicativo de exemplo está disponível no repositório [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="60e4d-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="60e4d-130">Este guia fornece diretrizes básicas de desenvolvimento e de arquitetura, principalmente no nível do ambiente de desenvolvimento, com foco em duas tecnologias: Docker e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="60e4d-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="60e4d-131">Nossa intenção é que você leia este guia, ao pensar sobre o design do aplicativo sem focar a infraestrutura (nuvem ou local) do ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="60e4d-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="60e4d-132">Você tomará decisões sobre a infraestrutura mais tarde, quando criar seus aplicativos prontos para produção.</span><span class="sxs-lookup"><span data-stu-id="60e4d-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="60e4d-133">Portanto, este guia tem a intenção de ser independente da infraestrutura e mais centrado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="60e4d-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="60e4d-134">Depois de estudar este guia, a próxima etapa será saber mais sobre os microsserviços pronto para produção no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="60e4d-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="60e4d-135">Versão</span><span class="sxs-lookup"><span data-stu-id="60e4d-135">Version</span></span>

<span data-ttu-id="60e4d-136">Este guia foi revisado para abordar a versão do **.NET Core 2.2**, além de muitas outras atualizações relacionadas à mesma "onda" de tecnologias (ou seja,</span><span class="sxs-lookup"><span data-stu-id="60e4d-136">This guide has been revised to cover **.NET Core 2.2** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="60e4d-137">as tecnologias do Azure e outras de terceiros) simultâneas ao .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="60e4d-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.2.</span></span> <span data-ttu-id="60e4d-138">É por isso que a versão do guia também foi atualizada para a versão **2.2**.</span><span class="sxs-lookup"><span data-stu-id="60e4d-138">That’s why the book version has also been updated to version **2.2**.</span></span> 

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="60e4d-139">O que este guia não cobre</span><span class="sxs-lookup"><span data-stu-id="60e4d-139">What this guide does not cover</span></span>

<span data-ttu-id="60e4d-140">Este guia não se concentra no ciclo de vida do aplicativo, em DevOps, nos pipelines de CI/CD nem no trabalho da equipe.</span><span class="sxs-lookup"><span data-stu-id="60e4d-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="60e4d-141">O guia complementar [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft) trata desse assunto.</span><span class="sxs-lookup"><span data-stu-id="60e4d-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="60e4d-142">O guia atual também não fornece detalhes de implementação na infraestrutura do Azure, como informações sobre orquestradores específicos.</span><span class="sxs-lookup"><span data-stu-id="60e4d-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="60e4d-143">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="60e4d-143">Additional resources</span></span>

- <span data-ttu-id="60e4d-144">**Ciclo de vida do aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft** (livro eletrônico para download)</span><span class="sxs-lookup"><span data-stu-id="60e4d-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="60e4d-145">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="60e4d-145">Who should use this guide</span></span>

<span data-ttu-id="60e4d-146">Escrevemos este guia para desenvolvedores e arquitetos de solução que são novos no desenvolvimento de aplicativos com base no Docker e em arquitetura baseada em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="60e4d-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="60e4d-147">Este guia será indicado para você se desejar saber como arquitetar, projetar e implementar aplicativos de prova de conceito com tecnologias de desenvolvimento da Microsoft (com foco especial no .NET Core) e com contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="60e4d-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="60e4d-148">Esse guia também será útil se você for um tomador de decisões técnicas, como um arquiteto corporativo que deseja ter uma visão geral da arquitetura e da tecnologia antes de decidir qual abordagem selecionar para aplicativos distribuídos novos e modernos.</span><span class="sxs-lookup"><span data-stu-id="60e4d-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="60e4d-149">Como usar este guia</span><span class="sxs-lookup"><span data-stu-id="60e4d-149">How to use this guide</span></span>

<span data-ttu-id="60e4d-150">A primeira parte deste guia apresenta os contêineres do Docker, discute como escolher entre o .NET Core e o .NET Framework como estrutura de desenvolvimento e fornece uma visão geral sobre microsserviços.</span><span class="sxs-lookup"><span data-stu-id="60e4d-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="60e4d-151">Este conteúdo é para arquitetos e tomadores de decisões técnicas que desejam ter uma visão geral, mas que não precisam se concentrar nos detalhes da implementação de código.</span><span class="sxs-lookup"><span data-stu-id="60e4d-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="60e4d-152">A segunda parte do guia de começa com a seção [Processo de desenvolvimento de aplicativos baseados no Docker](./docker-application-development-process/index.md).</span><span class="sxs-lookup"><span data-stu-id="60e4d-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="60e4d-153">Ela se concentra nos padrões de desenvolvimento e de microsserviços para implementar aplicativos que usam o .NET Core e o Docker.</span><span class="sxs-lookup"><span data-stu-id="60e4d-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="60e4d-154">Esta seção será de interesse especial para desenvolvedores e arquitetos que desejam se concentrar no código, nos padrões e nos detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="60e4d-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="60e4d-155">Aplicativo de referência baseado em contêiner e em microsserviço: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="60e4d-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="60e4d-156">O aplicativo eShopOnContainers é um aplicativo de referência de software livre para .NET Core e microsserviços criado para ser implantado usando contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="60e4d-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="60e4d-157">O aplicativo é composto de vários subsistemas, incluindo vários front-ends de interface do usuário de loja virtual (um aplicativo Web MVC, um SPA Web e um aplicativo móvel nativo).</span><span class="sxs-lookup"><span data-stu-id="60e4d-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="60e4d-158">Ele também inclui os microsserviços e os contêineres de back-end de todas as operações do servidor necessárias.</span><span class="sxs-lookup"><span data-stu-id="60e4d-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span> 

<span data-ttu-id="60e4d-159">A finalidade do aplicativo é demonstrar padrões de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="60e4d-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="60e4d-160">**A TI NÃO É UM MODELO PRONTO PARA PRODUÇÃO** para iniciar aplicativos de mundo real.</span><span class="sxs-lookup"><span data-stu-id="60e4d-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="60e4d-161">Na verdade, o aplicativo está em um estado beta permanente, porque também é usado para testar novas tecnologias potencialmente interessantes, à medida que aparecem.</span><span class="sxs-lookup"><span data-stu-id="60e4d-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="60e4d-162">Envie-nos seus comentários!</span><span class="sxs-lookup"><span data-stu-id="60e4d-162">Send us your feedback!</span></span>

<span data-ttu-id="60e4d-163">Escrevemos este guia para ajudá-lo a entender a arquitetura de aplicativos em contêineres e de microsserviços no .NET.</span><span class="sxs-lookup"><span data-stu-id="60e4d-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="60e4d-164">O guia e o aplicativo de referência relacionado continuarão sendo desenvolvidos, portanto seus comentários são bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="60e4d-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="60e4d-165">Se você tiver comentários sobre como este guia poderá ser melhorado, envie-os para:</span><span class="sxs-lookup"><span data-stu-id="60e4d-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="60e4d-166">Créditos</span><span class="sxs-lookup"><span data-stu-id="60e4d-166">Credits</span></span>

<span data-ttu-id="60e4d-167">Coautores:</span><span class="sxs-lookup"><span data-stu-id="60e4d-167">Co-Authors:</span></span>

> <span data-ttu-id="60e4d-168">**Cesar de la Torre**, Gerente sênior de produtos , equipe de produto do .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="60e4d-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="60e4d-169">**Bill Wagner**, Desenvolvedor sênior de conteúdo, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="60e4d-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="60e4d-170">**Mike Rousos**, Engenheiro de Software Principal, equipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="60e4d-171">Editores:</span><span class="sxs-lookup"><span data-stu-id="60e4d-171">Editors:</span></span>

> <span data-ttu-id="60e4d-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="60e4d-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="60e4d-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="60e4d-173">**Steve Hoag**</span></span>

<span data-ttu-id="60e4d-174">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="60e4d-174">Participants and reviewers:</span></span>

> <span data-ttu-id="60e4d-175">**Jeffrey Richter**, engenheiro de software parceiro, equipe do Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-176">**Jimmy Bogard**, Arquiteto Chefe na Headspring</span><span class="sxs-lookup"><span data-stu-id="60e4d-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="60e4d-177">**Udi Dahan**, Fundador e CEO, Particular Software</span><span class="sxs-lookup"><span data-stu-id="60e4d-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="60e4d-178">**Jimmy Nilsson**, Cofundador e CEO da Factor10</span><span class="sxs-lookup"><span data-stu-id="60e4d-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="60e4d-179">**Glenn Condron**, Gerente sênior de programas, equipe do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="60e4d-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="60e4d-180">**Mark Fussell**, PM Líder Principal, equipe do Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-181">**Diego Vega**, PM Líder, equipe do Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-182">**Barry Dorrans**, gerente de programas de segurança sênior</span><span class="sxs-lookup"><span data-stu-id="60e4d-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="60e4d-183">**Rowan Miller**, Gerente sênior de programas, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-184">**Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-185">**Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-186">**Nish Anil**, Gerente de Programa Sênior, Equipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-187">**Dylan Reisenberger**, Arquiteto e Desenvolvedor Líder na Polly</span><span class="sxs-lookup"><span data-stu-id="60e4d-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="60e4d-188">**Steve Smith**, Especialista e Instrutor em Software na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="60e4d-188">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="60e4d-189">**Cooper Ian**, Arquiteto de Codificação na Brighter</span><span class="sxs-lookup"><span data-stu-id="60e4d-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="60e4d-190">**Unai Zorrilla**, Arquiteto e Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="60e4d-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="60e4d-191">**Eduard Tomas**, Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="60e4d-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="60e4d-192">**Ramon Tomas**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="60e4d-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="60e4d-193">**David Sanz**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="60e4d-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="60e4d-194">**Javier Valero**, Diretor Executivo de Operações no Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="60e4d-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="60e4d-195">**Pierre Millet**, Consultor sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-196">**Michael Friis**, Gerente de Produto, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="60e4d-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="60e4d-197">**Charles Lowell**, Engenheiro de Software, equipe do VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="60e4d-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="60e4d-198">**Miguel Veloso**, Consultor sênior da Turing Challenge</span><span class="sxs-lookup"><span data-stu-id="60e4d-198">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>

## <a name="copyright"></a><span data-ttu-id="60e4d-199">Copyright</span><span class="sxs-lookup"><span data-stu-id="60e4d-199">Copyright</span></span>

<span data-ttu-id="60e4d-200">DOWNLOAD disponível em: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="60e4d-200">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="60e4d-201">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="60e4d-201">PUBLISHED BY</span></span>

<span data-ttu-id="60e4d-202">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60e4d-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="60e4d-203">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="60e4d-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="60e4d-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="60e4d-204">One Microsoft Way</span></span>

<span data-ttu-id="60e4d-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="60e4d-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="60e4d-206">Copyright © 2018, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="60e4d-206">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="60e4d-207">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="60e4d-207">All rights reserved.</span></span> <span data-ttu-id="60e4d-208">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="60e4d-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="60e4d-209">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="60e4d-209">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="60e4d-210">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="60e4d-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="60e4d-211">Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="60e4d-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="60e4d-212">Nenhuma associação ou conexão real é intencional ou deve ser deduzida.</span><span class="sxs-lookup"><span data-stu-id="60e4d-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="60e4d-213">A Microsoft e as marcas comerciais listadas em <https://www.microsoft.com> na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="60e4d-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="60e4d-214">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="60e4d-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="60e4d-215">O logotipo de baleia do Docker é uma marca registrada da Docker, Inc. usado mediante permissão.</span><span class="sxs-lookup"><span data-stu-id="60e4d-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="60e4d-216">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="60e4d-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="60e4d-217">Avançar</span><span class="sxs-lookup"><span data-stu-id="60e4d-217">Next</span></span>](container-docker-introduction/index.md)
