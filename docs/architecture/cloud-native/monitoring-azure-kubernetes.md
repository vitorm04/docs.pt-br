---
title: Monitoramento nos serviços Kubernetess do Azure
description: Monitoramento nos serviços Kubernetess do Azure
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184984"
---
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="1421a-103">Monitoramento nos serviços Kubernetess do Azure</span><span class="sxs-lookup"><span data-stu-id="1421a-103">Monitoring in Azure Kubernetes Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1421a-104">O log interno em kubernetes é primitivo.</span><span class="sxs-lookup"><span data-stu-id="1421a-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="1421a-105">No entanto, há algumas ótimas opções para fazer os logs de kubernetes e em um local onde eles podem ser analisados corretamente.</span><span class="sxs-lookup"><span data-stu-id="1421a-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="1421a-106">Se você precisar monitorar os clusters do AKS, configurar a pilha elástica para kubernetes é uma ótima solução.</span><span class="sxs-lookup"><span data-stu-id="1421a-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="1421a-107">Pilha elástica</span><span class="sxs-lookup"><span data-stu-id="1421a-107">Elastic Stack</span></span>

<span data-ttu-id="1421a-108">A pilha elástica é uma opção avançada para coletar informações de um cluster kubernetes.</span><span class="sxs-lookup"><span data-stu-id="1421a-108">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="1421a-109">O kubernetes dá suporte ao envio de logs para um ponto de extremidade Elasticsearch e, na [maioria das vezes](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), tudo o que você precisa para começar é definir as variáveis de ambiente, conforme mostrado na Figura 7-5:</span><span class="sxs-lookup"><span data-stu-id="1421a-109">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="1421a-110">**Figura 7-5** -variáveis de configuração para kubernetes</span><span class="sxs-lookup"><span data-stu-id="1421a-110">**Figure 7-5** - Configuration variables for Kubernetes</span></span>

<span data-ttu-id="1421a-111">Isso instalará o Elasticsearch no cluster e o destino enviando todos os logs de cluster para ele.</span><span class="sxs-lookup"><span data-stu-id="1421a-111">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="1421a-112">![Um exemplo de um painel de Kibana mostrando os resultados de uma consulta em relação a logs ingeridos da](./media/kibana-dashboard.png)
**Figura kubernetes 7-6**.</span><span class="sxs-lookup"><span data-stu-id="1421a-112">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="1421a-113">Um exemplo de um painel de Kibana que mostra os resultados de uma consulta em relação aos logs que são ingeridos do kubernetes</span><span class="sxs-lookup"><span data-stu-id="1421a-113">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="azure-container-monitoring"></a><span data-ttu-id="1421a-114">Monitoramento de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="1421a-114">Azure Container Monitoring</span></span>

<span data-ttu-id="1421a-115">O monitoramento de contêiner do Azure dá suporte a logs de consumo de não apenas kubernetes, mas também de outros mecanismos de orquestração, como DC/OS, Docker Swarm e Red Hat OpenShift.</span><span class="sxs-lookup"><span data-stu-id="1421a-115">Azure Container Monitoring supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="1421a-116">![Consumindo logs de](./media/containers-diagram.png)
vários contêineres,**Figura 7-7**.</span><span class="sxs-lookup"><span data-stu-id="1421a-116">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-7**.</span></span>  <span data-ttu-id="1421a-117">Consumindo logs de vários contêineres</span><span class="sxs-lookup"><span data-stu-id="1421a-117">Consuming logs from various containers</span></span>

<span data-ttu-id="1421a-118">As informações de log e métricas são coletadas não apenas dos contêineres em execução no cluster, mas também dos hosts de cluster.</span><span class="sxs-lookup"><span data-stu-id="1421a-118">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="1421a-119">Ele permite correlacionar as informações de log das duas tornando muito mais fácil rastrear um erro.</span><span class="sxs-lookup"><span data-stu-id="1421a-119">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="1421a-120">A instalação dos coletores de logs difere nos clusters do [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) e do [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) .</span><span class="sxs-lookup"><span data-stu-id="1421a-120">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="1421a-121">Mas, em ambos os casos, a coleção de log é implementada como um [daemonset](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)kubernetes, o que significa que o coletor de logs é executado como um contêiner em cada um dos nós.</span><span class="sxs-lookup"><span data-stu-id="1421a-121">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="1421a-122">Não importa qual orquestrador ou sistema operacional está executando o daemon de Azure Monitor, as informações de log são encaminhadas para as mesmas ferramentas de Azure Monitor com as quais os usuários estão familiarizados.</span><span class="sxs-lookup"><span data-stu-id="1421a-122">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="1421a-123">Isso garante uma experiência paralela em ambientes que misturam diferentes fontes de log, como um ambiente híbrido de kubernetes/Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="1421a-123">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="1421a-124">![Um painel de exemplo mostrando informações de log e métrica de vários contêineres em execução. **Figura 7-8**. ](./media/containers-dashboard.png)
</span><span class="sxs-lookup"><span data-stu-id="1421a-124">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-8**.</span></span> <span data-ttu-id="1421a-125">Um painel de exemplo mostrando informações de log e métrica de vários contêineres em execução.</span><span class="sxs-lookup"><span data-stu-id="1421a-125">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="1421a-126">Log. Finalize ()</span><span class="sxs-lookup"><span data-stu-id="1421a-126">Log.Finalize()</span></span>

<span data-ttu-id="1421a-127">O registro em log é uma das partes mais desprocuradas e, ainda mais importantes, da implantação de qualquer aplicativo em escala.</span><span class="sxs-lookup"><span data-stu-id="1421a-127">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="1421a-128">À medida que o tamanho e a complexidade dos aplicativos aumentam, então a dificuldade de depurá-los.</span><span class="sxs-lookup"><span data-stu-id="1421a-128">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="1421a-129">Ter os principais logs de qualidade disponíveis torna a depuração muito mais fácil e a move do território de "quase impossível" para "uma experiência agradável".</span><span class="sxs-lookup"><span data-stu-id="1421a-129">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1421a-130">[Anterior](logging-with-elastic-stack.md)
>[Próximo](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="1421a-130">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
