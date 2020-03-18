---
title: Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres
description: Arquitetura de microsserviços do .NET para aplicativos do .NET em contêineres | Microsserviços são serviços implantáveis de maneira modular e independente. Os contêineres do Docker (para Linux e Windows) simplificam a implantação e o teste ao agrupar um serviço e suas dependências em uma única unidade, que será executada em um ambiente isolado.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543528"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="98f90-105">Microsserviços .NET: arquitetura para aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="98f90-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Capa do livro](./media/cover-small.png)

<span data-ttu-id="98f90-107">**EDITION v3.1** - Atualizado para ASP.NET Núcleo 3.1</span><span class="sxs-lookup"><span data-stu-id="98f90-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="98f90-108">Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres.</span><span class="sxs-lookup"><span data-stu-id="98f90-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="98f90-109">Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f90-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="98f90-110">Para facilitar a introdução, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar.</span><span class="sxs-lookup"><span data-stu-id="98f90-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="98f90-111">O aplicativo de referência está disponível no repositório GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="98f90-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="98f90-112">Links de ação</span><span class="sxs-lookup"><span data-stu-id="98f90-112">Action links</span></span>

- <span data-ttu-id="98f90-113">Este e-book também está disponível em formato PDF (somente versão em inglês) [Download](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="98f90-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="98f90-114">Clone/Crie fork do aplicativo de referência [eShopOnContainers no GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="98f90-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="98f90-115">Assista ao [vídeo introdutório no Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="98f90-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="98f90-116">Conheça a [Arquitetura de Microsserviços](https://aka.ms/MicroservicesArchitecture) agora mesmo</span><span class="sxs-lookup"><span data-stu-id="98f90-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="98f90-117">Introdução</span><span class="sxs-lookup"><span data-stu-id="98f90-117">Introduction</span></span>

<span data-ttu-id="98f90-118">As empresas estão cada vez mais percebendo a economia de custo, resolvendo problemas de implantação e melhorando as operações de produção e de DevOps usando os contêineres.</span><span class="sxs-lookup"><span data-stu-id="98f90-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="98f90-119">A Microsoft tem lançando inovações de contêiner para Windows e Linux com a criação de produtos como o Serviço de Kubernetes do Azure e o Azure Service Fabric e por meio de parcerias com líderes do setor como a Docker, a Mesosphere e a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="98f90-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="98f90-120">Esses produtos oferecem soluções de contêiner que ajudam as empresas a criar e implantar aplicativos com a velocidade e a escala da nuvem, seja qual for a escolha de plataformas ou de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="98f90-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="98f90-121">O Docker está se tornando o verdadeiro padrão no setor de contêineres, com suporte dos fornecedores mais significativos nos ecossistemas do Windows e do Linux.</span><span class="sxs-lookup"><span data-stu-id="98f90-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="98f90-122">(A Microsoft é um dos principais fornecedores de nuvem que suportam o Docker.) No futuro, o Docker provavelmente será onipresente em qualquer datacenter na nuvem ou no local.</span><span class="sxs-lookup"><span data-stu-id="98f90-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="98f90-123">Além disso, a arquitetura de [microsserviços](https://martinfowler.com/articles/microservices.html) está despontando como uma abordagem importante para aplicativos críticos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="98f90-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="98f90-124">Em uma arquitetura baseada em microsserviço, o aplicativo é criado em uma coleção de serviços que podem ser desenvolvidos, testados, implantados e ter as versões controladas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="98f90-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="98f90-125">Sobre este guia</span><span class="sxs-lookup"><span data-stu-id="98f90-125">About this guide</span></span>

<span data-ttu-id="98f90-126">Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres.</span><span class="sxs-lookup"><span data-stu-id="98f90-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="98f90-127">Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f90-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="98f90-128">Para facilitar a introdução aos contêineres e microsserviços, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar.</span><span class="sxs-lookup"><span data-stu-id="98f90-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="98f90-129">O aplicativo de exemplo está disponível no repositório [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="98f90-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="98f90-130">Este guia fornece diretrizes básicas de desenvolvimento e de arquitetura principalmente no nível do ambiente de desenvolvimento com foco em duas tecnologias: Docker e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="98f90-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="98f90-131">Nossa intenção é que você leia este guia, ao pensar sobre o design do aplicativo sem focar a infraestrutura (nuvem ou local) do ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="98f90-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="98f90-132">Você tomará decisões sobre a infraestrutura mais tarde, quando criar seus aplicativos prontos para produção.</span><span class="sxs-lookup"><span data-stu-id="98f90-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="98f90-133">Portanto, este guia tem a intenção de ser independente da infraestrutura e mais centrado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="98f90-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="98f90-134">Depois de estudar este guia, a próxima etapa será saber mais sobre os microsserviços pronto para produção no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="98f90-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="98f90-135">Versão</span><span class="sxs-lookup"><span data-stu-id="98f90-135">Version</span></span>

<span data-ttu-id="98f90-136">Este guia foi revisado para cobrir a versão **.NET Core 3.1,** juntamente com muitas atualizações adicionais relacionadas à mesma "onda" de tecnologias (isto é, Azure e tecnologias adicionais de terceiros) coincidindo a tempo com a versão .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="98f90-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="98f90-137">É por isso que a versão do livro também foi atualizada para a versão **3.1**.</span><span class="sxs-lookup"><span data-stu-id="98f90-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="98f90-138">O que este guia não cobre</span><span class="sxs-lookup"><span data-stu-id="98f90-138">What this guide does not cover</span></span>

<span data-ttu-id="98f90-139">Este guia não se concentra no ciclo de vida do aplicativo, em DevOps, nos pipelines de CI/CD nem no trabalho da equipe.</span><span class="sxs-lookup"><span data-stu-id="98f90-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="98f90-140">O guia complementar [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft) trata desse assunto.</span><span class="sxs-lookup"><span data-stu-id="98f90-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="98f90-141">O guia atual também não fornece detalhes de implementação na infraestrutura do Azure, como informações sobre orquestradores específicos.</span><span class="sxs-lookup"><span data-stu-id="98f90-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="98f90-142">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="98f90-142">Additional resources</span></span>

- <span data-ttu-id="98f90-143">**Ciclo de vida do aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft** (livro eletrônico para download)</span><span class="sxs-lookup"><span data-stu-id="98f90-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="98f90-144">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="98f90-144">Who should use this guide</span></span>

<span data-ttu-id="98f90-145">Escrevemos este guia para desenvolvedores e arquitetos de solução que são novos no desenvolvimento de aplicativos com base no Docker e em arquitetura baseada em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="98f90-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="98f90-146">Este guia será indicado para você se desejar saber como arquitetar, projetar e implementar aplicativos de prova de conceito com tecnologias de desenvolvimento da Microsoft (com foco especial no .NET Core) e com contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f90-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="98f90-147">Esse guia também será útil se você for um tomador de decisões técnicas, como um arquiteto corporativo que deseja ter uma visão geral da arquitetura e da tecnologia antes de decidir qual abordagem selecionar para aplicativos distribuídos novos e modernos.</span><span class="sxs-lookup"><span data-stu-id="98f90-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="98f90-148">Como usar este guia</span><span class="sxs-lookup"><span data-stu-id="98f90-148">How to use this guide</span></span>

<span data-ttu-id="98f90-149">A primeira parte deste guia apresenta os contêineres do Docker, discute como escolher entre o .NET Core e o .NET Framework como estrutura de desenvolvimento e fornece uma visão geral sobre microsserviços.</span><span class="sxs-lookup"><span data-stu-id="98f90-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="98f90-150">Este conteúdo é para arquitetos e tomadores de decisões técnicas que desejam ter uma visão geral, mas que não precisam se concentrar nos detalhes da implementação de código.</span><span class="sxs-lookup"><span data-stu-id="98f90-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="98f90-151">A segunda parte do guia de começa com a seção [Processo de desenvolvimento de aplicativos baseados no Docker](./docker-application-development-process/index.md).</span><span class="sxs-lookup"><span data-stu-id="98f90-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="98f90-152">Ela se concentra nos padrões de desenvolvimento e de microsserviços para implementar aplicativos que usam o .NET Core e o Docker.</span><span class="sxs-lookup"><span data-stu-id="98f90-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="98f90-153">Esta seção será de interesse especial para desenvolvedores e arquitetos que desejam se concentrar no código, nos padrões e nos detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="98f90-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="98f90-154">Aplicativo de referência baseado em contêiner e em microsserviço: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="98f90-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="98f90-155">O aplicativo eShopOnContainers é um aplicativo de referência de software livre para .NET Core e microsserviços criado para ser implantado usando contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f90-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="98f90-156">O aplicativo é composto de vários subsistemas, incluindo vários front-ends de interface do usuário de loja virtual (um aplicativo Web MVC, um SPA Web e um aplicativo móvel nativo).</span><span class="sxs-lookup"><span data-stu-id="98f90-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="98f90-157">Ele também inclui os microsserviços e os contêineres de back-end de todas as operações do servidor necessárias.</span><span class="sxs-lookup"><span data-stu-id="98f90-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="98f90-158">A finalidade do aplicativo é demonstrar padrões de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="98f90-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="98f90-159">**A TI NÃO É UM MODELO PRONTO PARA PRODUÇÃO** para iniciar aplicativos de mundo real.</span><span class="sxs-lookup"><span data-stu-id="98f90-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="98f90-160">Na verdade, o aplicativo está em um estado beta permanente, porque também é usado para testar novas tecnologias potencialmente interessantes, à medida que aparecem.</span><span class="sxs-lookup"><span data-stu-id="98f90-160">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="98f90-161">Envie-nos seus comentários!</span><span class="sxs-lookup"><span data-stu-id="98f90-161">Send us your feedback!</span></span>

<span data-ttu-id="98f90-162">Escrevemos este guia para ajudá-lo a entender a arquitetura de aplicativos em contêineres e de microsserviços no .NET.</span><span class="sxs-lookup"><span data-stu-id="98f90-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="98f90-163">O guia e o aplicativo de referência relacionado continuarão sendo desenvolvidos, portanto seus comentários são bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="98f90-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="98f90-164">Se você tiver comentários sobre como este guia <https://aka.ms/ebookfeedback>pode ser melhorado, envie feedback em .</span><span class="sxs-lookup"><span data-stu-id="98f90-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="98f90-165">Credits</span><span class="sxs-lookup"><span data-stu-id="98f90-165">Credits</span></span>

<span data-ttu-id="98f90-166">Coautores:</span><span class="sxs-lookup"><span data-stu-id="98f90-166">Co-Authors:</span></span>

> <span data-ttu-id="98f90-167">**Cesar de la Torre**, Gerente sênior de produtos , equipe de produto do .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="98f90-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="98f90-168">**Bill Wagner**, Desenvolvedor sênior de conteúdo, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="98f90-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="98f90-169">**Mike Rousos**, Engenheiro de Software Principal, equipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="98f90-170">Editores:</span><span class="sxs-lookup"><span data-stu-id="98f90-170">Editors:</span></span>

> <span data-ttu-id="98f90-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="98f90-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="98f90-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="98f90-172">**Steve Hoag**</span></span>

<span data-ttu-id="98f90-173">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="98f90-173">Participants and reviewers:</span></span>

> <span data-ttu-id="98f90-174">**Jeffrey Richter**, engenheiro de software parceiro, equipe do Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-175">**Jimmy Bogard**, Arquiteto Chefe na Headspring</span><span class="sxs-lookup"><span data-stu-id="98f90-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="98f90-176">**Udi Dahan**, Fundador e CEO, Particular Software</span><span class="sxs-lookup"><span data-stu-id="98f90-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="98f90-177">**Jimmy Nilsson**, Cofundador e CEO da Factor10</span><span class="sxs-lookup"><span data-stu-id="98f90-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="98f90-178">**Glenn Condron**, Gerente sênior de programas, equipe do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="98f90-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="98f90-179">**Mark Fussell**, PM Líder Principal, equipe do Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-180">**Diego Vega**, PM Líder, equipe do Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-181">**Barry Dorrans**, gerente de programas de segurança sênior</span><span class="sxs-lookup"><span data-stu-id="98f90-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="98f90-182">**Rowan Miller**, Gerente sênior de programas, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="98f90-183">**Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-184">**Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-185">**Nish Anil**, Gerente de Programa Sênior, Equipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-186">**Dylan Reisenberger**, Arquiteto e Desenvolvedor Líder na Polly</span><span class="sxs-lookup"><span data-stu-id="98f90-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="98f90-187">**Steve "ardalis" Smith** – Arquiteto de software e instrutor – [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="98f90-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="98f90-188">**Cooper Ian**, Arquiteto de Codificação na Brighter</span><span class="sxs-lookup"><span data-stu-id="98f90-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="98f90-189">**Unai Zorrilla**, Arquiteto e Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="98f90-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="98f90-190">**Eduard Tomas**, Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="98f90-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="98f90-191">**Ramon Tomas**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="98f90-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="98f90-192">**David Sanz**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="98f90-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="98f90-193">**Javier Valero**, Diretor Executivo de Operações no Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="98f90-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="98f90-194">**Pierre Millet**, Consultor sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="98f90-195">**Michael Friis**, Gerente de Produto, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="98f90-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="98f90-196">**Charles Lowell**, Engenheiro de Software, equipe do VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="98f90-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="98f90-197">**Miguel Veloso**, Engenheiro de Desenvolvimento de Software na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="98f90-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="98f90-198">Direitos autorais</span><span class="sxs-lookup"><span data-stu-id="98f90-198">Copyright</span></span>

<span data-ttu-id="98f90-199">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="98f90-199">PUBLISHED BY</span></span>

<span data-ttu-id="98f90-200">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98f90-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="98f90-201">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="98f90-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="98f90-202">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="98f90-202">One Microsoft Way</span></span>

<span data-ttu-id="98f90-203">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="98f90-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="98f90-204">Copyright © 2020 pela Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="98f90-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="98f90-205">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="98f90-205">All rights reserved.</span></span> <span data-ttu-id="98f90-206">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="98f90-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="98f90-207">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="98f90-207">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="98f90-208">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="98f90-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="98f90-209"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="98f90-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="98f90-210">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="98f90-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="98f90-211">A Microsoft e as marcas comerciais listadas em <https://www.microsoft.com> na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98f90-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="98f90-212">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="98f90-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="98f90-213">O logotipo da baleia Docker é uma marca registrada da Docker, Inc. Usada por permissão.</span><span class="sxs-lookup"><span data-stu-id="98f90-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="98f90-214">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="98f90-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="98f90-215">Avançar</span><span class="sxs-lookup"><span data-stu-id="98f90-215">Next</span></span>](container-docker-introduction/index.md)
