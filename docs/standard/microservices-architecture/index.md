---
title: Microsserviços do .NET. Arquitetura de aplicativos .NET em contêineres
description: Arquitetura de microsserviços do .NET para aplicativos do .NET em contêineres | Microsserviços são serviços implantáveis de maneira modular e independente. Os contêineres do Docker (para Linux e Windows) simplificam a implantação e o teste ao agrupar um serviço e suas dependências em uma única unidade, que será executada em um ambiente isolado.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 58bb915c825cd69c68b3955573145ae6a1b1a6e4
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231415"
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="10d79-105">Microsserviços do .NET.</span><span class="sxs-lookup"><span data-stu-id="10d79-105">.NET Microservices.</span></span> <span data-ttu-id="10d79-106">Arquitetura de aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="10d79-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="10d79-107">DOWNLOAD disponível em: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="10d79-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="10d79-108">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="10d79-108">PUBLISHED BY</span></span>

<span data-ttu-id="10d79-109">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10d79-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="10d79-110">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="10d79-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="10d79-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="10d79-111">One Microsoft Way</span></span>

<span data-ttu-id="10d79-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="10d79-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="10d79-113">Copyright © 2018, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="10d79-113">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="10d79-114">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="10d79-114">All rights reserved.</span></span> <span data-ttu-id="10d79-115">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="10d79-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="10d79-116">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="10d79-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="10d79-117">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="10d79-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="10d79-118">Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="10d79-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="10d79-119">Nenhuma associação ou conexão real é intencional ou deve ser deduzida.</span><span class="sxs-lookup"><span data-stu-id="10d79-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="10d79-120">A Microsoft e as marcas comerciais listadas em http://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="10d79-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="10d79-121">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="10d79-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="10d79-122">O logotipo de baleia do Docker é uma marca registrada da Docker, Inc. usado mediante permissão.</span><span class="sxs-lookup"><span data-stu-id="10d79-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="10d79-123">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="10d79-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="10d79-124">Coautores:</span><span class="sxs-lookup"><span data-stu-id="10d79-124">Co-Authors:</span></span>

> <span data-ttu-id="10d79-125">**Cesar de la Torre**. PM Sênior, equipe do produto .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="10d79-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="10d79-126">**Bill Wagner**. Desenvolvedor de Conteúdo Sênior, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="10d79-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="10d79-127">**Mike Rousos**, Engenheiro de Software Principal, equipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="10d79-128">Editores:</span><span class="sxs-lookup"><span data-stu-id="10d79-128">Editors:</span></span>

> <span data-ttu-id="10d79-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="10d79-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="10d79-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="10d79-130">**Steve Hoag**</span></span>

<span data-ttu-id="10d79-131">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="10d79-131">Participants and reviewers:</span></span>

> <span data-ttu-id="10d79-132">**Jeffrey Richter**, engenheiro de software parceiro, equipe do Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-132">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="10d79-133">**Jimmy Bogard**, Arquiteto Chefe na Headspring</span><span class="sxs-lookup"><span data-stu-id="10d79-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="10d79-134">**Udi Dahan**, Fundador e CEO, Particular Software</span><span class="sxs-lookup"><span data-stu-id="10d79-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="10d79-135">**Jimmy Nilsson**, Cofundador e CEO da Factor10</span><span class="sxs-lookup"><span data-stu-id="10d79-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="10d79-136">**Glenn Condron**. Gerente de Programa Sênior, equipe do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="10d79-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="10d79-137">**Mark Fussell**, PM Líder Principal, equipe do Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="10d79-138">**Diego Vega**, PM Líder, equipe do Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="10d79-139">**Barry Dorrans**. Gerente de Programa de Segurança Sênior</span><span class="sxs-lookup"><span data-stu-id="10d79-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="10d79-140">**Rowan Miller**. Gerente de Programa Sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="10d79-141">**Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="10d79-142">**Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="10d79-143">**Dylan Reisenberger**, Arquiteto e Desenvolvedor Líder na Polly</span><span class="sxs-lookup"><span data-stu-id="10d79-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="10d79-144">**Steve Smith**, Especialista e Instrutor em Software na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="10d79-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="10d79-145">**Cooper Ian**, Arquiteto de Codificação na Brighter</span><span class="sxs-lookup"><span data-stu-id="10d79-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="10d79-146">**Unai Zorrilla**, Arquiteto e Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="10d79-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="10d79-147">**Eduard Tomas**, Desenvolvedor Líder na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="10d79-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="10d79-148">**Ramon Tomas**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="10d79-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="10d79-149">**David Sanz**, Desenvolvedor na Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="10d79-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="10d79-150">**Javier Valero**, Diretor Executivo de Operações no Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="10d79-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="10d79-151">**Pedro milho**. Consultor Sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="10d79-152">**Michael Friis**, Gerente de Produto, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="10d79-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="10d79-153">**Charles Lowell**, Engenheiro de Software, equipe do VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="10d79-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="10d79-154">Introdução</span><span class="sxs-lookup"><span data-stu-id="10d79-154">Introduction</span></span>

<span data-ttu-id="10d79-155">As empresas estão cada vez mais percebendo a economia de custo, resolvendo problemas de implantação e melhorando as operações de produção e de DevOps usando os contêineres.</span><span class="sxs-lookup"><span data-stu-id="10d79-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="10d79-156">A Microsoft tem lançando inovações de contêiner para Windows e Linux com a criação de produtos como o Serviço de Contêiner do Azure e o Azure Service Fabric e por meio de parcerias com líderes do setor como a Docker, a Mesosphere e a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="10d79-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="10d79-157">Esses produtos oferecem soluções de contêiner que ajudam as empresas a criar e implantar aplicativos com a velocidade e a escala da nuvem, seja qual for a escolha de plataformas ou de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="10d79-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="10d79-158">O Docker está se tornando o verdadeiro padrão no setor de contêineres, com suporte dos fornecedores mais significativos nos ecossistemas do Windows e do Linux.</span><span class="sxs-lookup"><span data-stu-id="10d79-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="10d79-159">(A Microsoft é um dos principais fornecedores de nuvem com suporte para o Docker). No futuro, o Docker provavelmente será onipresente em qualquer datacenter na nuvem ou local.</span><span class="sxs-lookup"><span data-stu-id="10d79-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="10d79-160">Além disso, a arquitetura de [microsserviços](https://martinfowler.com/articles/microservices.html) está despontando como uma abordagem importante para aplicativos críticos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="10d79-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="10d79-161">Em uma arquitetura baseada em microsserviço, o aplicativo é criado em uma coleção de serviços que podem ser desenvolvidos, testados, implantados e ter as versões controladas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="10d79-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="10d79-162">Sobre este guia</span><span class="sxs-lookup"><span data-stu-id="10d79-162">About this guide</span></span>

<span data-ttu-id="10d79-163">Este guia é uma introdução ao desenvolvimento de aplicativos com base em microsserviços e ao gerenciamento deles usando contêineres.</span><span class="sxs-lookup"><span data-stu-id="10d79-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="10d79-164">Ele discute as abordagens de design de arquitetura e de implementação usando o .NET Core e os contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="10d79-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="10d79-165">Para facilitar a introdução aos contêineres e microsserviços, o guia concentra-se em um aplicativo de referência em contêineres e baseado em microsserviços que você pode explorar.</span><span class="sxs-lookup"><span data-stu-id="10d79-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="10d79-166">O aplicativo de exemplo está disponível no repositório [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="10d79-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="10d79-167">Este guia fornece diretrizes básicas de desenvolvimento e de arquitetura principalmente no nível do ambiente de desenvolvimento com foco em duas tecnologias: Docker e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10d79-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="10d79-168">Nossa intenção é que você leia este guia, ao pensar sobre o design do aplicativo sem focar a infraestrutura (nuvem ou local) do ambiente de produção.</span><span class="sxs-lookup"><span data-stu-id="10d79-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="10d79-169">Você tomará decisões sobre a infraestrutura mais tarde, quando criar seus aplicativos prontos para produção.</span><span class="sxs-lookup"><span data-stu-id="10d79-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="10d79-170">Portanto, este guia tem a intenção de ser independente da infraestrutura e mais centrado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="10d79-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="10d79-171">Depois de estudar este guia, a próxima etapa será saber mais sobre os microsserviços pronto para produção no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="10d79-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="10d79-172">O que este guia não cobre</span><span class="sxs-lookup"><span data-stu-id="10d79-172">What this guide does not cover</span></span>

<span data-ttu-id="10d79-173">Este guia não se concentra no ciclo de vida do aplicativo, em DevOps, nos pipelines de CI/CD nem no trabalho da equipe.</span><span class="sxs-lookup"><span data-stu-id="10d79-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="10d79-174">O guia complementar [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft) trata desse assunto.</span><span class="sxs-lookup"><span data-stu-id="10d79-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="10d79-175">O guia atual também não fornece detalhes de implementação na infraestrutura do Azure, como informações sobre orquestradores específicos.</span><span class="sxs-lookup"><span data-stu-id="10d79-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="10d79-176">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="10d79-176">Additional resources</span></span>

-   <span data-ttu-id="10d79-177">**Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft** (e-book para download)[*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="10d79-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="10d79-178">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="10d79-178">Who should use this guide</span></span>

<span data-ttu-id="10d79-179">Escrevemos este guia para desenvolvedores e arquitetos de solução que são novos no desenvolvimento de aplicativos com base no Docker e em arquitetura baseada em microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10d79-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="10d79-180">Este guia será indicado para você se desejar saber como arquitetar, projetar e implementar aplicativos de prova de conceito com tecnologias de desenvolvimento da Microsoft (com foco especial no .NET Core) e com contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="10d79-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="10d79-181">Esse guia também será útil se você for um tomador de decisões técnicas, como um arquiteto corporativo que deseja ter uma visão geral da arquitetura e da tecnologia antes de decidir qual abordagem selecionar para aplicativos distribuídos novos e modernos.</span><span class="sxs-lookup"><span data-stu-id="10d79-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="10d79-182">Como usar este guia</span><span class="sxs-lookup"><span data-stu-id="10d79-182">How to use this guide</span></span>

<span data-ttu-id="10d79-183">A primeira parte deste guia apresenta os contêineres do Docker, discute como escolher entre o .NET Core e o .NET Framework como estrutura de desenvolvimento e fornece uma visão geral sobre microsserviços.</span><span class="sxs-lookup"><span data-stu-id="10d79-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="10d79-184">Este conteúdo é para arquitetos e tomadores de decisões técnicas que desejam ter uma visão geral, mas que não precisam se concentrar nos detalhes da implementação de código.</span><span class="sxs-lookup"><span data-stu-id="10d79-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="10d79-185">A segunda parte do guia de começa com a seção [Processo de desenvolvimento de aplicativos baseados no Docker](#ch_dev_process_for_docker_based_apps).</span><span class="sxs-lookup"><span data-stu-id="10d79-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="10d79-186">Ela se concentra nos padrões de desenvolvimento e de microsserviços para implementar aplicativos que usam o .NET Core e o Docker.</span><span class="sxs-lookup"><span data-stu-id="10d79-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="10d79-187">Esta seção será de interesse especial para desenvolvedores e arquitetos que desejam se concentrar no código, nos padrões e nos detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="10d79-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="10d79-188">Aplicativo de referência baseado em contêiner e em microsserviço: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="10d79-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="10d79-189">O aplicativo eShopOnContainers é um aplicativo de referência do .NET Core e de microsserviços que foi projetado para ser implantado usando contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="10d79-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="10d79-190">O aplicativo consiste em vários subsistemas, incluindo vários front-ends de interface do usuário de loja virtual (um aplicativo Web e um aplicativo móvel nativo).</span><span class="sxs-lookup"><span data-stu-id="10d79-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="10d79-191">Ele também inclui os microsserviços e os contêineres de back-end de todas as operações do servidor necessárias.</span><span class="sxs-lookup"><span data-stu-id="10d79-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="10d79-192">O código-fonte desse aplicativo baseado em contêineres e de microsserviço é de software livre e está disponível no repositório [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="10d79-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="10d79-193">Envie-nos seus comentários!</span><span class="sxs-lookup"><span data-stu-id="10d79-193">Send us your feedback!</span></span>

<span data-ttu-id="10d79-194">Escrevemos este guia para ajudá-lo a entender a arquitetura de aplicativos em contêineres e de microsserviços no .NET.</span><span class="sxs-lookup"><span data-stu-id="10d79-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="10d79-195">O guia e o aplicativo de referência relacionado continuarão sendo desenvolvidos, portanto seus comentários são bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="10d79-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="10d79-196">Se você tiver comentários sobre como este guia poderá ser melhorado, envie-os para:</span><span class="sxs-lookup"><span data-stu-id="10d79-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="10d79-197">[Next] (container-docker-introduction/index.md)</span><span class="sxs-lookup"><span data-stu-id="10d79-197">[Next] (container-docker-introduction/index.md)</span></span>
