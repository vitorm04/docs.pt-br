---
title: Escala de contêineres e aplicativos sem servidor
description: Dimensionamento de aplicativos nativos de nuvem com o serviço kubernetes do Azure para atender à demanda do usuário, aumentando os recursos individuais da máquina ou aumentando o número de computadores em um cluster de aplicativos.
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184795"
---
# <a name="scaling-containers-and-serverless-applications"></a>Escala de contêineres e aplicativos sem servidor

Há duas maneiras típicas de dimensionar um aplicativo: escalar verticalmente e escalar horizontalmente. O primeiro se refere à adição de recursos a um host, enquanto o último se refere à adição ao número total de hosts. Uma analogia comum a ser usada para pensar nisso é como se familiarizar com alguns amigos em toda a cidade. Se for apenas um amigo, você poderá entrar no carro de corrida de duas estações. Mas se for três ou quatro, talvez seja necessário pegar um de seus SUVs ou minivan, aumentando verticalmente para aumentar a capacidade. No entanto, quando o número total vai até uma dúzia ou mais, você provavelmente precisará realizar vários veículos (a menos que alguém retenha um barramento), que demonstra o conceito de expansão adicionando mais instâncias (neste caso, mais veículos). Vamos ver como isso se aplica aos nossos aplicativos.

## <a name="the-simple-solution-scaling-up"></a>A solução simples: escalar verticalmente

O processo de atualização de servidores existentes para fornecer a eles mais recursos (CPU, memória, velocidade de e/s de disco, velocidade de e/s de rede) é conhecido como *escalar verticalmente*. Em aplicativos nativos de nuvem, o dimensionamento normalmente não se refere à compra e à instalação de hardware real em máquinas físicas, tanto quanto a escolha de um plano mais compatível de uma lista de opções disponíveis. Os aplicativos nativos de nuvem normalmente aumentam modificando o tamanho da VM (máquina virtual) usado para hospedar os nós individuais em seu pool de nós kubernetes. Conceitos de kubernetes como nós, clusters e pods são descritos mais detalhadamente na [próxima seção](leverage-containers-orchestrators.md). O Azure dá suporte a uma ampla variedade de tamanhos de VM que executam o [Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) e o [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes). Para dimensionar verticalmente seu aplicativo, crie um novo pool de nós com um tamanho de VM de nó maior e, em seguida, migre as cargas de trabalho para o novo pool. Isso requer [vários pools de nó para o cluster AKs](https://docs.microsoft.com/azure/aks/use-multiple-node-pools), um recurso que está atualmente em visualização. Aplicativos sem servidor expandem verticalmente, escolhendo um [plano Premium](https://docs.microsoft.com/azure/azure-functions/functions-scale) e tamanhos de instância Premium ou escolhendo um plano de serviço de aplicativo dedicado diferente.

## <a name="scaling-out-cloud-native-apps"></a>Expandindo aplicativos nativos de nuvem

Os aplicativos nativos de nuvem dão suporte à expansão adicionando mais nós ou pods a solicitações de serviço. Isso pode ser feito manualmente ajustando as definições de configuração para o aplicativo (por exemplo, [dimensionando um pool de nós](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) ou por meio de *dimensionamento*automático. O dimensionamento automático ajusta os recursos usados por um aplicativo para responder à demanda, semelhante a como um termostato responde à temperatura chamando para aquecimento ou resfriamento adicional. Ao usar o dimensionamento automático, o dimensionamento manual é desabilitado.

Os clusters AKS podem ser dimensionados de uma das duas maneiras:

- O [autodimensionador do cluster](https://docs.microsoft.com/azure/aks/cluster-autoscaler) observa os pods que não podem ser agendados em nós devido a restrições de recursos. Ele adiciona nós adicionais conforme necessário.
- O **pod de dimensionamento horizontal** usa o servidor de métricas em um cluster kubernetes para monitorar as demandas de recursos de pods. Se um serviço precisar de mais recursos, o dimensionador automática aumentará o número de pods.

A Figura 3-13 mostra a relação entre esses dois serviços de dimensionamento.

![Dimensionando um plano do serviço de aplicativo.](./media/aks-cluster-autoscaler.png)

**Figura 3-13**. Dimensionando um plano do serviço de aplicativo.

Esses serviços também podem reduzir o número de pods ou nós conforme necessário. Esses dois serviços podem trabalhar juntos e geralmente são implantados juntos em um cluster. Quando combinado, a escala automática de Pod horizontal concentra-se na execução do número de pods necessário para atender à demanda do aplicativo. O dimensionador automática do cluster concentra-se na execução do número de nós necessários para dar suporte ao pods agendado.

### <a name="scaling-azure-functions"></a>Dimensionamento Azure Functions

O Azure Functions dá suporte automaticamente ao dimensionamento. O plano de consumo padrão adiciona (e remove) recursos dinamicamente com base no número de eventos de disparo de entrada. Você é cobrado apenas pelos recursos de computação que estão sendo usados quando suas funções estão sendo executadas com base no número de execuções, no tempo de execução e na memória usada. Usando o plano Premium, você obtém esses mesmos recursos, mas também pode controlar os tamanhos de instância que são usados, ter instâncias já ativadas (para evitar atrasos de inicialização a frio) e configurar VMs dedicadas nas quais executar suas funções. Embora a configuração padrão deva fornecer uma solução econômica e escalonável para a maioria dos aplicativos, a opção Premium permite aos desenvolvedores flexibilidade para requisitos de Azure Functions personalizados.

## <a name="references"></a>Referências

- [AKS vários pools de nós](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Autoescalar do cluster AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Tutorial: dimensionar aplicativos em AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Escala e Hospedagem de Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[Anterior](deploy-containers-azure.md)
>[Próximo](other-deployment-options.md)
