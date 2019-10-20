---
title: Comunicação resiliente
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Comunicação resiliente
ms.date: 06/30/2019
ms.openlocfilehash: 324f5426af1c892db73aa6fc2336a19b7a8e499e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315804"
---
# <a name="resilient-communications"></a>Comunicações resilientes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Em todo este livro, nós evangelizedmos os méritos de se moverem além do design de aplicativo monolítico tradicional e adotando uma arquitetura baseada em microserviço em que um conjunto de serviços distribuídos e independentes é executado de forma independente e se comunica com cada um outros usando protocolos de comunicação padrão, como HTTP e HTTPS. Embora essa arquitetura seja comprada por muitos benefícios importantes, ela também apresenta muitos desafios. Considere, por exemplo, as seguintes preocupações:

- *Comunicação de rede fora do processo.* Cada serviço se comunica em um protocolo de rede que apresenta congestionamento de rede, latência e falhas transitórias.
- *Descoberta de serviço.* Com cada serviço em execução em um cluster de computadores com seu próprio endereço IP e porta, como os serviços são descobertos e se comunicam entre si?
- *Resiliência.* Como gerenciar falhas de curta duração e manter o sistema estável?
- *Balanceamento de carga.* Como o tráfego de entrada é distribuído entre várias instâncias de um serviço?
- *Segurança.* Como as questões de segurança, como criptografia de nível de transporte e gerenciamento de certificados, são impostas?
- *Monitoramento distribuído.* -Como correlacionar e capturar a rastreabilidade e o monitoramento de uma única solicitação entre vários serviços de consumo?

Embora essas preocupações possam ser tratadas com várias bibliotecas e estruturas, implementá-las dentro de sua base de código pode ser cara, complexa e demorada. Além disso, você acaba com uma solução em que as preocupações com a infraestrutura são ligadas à lógica de negócios.

## <a name="service-mesh"></a>Malha de serviço

Uma abordagem melhor é considerar uma nova e rápida evolução da malha de *serviço*qualificada. Uma [malha de serviço](https://www.nginx.com/blog/what-is-a-service-mesh/) é uma camada de infraestrutura configurável com recursos internos para lidar com a comunicação do serviço e com muitos dos desafios mencionados acima. Ele separa essas preocupações de seu código comercial e as move para um proxy de serviço, uma instância do que acompanha cada um de seus serviços. Geralmente conhecido como o [padrão sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar), o proxy de malha de serviço é implantado em um processo separado para fornecer isolamento e encapsulamento do seu código comercial. No entanto, o proxy está fortemente vinculado ao serviço que está sendo criado junto com ele e compartilhando seu ciclo de vida. A Figura 6-9 mostra esse cenário.

![Malha de serviço com um carro lateral](./media/service-mesh-with-side-car.png)

**Figura 6-9**. Malha de serviço com um carro lateral

Na figura anterior, observe como o proxy intercepta e gerencia a comunicação entre os microserviços e o cluster.

Uma malha de serviço é dividida logicamente em dois componentes diferentes: um [plano de dados](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) e um [plano de controle](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). A Figura 6-10 mostra esses componentes e suas responsabilidades.

![Controle de malha de serviço e plano de dados](./media/istio-control-and-data-plane.png)

**Figura 6-10.** Controle de malha de serviço e plano de dados

Uma vez configurado, uma malha de serviço é altamente funcional. Ele pode recuperar um pool correspondente de instâncias de um ponto de extremidade de descoberta de serviço. Em seguida, ele pode enviar uma solicitação para uma instância específica, registrando a latência e o tipo de resposta do resultado. Uma malha pode escolher a instância mais provável de retornar uma resposta rápida com base em vários fatores, incluindo sua latência observada para solicitações recentes.

Se uma instância não estiver respondendo ou falhar, a malha poderá repetir a solicitação em outra instância. Se um pool retornar erros de forma consistente, uma malha poderá removê-lo do pool de balanceamento de carga para ser repetido periodicamente mais tarde depois de ser reparado. Se uma solicitação atingir o tempo limite, uma malha poderá falhar e, em seguida, repetir a solicitação. Uma malha captura o comportamento na forma de métricas e no rastreamento distribuído, que pode ser emitido para um sistema de métricas centralizado.

## <a name="istio-and-envoy"></a>İSTİO e Envoy

Embora algumas opções de malha de serviço existam atualmente, a [İSTİO](https://istio.io/docs/concepts/what-is-istio/) é a mais popular no momento da elaboração deste artigo. Uma joint venture da IBM, do Google e do lyft, é uma oferta de software livre que pode ser integrada a um aplicativo distribuído novo ou existente. Ele fornece uma solução consistente e completa para proteger, conectar e monitorar os microserviços. Seus recursos incluem:

- Proteja a comunicação entre serviços em um cluster com autenticação e autorização baseadas em identidade forte.
- Balanceamento de carga automático para tráfego HTTP, [gRPC](https://grpc.io/), WebSocket e TCP.
- Controle refinado do comportamento de tráfego com regras de roteamento avançadas, repetições, failovers e injeção de falha.
- Uma camada de política conectável e uma API de configuração que dão suporte a controles de acesso, limites de taxa e cotas.
- Métricas, logs e rastreamentos automáticos para todo o tráfego em um cluster, incluindo a entrada e saída do cluster.

Um componente fundamental para uma implementação de İSTİO é um serviço de proxy intitulado The [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy). Provenientes de lyft e subsequentemente contribuíram para a [base de computação nativa de nuvem](https://www.cncf.io/) (discutida no capítulo 1), o proxy Envoy é executado junto com cada serviço e fornece uma base independente de plataforma para os seguintes recursos:

- Descoberta dinâmica de serviço.
- Balanceamento de carga.
- Término do TLS.
- Proxies HTTP e gRPC.
- Resiliência do disjuntor.
- Verificações de integridade.
- Atualizações sem interrupção com implantações do [canário](https://martinfowler.com/bliki/CanaryRelease.html) .

Conforme discutido anteriormente, o Envoy é implantado como um sidecar para cada microserviço no cluster.

## <a name="integration-with-azure-kubernetes-services"></a>Integração com os serviços Kubernetess do Azure

A nuvem do Azure adota o İSTİO e fornece suporte direto para ele nos serviços Kubernetess do Azure. Os links a seguir podem ajudá-lo a começar:

- [Instalando o İSTİO no AKS](https://docs.microsoft.com/azure/aks/istio-install)
- [Usando AKS e İSTİO](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

>[!div class="step-by-step"]
>[Anterior](infrastructure-resiliency-azure.md)
>[Próximo](monitoring-health.md)
