---
title: Monitorar serviços de aplicativos em contêineres
description: Saiba alguns aspectos fundamentais do monitoramento de arquiteturas de contêiner
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673453"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="c587d-103">Monitorar serviços de aplicativos em contêineres</span><span class="sxs-lookup"><span data-stu-id="c587d-103">Monitor containerized application services</span></span>

<span data-ttu-id="c587d-104">É essencial para aplicativos divididos em vários contêineres e microsserviços ter uma maneira de monitorar e analisar o comportamento do aplicativo como um todo.</span><span class="sxs-lookup"><span data-stu-id="c587d-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="c587d-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="c587d-105">Azure Monitor</span></span>

<span data-ttu-id="c587d-106">O [Azure Monitor](https://azure.microsoft.com/services/monitor/) é um serviço de análise extensível que monitora seu aplicativo online.</span><span class="sxs-lookup"><span data-stu-id="c587d-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="c587d-107">Com ele, você pode detectar e diagnosticar problemas de desempenho e entender o que os usuários realmente fazem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c587d-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="c587d-108">É projetado para desenvolvedores com a intenção de ajudar você a melhorar continuamente o desempenho e a usabilidade de seus aplicativos ou serviços.</span><span class="sxs-lookup"><span data-stu-id="c587d-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="c587d-109">O Azure Monitor funciona com serviços e aplicativos Web autônomos em uma ampla variedade de plataforma, como .NET, Java, Node.js e diversas outras hospedadas localmente ou na nuvem.</span><span class="sxs-lookup"><span data-stu-id="c587d-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c587d-110">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c587d-110">Additional resources</span></span>

- <span data-ttu-id="c587d-111">**Visão geral do Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="c587d-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="c587d-112">**O que é o Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="c587d-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="c587d-113">**O que são as Métricas do Azure Monitor?**</span><span class="sxs-lookup"><span data-stu-id="c587d-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="c587d-114">**Solução de monitoramento de contêiner no Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="c587d-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="c587d-115">Serviços de backup e segurança</span><span class="sxs-lookup"><span data-stu-id="c587d-115">Security and backup services</span></span>

<span data-ttu-id="c587d-116">Há muitas tarefas de suporte com vários detalhes que você precisa abordar para garantir que os aplicativos e a infraestrutura estejam nas melhores condições para apoiar as necessidades de negócios. A situação fica mais complicada no caso dos microsserviços, portanto, você precisa de uma forma de obter exibições detalhadas e de alto nível quando precisar tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="c587d-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="c587d-117">O Azure tem as ferramentas para gerenciar e oferecer uma exibição unificada de quatro aspectos fundamentais dos recursos locais e em nuvem:</span><span class="sxs-lookup"><span data-stu-id="c587d-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="c587d-118">**Segurança**.</span><span class="sxs-lookup"><span data-stu-id="c587d-118">**Security**.</span></span> <span data-ttu-id="c587d-119">Com a [Central de Segurança do Azure](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="c587d-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="c587d-120">Tenha visibilidade e controle da segurança das suas máquinas virtuais, seus aplicativos e suas cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c587d-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="c587d-121">Centralize o gerenciamento das suas políticas de segurança e integre os processos e as ferramentas existentes.</span><span class="sxs-lookup"><span data-stu-id="c587d-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="c587d-122">Detecte ameaças reais com análise avançada.</span><span class="sxs-lookup"><span data-stu-id="c587d-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="c587d-123">**Backup**.</span><span class="sxs-lookup"><span data-stu-id="c587d-123">**Backup**.</span></span> <span data-ttu-id="c587d-124">Com o [Backup do Azure](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="c587d-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="c587d-125">Evite interrupções onerosas nos negócios, cumpra as metas de conformidade e proteja seus dados contra ransomware e erros humanos.</span><span class="sxs-lookup"><span data-stu-id="c587d-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="c587d-126">Mantenha seus dados de backup criptografados em trânsito e em repouso.</span><span class="sxs-lookup"><span data-stu-id="c587d-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="c587d-127">Garanta acesso com base na autenticação multifator para evitar o uso não autorizado.</span><span class="sxs-lookup"><span data-stu-id="c587d-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="c587d-128">**Recursos locais**.</span><span class="sxs-lookup"><span data-stu-id="c587d-128">**On-premises resources**.</span></span> <span data-ttu-id="c587d-129">Com [uma nuvem híbrida realmente consistente](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="c587d-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c587d-130">[Anterior](manage-production-docker-environments.md)
>[Próximo](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="c587d-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
