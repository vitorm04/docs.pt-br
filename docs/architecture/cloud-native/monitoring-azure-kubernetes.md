---
title: Como monitorar nos Serviços de Kubernetes do Azure
description: Como monitorar nos Serviços de Kubernetes do Azure
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184984"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Como monitorar nos Serviços de Kubernetes do Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

O log interno em kubernetes é primitivo. No entanto, há algumas ótimas opções para fazer os logs de kubernetes e em um local onde eles podem ser analisados corretamente. Se você precisar monitorar os clusters do AKS, configurar a pilha elástica para kubernetes é uma ótima solução.

## <a name="elastic-stack"></a>Pilha elástica

A pilha elástica é uma opção avançada para coletar informações de um cluster kubernetes. O kubernetes dá suporte ao envio de logs para um ponto de extremidade Elasticsearch e, na [maioria das vezes](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), tudo o que você precisa para começar é definir as variáveis de ambiente, conforme mostrado na Figura 7-5:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Figura 7-5** -variáveis de configuração para kubernetes

Isso instalará o Elasticsearch no cluster e o destino enviando todos os logs de cluster para ele.

![um exemplo de um painel Kibana que mostra os resultados de uma consulta em relação a logs ingeridos de kubernetes](./media/kibana-dashboard.png)
**figura 7-6**. Um exemplo de um painel de Kibana que mostra os resultados de uma consulta em relação aos logs que são ingeridos do kubernetes

## <a name="azure-container-monitoring"></a>Monitoramento de contêiner do Azure

O monitoramento de contêiner do Azure dá suporte a logs de consumo de não apenas kubernetes, mas também de outros mecanismos de orquestração, como DC/OS, Docker Swarm e Red Hat OpenShift.

![consumir logs de vários contêineres](./media/containers-diagram.png)
**figura 7-7**.  Consumindo logs de vários contêineres

As informações de log e métricas são coletadas não apenas dos contêineres em execução no cluster, mas também dos hosts de cluster. Ele permite correlacionar as informações de log das duas tornando muito mais fácil rastrear um erro.

A instalação dos coletores de logs difere nos clusters do [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) e do [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . Mas, em ambos os casos, a coleção de log é implementada como um [daemonset](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)kubernetes, o que significa que o coletor de logs é executado como um contêiner em cada um dos nós.

Não importa qual orquestrador ou sistema operacional está executando o daemon de Azure Monitor, as informações de log são encaminhadas para as mesmas ferramentas de Azure Monitor com as quais os usuários estão familiarizados. Isso garante uma experiência paralela em ambientes que misturam diferentes fontes de log, como um ambiente híbrido de kubernetes/Azure Functions.

![um painel de exemplo mostrando informações de log e métrica de vários contêineres em execução.](./media/containers-dashboard.png)
**figura 7-8**. Um painel de exemplo mostrando informações de log e métrica de vários contêineres em execução.

## <a name="logfinalize"></a>Log. Finalize ()

O registro em log é uma das partes mais desprocuradas e, ainda mais importantes, da implantação de qualquer aplicativo em escala. À medida que o tamanho e a complexidade dos aplicativos aumentam, então a dificuldade de depurá-los. Ter os principais logs de qualidade disponíveis torna a depuração muito mais fácil e a move do território de "quase impossível" para "uma experiência agradável".

>[!div class="step-by-step"]
>[Anterior](logging-with-elastic-stack.md)
>[Próximo](azure-monitor.md)
