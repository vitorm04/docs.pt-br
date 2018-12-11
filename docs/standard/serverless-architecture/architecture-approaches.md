---
title: Abordagens de arquitetura - aplicativos sem servidor
description: Uma introdução à arquitetura de abordagens para criar aplicativos corporativos baseados em nuvem, de arquiteturas de N camadas sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 04ad383586f974bb2dccc4623a9a254f5668dab4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126739"
---
# <a name="architecture-approaches"></a><span data-ttu-id="2b67c-103">Abordagens de arquitetura</span><span class="sxs-lookup"><span data-stu-id="2b67c-103">Architecture approaches</span></span>

<span data-ttu-id="2b67c-104">Noções básicas sobre as abordagens existentes para arquitetar aplicativos empresariais ajuda a esclarecer o papel desempenhado sem servidor.</span><span class="sxs-lookup"><span data-stu-id="2b67c-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="2b67c-105">Há muitas abordagens e padrões que evoluíram ao longo de décadas de desenvolvimento de software, e todas têm seus próprios prós e contras.</span><span class="sxs-lookup"><span data-stu-id="2b67c-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="2b67c-106">Em muitos casos, a solução definitiva não pode envolver a decidir sobre uma abordagem única, mas pode integrar várias abordagens.</span><span class="sxs-lookup"><span data-stu-id="2b67c-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="2b67c-107">Cenários de migração geralmente envolvem o deslocamento da abordagem de arquitetura de um para outro através de uma abordagem híbrida.</span><span class="sxs-lookup"><span data-stu-id="2b67c-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="2b67c-108">Este capítulo fornece uma visão geral de ambos os padrões de arquitetura lógica e física para aplicativos corporativos.</span><span class="sxs-lookup"><span data-stu-id="2b67c-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="2b67c-109">Padrões de arquitetura</span><span class="sxs-lookup"><span data-stu-id="2b67c-109">Architecture patterns</span></span>

<span data-ttu-id="2b67c-110">Aplicativos de negócios modernos siga uma variedade de padrões de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="2b67c-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="2b67c-111">Esta seção representa uma pesquisa de padrões comuns.</span><span class="sxs-lookup"><span data-stu-id="2b67c-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="2b67c-112">Os padrões listados aqui não são necessariamente todas as práticas recomendadas, mas ilustram diferentes abordagens.</span><span class="sxs-lookup"><span data-stu-id="2b67c-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="2b67c-113">Para obter mais informações, consulte [guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="2b67c-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="2b67c-114">Monolitos</span><span class="sxs-lookup"><span data-stu-id="2b67c-114">Monoliths</span></span>

<span data-ttu-id="2b67c-115">Muitos aplicativos de negócios seguem um padrão de monólito.</span><span class="sxs-lookup"><span data-stu-id="2b67c-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="2b67c-116">Os aplicativos herdados geralmente são implementados como monolitos.</span><span class="sxs-lookup"><span data-stu-id="2b67c-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="2b67c-117">No padrão de monólito, todas as preocupações de aplicativo estão contidas em uma única implantação.</span><span class="sxs-lookup"><span data-stu-id="2b67c-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="2b67c-118">Tudo, desde a interface do usuário para chamadas de banco de dados está incluído na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="2b67c-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Arquitetura de monólito](./media/monolith-architecture.png)

<span data-ttu-id="2b67c-120">Há várias vantagens para a abordagem de monólito.</span><span class="sxs-lookup"><span data-stu-id="2b67c-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="2b67c-121">Geralmente é mais fácil puxe para baixo de uma única base de código e começar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2b67c-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="2b67c-122">Tempo de aprendizado pode ser menor e criação de ambientes de teste é tão simple quanto fornecendo uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="2b67c-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="2b67c-123">O monolito pode ser projetado para incluir vários componentes e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2b67c-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="2b67c-124">Infelizmente, o padrão de monolito tende a dividir em grande escala.</span><span class="sxs-lookup"><span data-stu-id="2b67c-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="2b67c-125">Principais desvantagens da abordagem monólito incluem:</span><span class="sxs-lookup"><span data-stu-id="2b67c-125">Major disadvantages of the monolith approach include:</span></span>

* <span data-ttu-id="2b67c-126">Difícil de trabalhar em paralelo na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="2b67c-126">Difficult to work in parallel in the same code base.</span></span>
* <span data-ttu-id="2b67c-127">Qualquer alteração, não importa como trivial, exige a implantação de uma nova versão do aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="2b67c-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
* <span data-ttu-id="2b67c-128">Refatoração potencialmente afeta todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b67c-128">Refactoring potentially impacts the entire application.</span></span>
* <span data-ttu-id="2b67c-129">Geralmente a única solução para dimensionar é criar várias cópias de muitos recursos do monólito.</span><span class="sxs-lookup"><span data-stu-id="2b67c-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
* <span data-ttu-id="2b67c-130">Como expandir de sistemas ou adquiridos de outros sistemas, integração pode ser difícil.</span><span class="sxs-lookup"><span data-stu-id="2b67c-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
* <span data-ttu-id="2b67c-131">Pode ser difícil de testar devido à necessidade de configurar o monolito inteiro.</span><span class="sxs-lookup"><span data-stu-id="2b67c-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
* <span data-ttu-id="2b67c-132">Reutilização de código é um desafio e outros aplicativos acabam tendo suas próprias cópias do código.</span><span class="sxs-lookup"><span data-stu-id="2b67c-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="2b67c-133">Muitas empresas olham para a nuvem como uma oportunidade para migrar aplicativos monólito e ao mesmo tempo refatorá-los para mais padrões utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="2b67c-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="2b67c-134">É comum para quebrar a aplicativos individuais e componentes para permitir que eles possam ser mantida, implantados e dimensionados separadamente.</span><span class="sxs-lookup"><span data-stu-id="2b67c-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="2b67c-135">Aplicativos de N-camadas</span><span class="sxs-lookup"><span data-stu-id="2b67c-135">N-Layer applications</span></span>

<span data-ttu-id="2b67c-136">Lógica de aplicativo da partição de aplicativo de N camadas em camadas específicas.</span><span class="sxs-lookup"><span data-stu-id="2b67c-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="2b67c-137">As camadas mais comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="2b67c-137">The most common layers include:</span></span>

* <span data-ttu-id="2b67c-138">Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="2b67c-138">User interface</span></span>
* <span data-ttu-id="2b67c-139">lógica de negócios</span><span class="sxs-lookup"><span data-stu-id="2b67c-139">Business logic</span></span>
* <span data-ttu-id="2b67c-140">Acesso aos dados</span><span class="sxs-lookup"><span data-stu-id="2b67c-140">Data access</span></span>

<span data-ttu-id="2b67c-141">Outras camadas podem incluir o middleware, processamento em lotes e API.</span><span class="sxs-lookup"><span data-stu-id="2b67c-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="2b67c-142">É importante observar que as camadas são lógicas.</span><span class="sxs-lookup"><span data-stu-id="2b67c-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="2b67c-143">Embora elas são desenvolvidas em isolamento, eles podem todos ser implantados para a mesma plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="2b67c-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Arquitetura de N-camadas](./media/n-layer-architecture.png)

<span data-ttu-id="2b67c-145">Há várias vantagens para a abordagem de N-camadas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="2b67c-145">There are several advantages to the N-Layer approach, including:</span></span>

* <span data-ttu-id="2b67c-146">Refatoração é isolada em uma camada.</span><span class="sxs-lookup"><span data-stu-id="2b67c-146">Refactoring is isolated to a layer.</span></span>
* <span data-ttu-id="2b67c-147">As equipes de forma independente podem criar, testar, implantar e manter a camadas separadas.</span><span class="sxs-lookup"><span data-stu-id="2b67c-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
* <span data-ttu-id="2b67c-148">Camadas podem ser alternadas, por exemplo a camada de dados pode acessar vários bancos de dados sem a necessidade de alterações para a camada de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2b67c-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="2b67c-149">Sem servidor pode ser usada para implementar uma ou mais camadas.</span><span class="sxs-lookup"><span data-stu-id="2b67c-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="2b67c-150">Microsserviços</span><span class="sxs-lookup"><span data-stu-id="2b67c-150">Microservices</span></span>

<span data-ttu-id="2b67c-151">**[Microsserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  arquiteturas contêm características comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="2b67c-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

* <span data-ttu-id="2b67c-152">Aplicativos são compostos por vários serviços pequenos.</span><span class="sxs-lookup"><span data-stu-id="2b67c-152">Applications are composed of several small services.</span></span>
* <span data-ttu-id="2b67c-153">Cada serviço é executado em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="2b67c-153">Each service runs in its own process.</span></span>
* <span data-ttu-id="2b67c-154">Os serviços são alinhados em torno de domínios de negócios.</span><span class="sxs-lookup"><span data-stu-id="2b67c-154">Services are aligned around business domains.</span></span>
* <span data-ttu-id="2b67c-155">Os serviços se comunicam por APIs leves, normalmente usando HTTP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="2b67c-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
* <span data-ttu-id="2b67c-156">Serviços podem ser implantados e atualizados independentemente.</span><span class="sxs-lookup"><span data-stu-id="2b67c-156">Services can be deployed and upgraded independently.</span></span>
* <span data-ttu-id="2b67c-157">Os serviços não são dependentes de um único armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="2b67c-157">Services aren't dependent on a single data store.</span></span>
* <span data-ttu-id="2b67c-158">O sistema foi projetado com falha em mente e o aplicativo poderá ser executado mesmo quando determinados serviços falham.</span><span class="sxs-lookup"><span data-stu-id="2b67c-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="2b67c-159">Microsserviços não precisam ser mutuamente exclusivos para outras abordagens de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="2b67c-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="2b67c-160">Por exemplo, uma arquitetura de N camadas pode usar microsserviços para a camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="2b67c-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="2b67c-161">Também é possível implementar microsserviços em uma variedade de maneiras de diretórios virtuais em hosts do IIS para contêineres.</span><span class="sxs-lookup"><span data-stu-id="2b67c-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="2b67c-162">As características dos microsserviços tornam especialmente ideais para implementações sem servidor.</span><span class="sxs-lookup"><span data-stu-id="2b67c-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Arquitetura de microsserviços](./media/microservices-architecture.png)

<span data-ttu-id="2b67c-164">Os profissionais de arquiteturas de microsserviços incluem:</span><span class="sxs-lookup"><span data-stu-id="2b67c-164">The pros of microservices architectures include:</span></span>

* <span data-ttu-id="2b67c-165">Refatoração geralmente é isolada em um único serviço.</span><span class="sxs-lookup"><span data-stu-id="2b67c-165">Refactoring is often isolated to a single service.</span></span>
* <span data-ttu-id="2b67c-166">Os serviços podem ser atualizados independentemente uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="2b67c-166">Services can be upgraded independently of each other.</span></span>
* <span data-ttu-id="2b67c-167">Resiliência e a elasticidade podem ser ajustados à demanda de serviços individuais.</span><span class="sxs-lookup"><span data-stu-id="2b67c-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
* <span data-ttu-id="2b67c-168">Desenvolvimento pode ocorrer em paralelo entre plataformas e equipes diferentes.</span><span class="sxs-lookup"><span data-stu-id="2b67c-168">Development can happen in parallel across disparate teams and platforms.</span></span>
* <span data-ttu-id="2b67c-169">É mais fácil escrever testes abrangentes para os serviços isolados.</span><span class="sxs-lookup"><span data-stu-id="2b67c-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="2b67c-170">Microsserviços vêm com seus próprios desafios, incluindo:</span><span class="sxs-lookup"><span data-stu-id="2b67c-170">Microservices come with their own challenges, including:</span></span>

* <span data-ttu-id="2b67c-171">Determinando quais serviços estão disponíveis e como chamá-los.</span><span class="sxs-lookup"><span data-stu-id="2b67c-171">Determining what services are available and how to call them.</span></span>
* <span data-ttu-id="2b67c-172">Gerenciando o ciclo de vida de serviços.</span><span class="sxs-lookup"><span data-stu-id="2b67c-172">Managing the lifecycle of services.</span></span>
* <span data-ttu-id="2b67c-173">Noções básicas sobre como os serviços se encaixam no aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="2b67c-173">Understanding how services fit together in the overall application.</span></span>
* <span data-ttu-id="2b67c-174">Testes de sistema completo de chamadas feitas entre diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="2b67c-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="2b67c-175">Finalmente, há soluções para atender a todos esses desafios, incluindo tocar os benefícios sem servidor que serão discutidos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="2b67c-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b67c-176">[Anterior](index.md)
>[Próximo](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="2b67c-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>