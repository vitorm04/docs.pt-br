---
title: Aplicativos candidatos para nativos da nuvem
description: Saiba quais tipos de aplicativos se beneficiam de uma abordagem nativa da nuvem
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805619"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="37923-103">Aplicativos candidatos para nativos da nuvem</span><span class="sxs-lookup"><span data-stu-id="37923-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="37923-104">Olhe para os aplicativos em seu portfólio.</span><span class="sxs-lookup"><span data-stu-id="37923-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="37923-105">Quantos deles se qualificam para uma arquitetura nativa da nuvem?</span><span class="sxs-lookup"><span data-stu-id="37923-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="37923-106">Todos eles?</span><span class="sxs-lookup"><span data-stu-id="37923-106">All of them?</span></span> <span data-ttu-id="37923-107">Talvez alguns?</span><span class="sxs-lookup"><span data-stu-id="37923-107">Perhaps some?</span></span>

<span data-ttu-id="37923-108">Aplicando uma análise de custo/benefício, há uma boa chance de que a maioria não suportaria a etiqueta de preço pesada necessária para ser nativa da nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="37923-109">O custo de ser nativo da nuvem excederia em muito o valor de negócios da aplicação.</span><span class="sxs-lookup"><span data-stu-id="37923-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="37923-110">Que tipo de candidatura pode ser um candidato para nativo da nuvem?</span><span class="sxs-lookup"><span data-stu-id="37923-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="37923-111">Um sistema corporativo grande e estratégico que precisa evoluir constantemente os recursos/recursos dos negócios</span><span class="sxs-lookup"><span data-stu-id="37923-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="37923-112">Um aplicativo que requer uma alta velocidade de liberação - com alta confiança</span><span class="sxs-lookup"><span data-stu-id="37923-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="37923-113">Um sistema com onde os recursos individuais devem ser *liberados sem* uma reimplantação completa de todo o sistema</span><span class="sxs-lookup"><span data-stu-id="37923-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="37923-114">Um aplicativo desenvolvido por equipes com expertise em diferentes pilhas de tecnologia</span><span class="sxs-lookup"><span data-stu-id="37923-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="37923-115">Um aplicativo com componentes que devem ser dimensionados independentemente</span><span class="sxs-lookup"><span data-stu-id="37923-115">An application with components that must scale independently</span></span>

<span data-ttu-id="37923-116">Então há sistemas legados.</span><span class="sxs-lookup"><span data-stu-id="37923-116">Then there are legacy systems.</span></span> <span data-ttu-id="37923-117">Embora todos gostaríamos de construir novos aplicativos, muitas vezes somos responsáveis por modernizar cargas de trabalho legados que são fundamentais para os negócios.</span><span class="sxs-lookup"><span data-stu-id="37923-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="37923-118">Com o tempo, um aplicativo legado pode ser decomposto em microsserviços, contêiner e, finalmente, "replataformado" em uma arquitetura nativa da nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="37923-119">Modernização de aplicativos legados</span><span class="sxs-lookup"><span data-stu-id="37923-119">Modernizing legacy apps</span></span>

<span data-ttu-id="37923-120">O e-book gratuito da Microsoft [Modernize os aplicativos .NET existentes com nuvem Azure e Contêineres Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fornece orientação para migrar cargas de trabalho no local para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="37923-121">A Figura 1-10 mostra que não há uma única estratégia de tamanho único para modernizar aplicativos legados.</span><span class="sxs-lookup"><span data-stu-id="37923-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Estratégias para migrar cargas de trabalho legados](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="37923-123">**Figura 1-10**.</span><span class="sxs-lookup"><span data-stu-id="37923-123">**Figure 1-10**.</span></span> <span data-ttu-id="37923-124">Estratégias para migrar cargas de trabalho legados</span><span class="sxs-lookup"><span data-stu-id="37923-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="37923-125">Os aplicativos monolíticos que não são críticos beneficiam em grande parte de uma migração rápida de levantamento e mudança[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)</span><span class="sxs-lookup"><span data-stu-id="37923-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="37923-126">Aqui, a carga de trabalho no local é rehospedada em uma VM baseada em nuvem, sem alterações.</span><span class="sxs-lookup"><span data-stu-id="37923-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="37923-127">Esta abordagem utiliza o [modelo IaaS (Infrastructure as a Service).](https://azure.microsoft.com/overview/what-is-iaas/)</span><span class="sxs-lookup"><span data-stu-id="37923-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="37923-128">O Azure inclui várias ferramentas, como [o Azure Migrate,](https://azure.microsoft.com/services/azure-migrate/) [o Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)e [o Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) para facilitar esse movimento.</span><span class="sxs-lookup"><span data-stu-id="37923-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="37923-129">Embora essa estratégia possa gerar alguma redução de custos, tais aplicativos normalmente não foram arquitetados para desbloquear e aproveitar os benefícios da computação em nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="37923-130">Aplicativos monolíticos que são críticos para os negócios muitas vezes se beneficiam de uma migração aprimorada de elevação e mudança *(Otimização da Nuvem).*</span><span class="sxs-lookup"><span data-stu-id="37923-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="37923-131">Essa abordagem inclui otimizações de implantação que permitem os principais serviços de nuvem - sem alterar a arquitetura principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37923-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="37923-132">Por exemplo, você pode [contêiner](https://docs.microsoft.com/virtualization/windowscontainers/about/) o aplicativo e implantá-lo em um orquestrador de [contêineres, como o Azure Kubernetes Services,](https://azure.microsoft.com/services/kubernetes-service/)discutido mais tarde neste livro.</span><span class="sxs-lookup"><span data-stu-id="37923-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="37923-133">Uma vez na nuvem, o aplicativo poderia consumir outros serviços em nuvem, como bancos de dados, filas de mensagens, monitoramento e cache distribuído.</span><span class="sxs-lookup"><span data-stu-id="37923-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="37923-134">Finalmente, aplicativos monolíticos que executam funções corporativas estratégicas podem se beneficiar melhor de uma abordagem *Cloud-Native,* o tema deste livro.</span><span class="sxs-lookup"><span data-stu-id="37923-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="37923-135">Essa abordagem proporciona agilidade e velocidade.</span><span class="sxs-lookup"><span data-stu-id="37923-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="37923-136">Mas, ele vem a um custo de replataforma, rearquiteto e reescrever código.</span><span class="sxs-lookup"><span data-stu-id="37923-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="37923-137">Se você e sua equipe acreditam que uma abordagem nativa da nuvem é apropriada, cabe a você racionalizar a decisão com sua organização.</span><span class="sxs-lookup"><span data-stu-id="37923-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="37923-138">Qual é exatamente o problema de negócios que uma abordagem nativa da nuvem resolverá?</span><span class="sxs-lookup"><span data-stu-id="37923-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="37923-139">Como isso se alinharia às necessidades dos negócios?</span><span class="sxs-lookup"><span data-stu-id="37923-139">How would it align with business needs?</span></span>

- <span data-ttu-id="37923-140">Lançamentos rápidos de recursos com maior confiança?</span><span class="sxs-lookup"><span data-stu-id="37923-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="37923-141">Escalabilidade de grãos finos - uso mais eficiente de recursos?</span><span class="sxs-lookup"><span data-stu-id="37923-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="37923-142">Melhor resiliência do sistema?</span><span class="sxs-lookup"><span data-stu-id="37923-142">Improved system resiliency?</span></span>

- <span data-ttu-id="37923-143">Melhor desempenho do sistema?</span><span class="sxs-lookup"><span data-stu-id="37923-143">Improved system performance?</span></span>

- <span data-ttu-id="37923-144">Mais visibilidade nas operações?</span><span class="sxs-lookup"><span data-stu-id="37923-144">More visibility into operations?</span></span>

- <span data-ttu-id="37923-145">Misturar plataformas de desenvolvimento e data stores para chegar à melhor ferramenta para o trabalho?</span><span class="sxs-lookup"><span data-stu-id="37923-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="37923-146">Investimento em aplicações à prova de futuro?</span><span class="sxs-lookup"><span data-stu-id="37923-146">Future-proof application investment?</span></span>

<span data-ttu-id="37923-147">A estratégia de migração correta depende das prioridades organizacionais e dos sistemas que você está mirando.</span><span class="sxs-lookup"><span data-stu-id="37923-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="37923-148">Para muitos, pode ser mais econômico otimizar uma aplicação monolítica na nuvem ou adicionar serviços de grãos grossos a um aplicativo N-Tier.</span><span class="sxs-lookup"><span data-stu-id="37923-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="37923-149">Nesses casos, você ainda pode fazer uso total dos recursos do PaaS na nuvem, como os oferecidos pelo Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="37923-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="37923-150">Resumo</span><span class="sxs-lookup"><span data-stu-id="37923-150">Summary</span></span>

<span data-ttu-id="37923-151">Neste capítulo, introduzimos a computação nativa em nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="37923-152">Fornecemos uma definição juntamente com os principais recursos que impulsionam um aplicativo nativo da nuvem.</span><span class="sxs-lookup"><span data-stu-id="37923-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="37923-153">Analisamos os tipos de aplicações que podem justificar esse investimento e esforço.</span><span class="sxs-lookup"><span data-stu-id="37923-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="37923-154">Com a introdução por trás, agora mergulhamos em um olhar muito mais detalhado sobre os nativos das nuvens.</span><span class="sxs-lookup"><span data-stu-id="37923-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="37923-155">Referências</span><span class="sxs-lookup"><span data-stu-id="37923-155">References</span></span>

- [<span data-ttu-id="37923-156">Fundação de Computação Nativa da Nuvem</span><span class="sxs-lookup"><span data-stu-id="37923-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="37923-157">.NET Microservices: Arquitetura para aplicativos .NET contêiner</span><span class="sxs-lookup"><span data-stu-id="37923-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="37923-158">Modernize os aplicativos .NET existentes com a nuvem DoZure e os contêineres windows</span><span class="sxs-lookup"><span data-stu-id="37923-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="37923-159">Padrões nativos da nuvem por Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="37923-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="37923-160">Além da aplicação de doze fatores</span><span class="sxs-lookup"><span data-stu-id="37923-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="37923-161">O que é Infra-estrutura como Código</span><span class="sxs-lookup"><span data-stu-id="37923-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="37923-162">Micro Implantação da Uber Engineering: Implantação diária com confiança</span><span class="sxs-lookup"><span data-stu-id="37923-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="37923-163">Como a Netflix implanta código</span><span class="sxs-lookup"><span data-stu-id="37923-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="37923-164">Controle de sobrecarga para dimensionamento de microserviços wechat</span><span class="sxs-lookup"><span data-stu-id="37923-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="37923-165">[Próximo](definition.md)
>[anterior](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="37923-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
