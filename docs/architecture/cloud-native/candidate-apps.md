---
title: Aplicativos candidatos para nuvem nativa
description: Saiba quais tipos de aplicativos se beneficiam de uma abordagem nativa de nuvem
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 127dca45ce8a5e025ca7511e6513afffe64e592d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087685"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="38c4b-103">Aplicativos candidatos para nuvem nativa</span><span class="sxs-lookup"><span data-stu-id="38c4b-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="38c4b-104">Examine os aplicativos em seu portfólio.</span><span class="sxs-lookup"><span data-stu-id="38c4b-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="38c4b-105">Quantas delas se qualificam para uma arquitetura nativa de nuvem?</span><span class="sxs-lookup"><span data-stu-id="38c4b-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="38c4b-106">Todos eles?</span><span class="sxs-lookup"><span data-stu-id="38c4b-106">All of them?</span></span> <span data-ttu-id="38c4b-107">Talvez alguns?</span><span class="sxs-lookup"><span data-stu-id="38c4b-107">Perhaps some?</span></span>

<span data-ttu-id="38c4b-108">Aplicando uma análise de custo/benefício, há uma boa chance de que a maioria não dê suporte à marca de preço pesada necessária para ser nativa na nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="38c4b-109">O custo de ser nativo na nuvem excedeu muito o valor comercial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38c4b-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="38c4b-110">Que tipo de aplicativo pode ser um candidato para a nuvem nativa?</span><span class="sxs-lookup"><span data-stu-id="38c4b-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="38c4b-111">Um sistema empresarial grande e estratégico que precisa desenvolver constantemente recursos/recursos de negócios</span><span class="sxs-lookup"><span data-stu-id="38c4b-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="38c4b-112">Um aplicativo que requer uma velocidade de liberação alta – com alta confiança</span><span class="sxs-lookup"><span data-stu-id="38c4b-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="38c4b-113">Um sistema com o qual os recursos individuais devem ser liberados *sem* uma reimplantação completa de todo o sistema</span><span class="sxs-lookup"><span data-stu-id="38c4b-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="38c4b-114">Um aplicativo desenvolvido por equipes com experiência em diferentes pilhas de tecnologia</span><span class="sxs-lookup"><span data-stu-id="38c4b-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="38c4b-115">Um aplicativo com componentes que devem ser dimensionados de forma independente</span><span class="sxs-lookup"><span data-stu-id="38c4b-115">An application with components that must scale independently</span></span>

<span data-ttu-id="38c4b-116">Em seguida, há sistemas herdados.</span><span class="sxs-lookup"><span data-stu-id="38c4b-116">Then there are legacy systems.</span></span> <span data-ttu-id="38c4b-117">Embora todos gostaríamos de criar novos aplicativos, muitas vezes somos responsáveis por modernizar cargas de trabalho herdadas que são críticas para os negócios.</span><span class="sxs-lookup"><span data-stu-id="38c4b-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="38c4b-118">Ao longo do tempo, um aplicativo herdado poderia ser decomposto em microserviços, em contêineres e, por fim, "replataforma" em uma arquitetura nativa de nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="38c4b-119">Modernizando aplicativos herdados</span><span class="sxs-lookup"><span data-stu-id="38c4b-119">Modernizing legacy apps</span></span>

<span data-ttu-id="38c4b-120">O Microsoft e-book gratuito [modernizar aplicativos .net existentes com a nuvem do Azure e contêineres do Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fornece orientação para migrar cargas de trabalho locais para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="38c4b-121">A Figura 1-10 mostra que não há uma estratégia única de um único tamanho para modernizar aplicativos herdados.</span><span class="sxs-lookup"><span data-stu-id="38c4b-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Estratégias para migrar cargas de trabalho herdadas](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="38c4b-123">**Figura 1-10**.</span><span class="sxs-lookup"><span data-stu-id="38c4b-123">**Figure 1-10**.</span></span> <span data-ttu-id="38c4b-124">Estratégias para migrar cargas de trabalho herdadas</span><span class="sxs-lookup"><span data-stu-id="38c4b-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="38c4b-125">Aplicativos monolíticos que não são críticos amplamente se beneficiam de uma migração rápida de comparação de precisão e mudança ([pronta para a infraestrutura de nuvem](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)).</span><span class="sxs-lookup"><span data-stu-id="38c4b-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)) migration.</span></span> <span data-ttu-id="38c4b-126">Aqui, a carga de trabalho local é rehospedada para uma VM baseada em nuvem, sem alterações.</span><span class="sxs-lookup"><span data-stu-id="38c4b-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="38c4b-127">Essa abordagem usa o [modelo IaaS (infraestrutura como serviço)](https://azure.microsoft.com/overview/what-is-iaas/).</span><span class="sxs-lookup"><span data-stu-id="38c4b-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="38c4b-128">O Azure inclui várias ferramentas como ([migrações para Azure](https://aka.ms/azuremigrate), [Azure site Recovery](https://azure.microsoft.com/services/site-recovery/)e serviço de migração de [banco de dados do Azure](https://azure.microsoft.com/campaigns/database-migration/)) para facilitar a movimentação.</span><span class="sxs-lookup"><span data-stu-id="38c4b-128">Azure includes several tools such as ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)) to make such a move easier.</span></span> <span data-ttu-id="38c4b-129">Embora essa estratégia possa gerar alguma economia de custos, esses aplicativos normalmente não eram arquitetados para desbloquear e aproveitar os benefícios da computação em nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="38c4b-130">Os aplicativos monolíticos que são essenciais para os negócios muitas vezes se beneficiam de uma migração avançada de comparação de precisão e deslocamento (*otimizada para nuvem*).</span><span class="sxs-lookup"><span data-stu-id="38c4b-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="38c4b-131">Essa abordagem inclui otimizações de implantação que habilitam os principais serviços de nuvem, sem alterar a arquitetura principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38c4b-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="38c4b-132">Por exemplo, você pode colocar o aplicativo em [contêiner](https://docs.microsoft.com/virtualization/windowscontainers/about/) e implantá-lo em um orquestrador de contêiner, como os [Serviços Kubernetess do Azure](https://azure.microsoft.com/services/kubernetes-service/), discutidos posteriormente neste livro.</span><span class="sxs-lookup"><span data-stu-id="38c4b-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="38c4b-133">Uma vez na nuvem, o aplicativo poderia consumir outros serviços de nuvem, como bancos de dados, filas de mensagens, monitoramento e Caching distribuído.</span><span class="sxs-lookup"><span data-stu-id="38c4b-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="38c4b-134">Por fim, os aplicativos monolíticos que executam funções empresariais estratégicas podem se beneficiar melhor de uma abordagem *nativa de nuvem* , o assunto deste livro.</span><span class="sxs-lookup"><span data-stu-id="38c4b-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="38c4b-135">Essa abordagem fornece agilidade e velocidade.</span><span class="sxs-lookup"><span data-stu-id="38c4b-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="38c4b-136">Mas, ele vem a um custo de replataforma, rearquitetura e reescrita de código.</span><span class="sxs-lookup"><span data-stu-id="38c4b-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="38c4b-137">Se você e sua equipe acreditarem que uma abordagem nativa de nuvem é apropriada, ela convém você a racionalizar a decisão com sua organização.</span><span class="sxs-lookup"><span data-stu-id="38c4b-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="38c4b-138">O que é exatamente o problema de negócios que uma abordagem nativa de nuvem resolverá?</span><span class="sxs-lookup"><span data-stu-id="38c4b-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="38c4b-139">Como ele se alinharia com as necessidades dos negócios?</span><span class="sxs-lookup"><span data-stu-id="38c4b-139">How would it align with business needs?</span></span>

- <span data-ttu-id="38c4b-140">Versões rápidas de recursos com maior confiança?</span><span class="sxs-lookup"><span data-stu-id="38c4b-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="38c4b-141">Escalabilidade refinada-uso mais eficiente de recursos?</span><span class="sxs-lookup"><span data-stu-id="38c4b-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="38c4b-142">Maior resiliência do sistema?</span><span class="sxs-lookup"><span data-stu-id="38c4b-142">Improved system resiliency?</span></span>

- <span data-ttu-id="38c4b-143">Melhor desempenho do sistema?</span><span class="sxs-lookup"><span data-stu-id="38c4b-143">Improved system performance?</span></span>

- <span data-ttu-id="38c4b-144">Mais visibilidade de operações?</span><span class="sxs-lookup"><span data-stu-id="38c4b-144">More visibility into operations?</span></span>

- <span data-ttu-id="38c4b-145">As plataformas de desenvolvimento de Blend e armazenamentos de dados chegam à melhor ferramenta para o trabalho?</span><span class="sxs-lookup"><span data-stu-id="38c4b-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="38c4b-146">Investimento de aplicativos à prova de futuro?</span><span class="sxs-lookup"><span data-stu-id="38c4b-146">Future-proof application investment?</span></span>

<span data-ttu-id="38c4b-147">A estratégia de migração certa depende das prioridades organizacionais e dos sistemas que você está direcionando.</span><span class="sxs-lookup"><span data-stu-id="38c4b-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="38c4b-148">Para muitos, pode ser mais econômico para otimizar a nuvem um aplicativo monolítico ou adicionar serviços de alta granularidade a um aplicativo de N camadas.</span><span class="sxs-lookup"><span data-stu-id="38c4b-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="38c4b-149">Nesses casos, você ainda pode fazer uso completo de recursos de PaaS de nuvem como os oferecidos pelo serviço Azure App.</span><span class="sxs-lookup"><span data-stu-id="38c4b-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="38c4b-150">Resumo</span><span class="sxs-lookup"><span data-stu-id="38c4b-150">Summary</span></span>

<span data-ttu-id="38c4b-151">Neste capítulo, introduzimos a computação nativa de nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="38c4b-152">Fornecemos uma definição junto com os principais recursos que orientam um aplicativo nativo de nuvem.</span><span class="sxs-lookup"><span data-stu-id="38c4b-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="38c4b-153">Examinamos os tipos de aplicativos que podem justificar esse investimento e esforço.</span><span class="sxs-lookup"><span data-stu-id="38c4b-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="38c4b-154">Com a introdução por trás, agora nos aprofundamos em uma visão muito mais detalhada na nuvem nativa.</span><span class="sxs-lookup"><span data-stu-id="38c4b-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="38c4b-155">Referências</span><span class="sxs-lookup"><span data-stu-id="38c4b-155">References</span></span>

- [<span data-ttu-id="38c4b-156">Computação nativa da nuvem Foundation</span><span class="sxs-lookup"><span data-stu-id="38c4b-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="38c4b-157">Microserviços .NET: arquitetura para aplicativos .NET em contêineres</span><span class="sxs-lookup"><span data-stu-id="38c4b-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="38c4b-158">Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure</span><span class="sxs-lookup"><span data-stu-id="38c4b-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="38c4b-159">Padrões de nuvem nativa por Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="38c4b-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="38c4b-160">Além do aplicativo de doze fatores</span><span class="sxs-lookup"><span data-stu-id="38c4b-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="38c4b-161">O que é infraestrutura como código</span><span class="sxs-lookup"><span data-stu-id="38c4b-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="38c4b-162">Micro Deploy de engenharia de Uber: implantação diária com confiança</span><span class="sxs-lookup"><span data-stu-id="38c4b-162">Uber Engineering’s Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="38c4b-163">Como o Netflix implanta o código</span><span class="sxs-lookup"><span data-stu-id="38c4b-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="38c4b-164">Controle de sobrecarga para dimensionar microserviços WeChat</span><span class="sxs-lookup"><span data-stu-id="38c4b-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

- [<span data-ttu-id="38c4b-165">O Raygun-estudo de caso</span><span class="sxs-lookup"><span data-stu-id="38c4b-165">RayGun - Case Study</span></span>](https://raygun.com/case-study/ovation)

>[!div class="step-by-step"]
><span data-ttu-id="38c4b-166">[Anterior](definition.md)
>[Próximo](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="38c4b-166">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
