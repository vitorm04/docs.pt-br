---
title: Monitorar serviços de aplicativos em contêineres
description: Saiba mais alguns aspectos fundamentais do monitoramento de arquiteturas de contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922740"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="97a2b-103">Monitorar serviços de aplicativos em contêineres</span><span class="sxs-lookup"><span data-stu-id="97a2b-103">Monitor containerized application services</span></span>

<span data-ttu-id="97a2b-104">É essencial para aplicativos dividida em vários contêineres e microsserviços ter uma maneira de monitorar e analisar o comportamento de todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97a2b-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="97a2b-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="97a2b-105">Azure Monitor</span></span>

<span data-ttu-id="97a2b-106">[O Azure Monitor](https://azure.microsoft.com/services/monitor/) é um serviço de análise extensível que monitora seu aplicativo ativo.</span><span class="sxs-lookup"><span data-stu-id="97a2b-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="97a2b-107">Ele ajuda a detectar e diagnosticar problemas de desempenho e entender o que os usuários realmente fazem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97a2b-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="97a2b-108">Ele é projetado para desenvolvedores, com a intenção de ajudá-lo a melhorar continuamente o desempenho e a usabilidade de seus aplicativos ou serviços.</span><span class="sxs-lookup"><span data-stu-id="97a2b-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="97a2b-109">O Azure Monitor funciona com autônomo e de web/serviços aplicativos em uma ampla variedade de plataformas, como .NET, Java, Node. js e muitas outras plataformas, hospedados localmente ou na nuvem.</span><span class="sxs-lookup"><span data-stu-id="97a2b-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="97a2b-110">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="97a2b-110">Additional resources</span></span>

- <span data-ttu-id="97a2b-111">**Visão geral do Monitor do Azure** \\</span><span class="sxs-lookup"><span data-stu-id="97a2b-111">**Overview of Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="97a2b-112">**O que é o Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="97a2b-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="97a2b-113">**O que é monitorar métricas do Azure?**</span><span class="sxs-lookup"><span data-stu-id="97a2b-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="97a2b-114">**Solução de monitoramento de contêiner no Azure Monitor** \\</span><span class="sxs-lookup"><span data-stu-id="97a2b-114">**Container Monitoring solution in Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="97a2b-115">Serviços de backup e de segurança</span><span class="sxs-lookup"><span data-stu-id="97a2b-115">Security and backup services</span></span>

<span data-ttu-id="97a2b-116">Há muitas tarefas de suporte com muitos detalhes que você precisa lidar com para garantir que seus aplicativos e infraestrutura estão em condições de entalhe superior para dar suporte às necessidades de negócios e a situação fica mais complicada no realm de microsserviços, portanto, você precisa de uma maneira de tem exibições detalhadas e de alto nível quando você precisa realizar ação.</span><span class="sxs-lookup"><span data-stu-id="97a2b-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="97a2b-117">O Azure tem as ferramentas para gerenciar e fornecer uma exibição unificada de quatro aspectos críticos dos recursos de sua nuvem e locais:</span><span class="sxs-lookup"><span data-stu-id="97a2b-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="97a2b-118">**Segurança**.</span><span class="sxs-lookup"><span data-stu-id="97a2b-118">**Security**.</span></span> <span data-ttu-id="97a2b-119">Com o [Central de segurança do Azure](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="97a2b-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="97a2b-120">Obtenha visibilidade e controle sobre a segurança de suas máquinas virtuais, aplicativos e cargas de trabalho completos.</span><span class="sxs-lookup"><span data-stu-id="97a2b-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="97a2b-121">Centralizar o gerenciamento de suas políticas de segurança e integre ferramentas e processos existentes.</span><span class="sxs-lookup"><span data-stu-id="97a2b-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="97a2b-122">Detecte ameaças reais usando análise avançada.</span><span class="sxs-lookup"><span data-stu-id="97a2b-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="97a2b-123">**Backup**.</span><span class="sxs-lookup"><span data-stu-id="97a2b-123">**Backup**.</span></span> <span data-ttu-id="97a2b-124">Com o [o Backup do Azure](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="97a2b-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="97a2b-125">Evite interrupções dos negócios onerosas, cumpra metas de conformidade e proteger seus dados contra ransomware e erros humanos.</span><span class="sxs-lookup"><span data-stu-id="97a2b-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="97a2b-126">Mantenha seus dados de backup criptografados em trânsito e em repouso.</span><span class="sxs-lookup"><span data-stu-id="97a2b-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="97a2b-127">Verifique se o acesso com base na autenticação multifator para evitar uso não autorizado.</span><span class="sxs-lookup"><span data-stu-id="97a2b-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="97a2b-128">**Recursos locais**.</span><span class="sxs-lookup"><span data-stu-id="97a2b-128">**On-premises resources**.</span></span> <span data-ttu-id="97a2b-129">Com o [uma nuvem híbrida realmente consistente](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="97a2b-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="97a2b-130">[Anterior](manage-production-docker-environments.md)
>[Próximo](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="97a2b-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
