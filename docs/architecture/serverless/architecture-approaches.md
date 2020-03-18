---
title: Abordagens de arquitetura - Aplicativos sem servidor
description: Uma introdução às abordagens de arquitetura para criar aplicativos corporativos baseados em nuvem, desde arquiteturas n-tier até sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522902"
---
# <a name="architecture-approaches"></a><span data-ttu-id="4a986-103">Abordagens de arquitetura</span><span class="sxs-lookup"><span data-stu-id="4a986-103">Architecture approaches</span></span>

<span data-ttu-id="4a986-104">Entender as abordagens existentes para arquitetar aplicativos corporativos ajuda a esclarecer o papel desempenhado por sem servidor.</span><span class="sxs-lookup"><span data-stu-id="4a986-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="4a986-105">Existem muitas abordagens e padrões que evoluíram ao longo de décadas de desenvolvimento de software, e todos têm seus próprios prós e contras.</span><span class="sxs-lookup"><span data-stu-id="4a986-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="4a986-106">Em muitos casos, a solução final pode não envolver a decisão de uma única abordagem, mas pode integrar várias abordagens.</span><span class="sxs-lookup"><span data-stu-id="4a986-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="4a986-107">Os cenários de migração geralmente envolvem a mudança de uma abordagem de arquitetura para outra através de uma abordagem híbrida.</span><span class="sxs-lookup"><span data-stu-id="4a986-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="4a986-108">Este capítulo fornece uma visão geral dos padrões de arquitetura lógica e física para aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="4a986-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="4a986-109">Padrões de arquitetura</span><span class="sxs-lookup"><span data-stu-id="4a986-109">Architecture patterns</span></span>

<span data-ttu-id="4a986-110">Aplicações de negócios modernas seguem uma variedade de padrões de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="4a986-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="4a986-111">Esta seção representa um levantamento de padrões comuns.</span><span class="sxs-lookup"><span data-stu-id="4a986-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="4a986-112">Os padrões listados aqui não são necessariamente todas as melhores práticas, mas ilustram diferentes abordagens.</span><span class="sxs-lookup"><span data-stu-id="4a986-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="4a986-113">Para obter mais informações, consulte [o guia de arquitetura de aplicativos do Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="4a986-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="4a986-114">Monólitos</span><span class="sxs-lookup"><span data-stu-id="4a986-114">Monoliths</span></span>

<span data-ttu-id="4a986-115">Muitas aplicações de negócios seguem um padrão de monólito.</span><span class="sxs-lookup"><span data-stu-id="4a986-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="4a986-116">Os aplicativos legados são frequentemente implementados como monólitos.</span><span class="sxs-lookup"><span data-stu-id="4a986-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="4a986-117">No padrão do monólito, todas as preocupações com a aplicação estão contidas em uma única implantação.</span><span class="sxs-lookup"><span data-stu-id="4a986-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="4a986-118">Tudo, desde a interface do usuário até as chamadas de banco de dados, está incluído na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="4a986-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Arquitetura monolito](./media/monolith-architecture.png)

<span data-ttu-id="4a986-120">Há várias vantagens para a abordagem do monolito.</span><span class="sxs-lookup"><span data-stu-id="4a986-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="4a986-121">Muitas vezes é fácil puxar para baixo uma única base de código e começar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="4a986-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="4a986-122">O tempo de rampa pode ser menor, e criar ambientes de teste é tão simples quanto fornecer uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="4a986-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="4a986-123">O monólito pode ser projetado para incluir vários componentes e aplicações.</span><span class="sxs-lookup"><span data-stu-id="4a986-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="4a986-124">Infelizmente, o padrão do monólito tende a quebrar em escala.</span><span class="sxs-lookup"><span data-stu-id="4a986-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="4a986-125">As principais desvantagens da abordagem do monolito incluem:</span><span class="sxs-lookup"><span data-stu-id="4a986-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="4a986-126">Difícil trabalhar em paralelo na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="4a986-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="4a986-127">Qualquer mudança, por mais trivial que seja, requer a implantação de uma nova versão de todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a986-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="4a986-128">A refatoração impacta potencialmente toda a aplicação.</span><span class="sxs-lookup"><span data-stu-id="4a986-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="4a986-129">Muitas vezes, a única solução para escalar é criar cópias múltiplas e intensivas em recursos do monólito.</span><span class="sxs-lookup"><span data-stu-id="4a986-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="4a986-130">À medida que os sistemas se expandem ou outros sistemas são adquiridos, a integração pode ser difícil.</span><span class="sxs-lookup"><span data-stu-id="4a986-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="4a986-131">Pode ser difícil testar devido à necessidade de configurar todo o monólito.</span><span class="sxs-lookup"><span data-stu-id="4a986-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="4a986-132">O reaproveitamento de códigos é desafiador e muitas vezes outros aplicativos acabam tendo suas próprias cópias de código.</span><span class="sxs-lookup"><span data-stu-id="4a986-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="4a986-133">Muitas empresas olham para a nuvem como uma oportunidade de migrar aplicativos de monolito e, ao mesmo tempo, refatorá-los para padrões mais utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="4a986-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="4a986-134">É comum quebrar os aplicativos e componentes individuais para permitir que sejam mantidos, implantados e dimensionados separadamente.</span><span class="sxs-lookup"><span data-stu-id="4a986-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="4a986-135">Aplicativos N-Layer</span><span class="sxs-lookup"><span data-stu-id="4a986-135">N-Layer applications</span></span>

<span data-ttu-id="4a986-136">Lógica do aplicativo de partição de aplicativo de camada n em camadas específicas.</span><span class="sxs-lookup"><span data-stu-id="4a986-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="4a986-137">As camadas mais comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="4a986-137">The most common layers include:</span></span>

- <span data-ttu-id="4a986-138">Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="4a986-138">User interface</span></span>
- <span data-ttu-id="4a986-139">Lógica de negócios</span><span class="sxs-lookup"><span data-stu-id="4a986-139">Business logic</span></span>
- <span data-ttu-id="4a986-140">Acesso de dados</span><span class="sxs-lookup"><span data-stu-id="4a986-140">Data access</span></span>

<span data-ttu-id="4a986-141">Outras camadas podem incluir middleware, processamento de lotes e API.</span><span class="sxs-lookup"><span data-stu-id="4a986-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="4a986-142">É importante notar que as camadas são lógicas.</span><span class="sxs-lookup"><span data-stu-id="4a986-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="4a986-143">Embora sejam desenvolvidos isoladamente, podem ser todos implantados na mesma plataforma alvo.</span><span class="sxs-lookup"><span data-stu-id="4a986-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Arquitetura N-Camada](./media/n-layer-architecture.png)

<span data-ttu-id="4a986-145">Existem várias vantagens para a abordagem N-Layer, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4a986-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="4a986-146">A refatoração é isolada a uma camada.</span><span class="sxs-lookup"><span data-stu-id="4a986-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="4a986-147">As equipes podem construir, testar, implantar e manter camadas separadas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="4a986-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="4a986-148">As camadas podem ser trocadas, por exemplo, a camada de dados pode acessar vários bancos de dados sem exigir alterações na camada de IA.</span><span class="sxs-lookup"><span data-stu-id="4a986-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="4a986-149">Sem servidor pode ser usado para implementar uma ou mais camadas.</span><span class="sxs-lookup"><span data-stu-id="4a986-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="4a986-150">Microsserviços</span><span class="sxs-lookup"><span data-stu-id="4a986-150">Microservices</span></span>

<span data-ttu-id="4a986-151">**[As arquiteturas de microserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** contêm características comuns que incluem:</span><span class="sxs-lookup"><span data-stu-id="4a986-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="4a986-152">As aplicações são compostas por vários pequenos serviços.</span><span class="sxs-lookup"><span data-stu-id="4a986-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="4a986-153">Cada serviço é executado em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="4a986-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="4a986-154">Os serviços estão alinhados em torno de domínios de negócios.</span><span class="sxs-lookup"><span data-stu-id="4a986-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="4a986-155">Os serviços se comunicam através de APIs leves, normalmente usando HTTP como transporte.</span><span class="sxs-lookup"><span data-stu-id="4a986-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="4a986-156">Os serviços podem ser implantados e atualizados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="4a986-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="4a986-157">Os serviços não dependem de um único armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="4a986-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="4a986-158">O sistema é projetado com falha em mente, e o aplicativo ainda pode ser executado mesmo quando certos serviços falham.</span><span class="sxs-lookup"><span data-stu-id="4a986-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="4a986-159">Os microserviços não têm que ser mutuamente exclusivos de outras abordagens de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="4a986-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="4a986-160">Por exemplo, uma arquitetura N-Tier pode usar microsserviços para o nível intermediário.</span><span class="sxs-lookup"><span data-stu-id="4a986-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="4a986-161">Também é possível implementar microsserviços de várias maneiras, desde diretórios virtuais em hosts IIS até contêineres.</span><span class="sxs-lookup"><span data-stu-id="4a986-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="4a986-162">As características dos microserviços os tornam especialmente ideais para implementações sem servidor.</span><span class="sxs-lookup"><span data-stu-id="4a986-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Arquitetura de microsserviços](./media/microservices-architecture.png)

<span data-ttu-id="4a986-164">Os prós das arquiteturas de microsserviços incluem:</span><span class="sxs-lookup"><span data-stu-id="4a986-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="4a986-165">A refatoração é muitas vezes isolada a um único serviço.</span><span class="sxs-lookup"><span data-stu-id="4a986-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="4a986-166">Os serviços podem ser atualizados independentemente uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="4a986-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="4a986-167">A resiliência e a elasticidade podem estar sintonizadas com as demandas dos serviços individuais.</span><span class="sxs-lookup"><span data-stu-id="4a986-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="4a986-168">O desenvolvimento pode acontecer em paralelo entre equipes e plataformas diferentes.</span><span class="sxs-lookup"><span data-stu-id="4a986-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="4a986-169">É mais fácil escrever testes abrangentes para serviços isolados.</span><span class="sxs-lookup"><span data-stu-id="4a986-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="4a986-170">Os microserviços vêm com seus próprios desafios, incluindo:</span><span class="sxs-lookup"><span data-stu-id="4a986-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="4a986-171">Determinando quais serviços estão disponíveis e como chamá-los.</span><span class="sxs-lookup"><span data-stu-id="4a986-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="4a986-172">Gerenciando o ciclo de vida dos serviços.</span><span class="sxs-lookup"><span data-stu-id="4a986-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="4a986-173">Entender como os serviços se encaixam na aplicação geral.</span><span class="sxs-lookup"><span data-stu-id="4a986-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="4a986-174">Teste completo do sistema de chamadas feitas em serviços diferentes.</span><span class="sxs-lookup"><span data-stu-id="4a986-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="4a986-175">Em última análise, existem soluções para enfrentar todos esses desafios, incluindo aproveitar os benefícios dos sem servidor que são discutidos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="4a986-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4a986-176">[Próximo](index.md)
>[anterior](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="4a986-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
