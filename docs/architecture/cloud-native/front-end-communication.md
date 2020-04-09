---
title: Comunicação front-end de cliente
description: Saiba como os clientes front-end se comunicam com sistemas nativos da nuvem
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989071"
---
# <a name="front-end-client-communication"></a>Comunicação front-end de cliente

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Em um sistema nativo da nuvem, os clientes front-end (aplicativos móveis, web e desktop) exigem um canal de comunicação para interagir com microserviços independentes de back-end.  

Quais são as opções?

Para manter as coisas simples, um cliente front-end poderia *se comunicar diretamente* com os microsserviços back-end, mostrados na Figura 4-2.

![Cliente direto para comunicação de serviço](./media/direct-client-to-service-communication.png)

**Figura 4-2.** Cliente direto para comunicação de serviço

Com essa abordagem, cada microserviço tem um ponto final público que é acessível por clientes front-end. Em um ambiente de produção, você colocaria um balanceador de carga na frente dos microsserviços, direcionando o tráfego proporcionalmente.

Embora simples de implementar, a comunicação direta com o cliente seria aceitável apenas para aplicações simples de microsserviços. Esse padrão acopla clientes front-end para serviços back-end principais, abrindo a porta para uma série de problemas, incluindo:

- Suscetibilidade do cliente à refatoração de serviço back-end.
- Uma superfície de ataque mais ampla à medida que os serviços de back-end principais são diretamente expostos.
- Duplicação de preocupações transversais em cada microserviço.
- Código de cliente excessivamente complexo - os clientes devem acompanhar vários pontos finais e lidar com falhas de forma resiliente.

Em vez disso, um padrão de design de nuvem amplamente aceito é implementar um [API Gateway Service](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) entre os aplicativos front-end e os serviços back-end. O padrão é mostrado na Figura 4-3.

![Padrão de gateway api](./media/api-gateway-pattern.png)

**Figura 4-3.** Padrão de gateway aPI

Na figura anterior, observe como o serviço API Gateway abstrai os microsserviços de núcleo back-end. Implementado como uma API web, atua como um *proxy reverso,* roteando o tráfego de entrada para os microsserviços internos.

O gateway isola o cliente do particionamento e refatoração do serviço interno. Se você alterar um serviço back-end, você acomoda-o no gateway sem quebrar o cliente. É também sua primeira linha de defesa para preocupações transversais, como identidade, cache, resiliência, medição e estrangulamento. Muitas dessas preocupações transversais podem ser descarregadas dos serviços de núcleo back-end para o gateway, simplificando os serviços back-end.

Deve-se tomar cuidado para manter o Gateway API simples e rápido. Normalmente, a lógica empresarial é mantida fora do portal. Um portal complexo corre o risco de se tornar um gargalo e, eventualmente, um monólito em si. Sistemas maiores geralmente expõem vários Gateways de API segmentados por tipo de cliente (mobile, web, desktop) ou funcionalidade back-end. O [padrão Backend for Frontends](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) fornece direção para a implementação de vários gateways. O padrão é mostrado na Figura 4-4.

![Padrão de gateway api](./media/backend-for-frontend-pattern.png)

**Figura 4-4.** Backend para o padrão frontend

Observe no número anterior como o tráfego de entrada é enviado para um gateway de API específico - com base no tipo de cliente: web, mobile ou desktop app. Essa abordagem faz sentido, pois as capacidades de cada dispositivo diferem significativamente entre fator de forma, desempenho e limitações de exibição. Normalmente, aplicativos móveis expõem menos funcionalidade do que um navegador ou aplicativos de desktop. Cada gateway pode ser otimizado para corresponder aos recursos e funcionalidades do dispositivo correspondente.

Para começar, você pode construir seu próprio serviço API Gateway. Uma pesquisa rápida do GitHub fornecerá muitos exemplos. No entanto, existem várias estruturas e produtos de gateway comercial disponíveis.

## <a name="ocelot-gateway"></a>Gateway de Jaguation

Para aplicações nativas em nuvem .NET simples, você pode considerar o [Gateway de ocelot](https://github.com/ThreeMammals/Ocelot). O Ocelot é um Gateway de API de código aberto criado para microsserviços .NET que requerem um ponto de entrada unificado em seu sistema. É leve, rápido, escalável.

Como qualquer Gateway de API, sua principal funcionalidade é encaminhar solicitações HTTP recebidas para serviços a jusante. Além disso, ele suporta uma grande variedade de recursos que são configuráveis em um pipeline de middleware .NET Core. Seu conjunto de recursos é apresentado na tabela a seguir.

|Características da jaguation  | |
| :-------- | :-------- |
| Roteamento | Autenticação |
| Agregação de pedidos | Autorização |
| Descoberta de Serviços (com Cônsul e Eureka) | Limitação |
| Balanceamento de Carga | Registro, Rastreamento |
| Cache | Headers/Transformação de string sustais de consulta |
| Passagem de Correlação | Middleware personalizado |
| Qualidade de Serviço | Políticas de reteste |

Cada gateway Ocelot especifica os endereços upstream e downstream e recursos configuráveis em um arquivo de configuração JSON. O cliente envia uma solicitação HTTP para o gateway Da Jaguaticia. Uma vez recebida, a Ocelot passa o objeto HttpRequest através de seu pipeline manipulando-o para o estado especificado por sua configuração. No final do pipeline, a Ocelot cria um novo HTTPResponseObject e o passa para o serviço downstream. Para a resposta, a Ocelot inverte o pipeline, enviando a resposta de volta ao cliente.

O celot está disponível como um pacote NuGet. Ele tem como alvo o NET Standard 2.0, tornando-o compatível com os tempos de execução .NET Core 2.0+ e .NET Framework 4.6.1+. O Ocelot se integra com qualquer coisa que fale HTTP e seja executado nas plataformas que o .NET Core suporta: Linux, macOS e Windows. A Ocelot é extensível e suporta muitas plataformas modernas, incluindo contêineres Docker, Azure Kubernetes Services ou outras nuvens públicas.  A Jaguaticia integra-se com pacotes de código aberto como [Cônsul,](https://www.consul.io) [GraphQL](https://graphql.org)e [Eureka](https://github.com/Netflix/eureka)da Netflix.

Considere o Ocelot para aplicativos simples nativos da nuvem que não requerem o rico conjunto de recursos de um gateway de API comercial.

## <a name="azure-application-gateway"></a>Gateway de Aplicativo do Azure

Para requisitos simples de gateway, você pode considerar [o Gateway de aplicativos do Azure](https://docs.microsoft.com/azure/application-gateway/overview). Disponível como um serviço Azure [PaaS,](https://azure.microsoft.com/overview/what-is-paas/)ele inclui recursos básicos de gateway, como roteamento de URL, terminação SSL e um Firewall de Aplicativo web. O serviço suporta recursos [de balanceamento de carga camada 7.](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) Com a Camada 7, você pode encaminhar solicitações com base no conteúdo real de uma mensagem HTTP, não apenas pacotes de rede TCP de baixo nível.

Ao longo deste livro, evangelizamos a hospedagem de sistemas nativos em nuvem em [Kubernetes.](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html) Um orquestrador de contêineres, o Kubernetes automatiza a implantação, o dimensionamento e as preocupações operacionais das cargas de trabalho em contêineres. O Azure Application Gateway pode ser configurado como um gateway de API para o cluster [Azure Kubernetes Service.](https://azure.microsoft.com/services/kubernetes-service/)

O [Controlador de Entrada de Gateway](https://azure.github.io/application-gateway-kubernetes-ingress/) de Aplicativo permite que o Gateway de aplicativos do Azure funcione diretamente com o [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). A Figura 4.5 mostra a arquitetura.

![Controlador de Entrada do Gateway de Aplicativo](./media/application-gateway-ingress-controller.png)

**Figura 4-5.** Controlador de Entrada do Gateway de Aplicativo

Kubernetes inclui um recurso incorporado que suporta balanceamento de carga HTTP (Nível 7), chamado [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/). Ingress define um conjunto de regras para como as instâncias de microserviço dentro do AKS podem ser expostas ao mundo exterior. Na imagem anterior, o controlador de entrada interpreta as regras de entrada configuradas para o cluster e configura automaticamente o Gateway de aplicativo Do Zure. Com base nessas regras, o Application Gateway direciona o tráfego para microserviços que executam dentro do AKS. O controlador de entrada ouve alterações nas regras de entrada e faz as alterações apropriadas no Gateway de aplicativo Do Azure.

## <a name="azure-api-management"></a>Gerenciamento de API do Azure

Para sistemas moderados a em larga escala nativos em nuvem, você pode considerar [o Gerenciamento de API do Azure](https://azure.microsoft.com/services/api-management/). É um serviço baseado em nuvem que não só resolve suas necessidades do API Gateway, mas fornece uma experiência administrativa e de desenvolvedor completo. O gerenciamento de API é mostrado na Figura 4-6.

![Gerenciamento de API do Azure](./media/azure-api-management.png)

**Figura 4-6.** Gerenciamento de API do Azure

Para começar, o Gerenciamento de API expõe um servidor de gateway que permite acesso controlado a serviços back-end com base em regras e políticas configuráveis. Esses serviços podem estar na nuvem do Azure, no seu data center on-prem ou em outras nuvens públicas. Chaves de API e tokens JWT determinam quem pode fazer o quê. Todo o tráfego está registrado para fins analíticos.

Para desenvolvedores, a API Management oferece um portal de desenvolvedores que fornece acesso a serviços, documentação e código de exemplo para invocá-los. Os desenvolvedores podem usar a API Swagger/Open para inspecionar pontos finais de serviço e analisar seu uso. O serviço funciona nas principais plataformas de desenvolvimento: .NET, Java, Golang e muito mais.

O portal do editor expõe um painel de gerenciamento onde os administradores expõem APIs e gerenciam seu comportamento. O acesso ao serviço pode ser concedido, serviço de saúde monitorado e telemetria de serviço saem. Os administradores aplicam *políticas* em cada ponto final para afetar o comportamento. [As políticas](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) são instruções pré-construídas que são executadas sequencialmente para cada chamada de serviço.  As políticas são configuradas para uma chamada de entrada, chamada de saída ou invocadas após um erro. As políticas podem ser aplicadas em diferentes escopos de serviço para permitir o ordenamento determinístico ao combinar políticas. O produto é fornecido com um grande número de [políticas](https://docs.microsoft.com/azure/api-management/api-management-policies)pré-construídas.

Aqui estão exemplos de como as políticas podem afetar o comportamento de seus serviços nativos na nuvem:  

- Restringir o acesso ao serviço.
- Impor autenticação.  
- Atender chamadas de uma única fonte, se necessário.
- Habilitar caching.
- Bloqueie chamadas de endereços IP específicos.
- Controle o fluxo do serviço.
- Converta solicitações de SOAP para REST ou entre diferentes formatos de dados, como de XML para JSON.

O Azure API Management pode expor serviços back-end que estão hospedados em qualquer lugar – na nuvem ou no data center. Para serviços legados que você pode expor em seus sistemas nativos da nuvem, ele suporta APIs REST e SOAP. Até mesmo outros serviços do Azure podem ser expostos através da API Management. Você pode colocar uma API gerenciada em cima de um serviço de backup do Azure, como [o Azure Service Bus](https://azure.microsoft.com/services/service-bus/) ou o [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/). O Azure API Management não inclui suporte de balanceamento de carga incorporado e deve ser usado em conjunto com um serviço de balanceamento de carga.

O Azure API Management está disponível em [quatro níveis diferentes:](https://azure.microsoft.com/pricing/details/api-management/)

- Desenvolvedor
- Basic
- Standard
- Premium

O nível Desenvolvedor destina-se a cargas de trabalho e avaliação não-produtivas. Os outros níveis oferecem progressivamente mais energia, recursos e contratos de nível de serviço mais altos (SLAs). O nível Premium oferece [suporte à Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) e a [várias regiões.](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region) Todas as camadas têm um preço fixo por hora.

Recentemente, a Microsoft anunciou um [nível sem servidor de Gerenciamento de API](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) para o Gerenciamento de API do Azure. Referido como o *nível de preços de consumo,* o serviço é uma variante do Gerenciamento de API projetado em torno do modelo de computação sem servidor. Ao contrário dos níveis de preços "pré-alocados" mostrados anteriormente, o nível de consumo fornece provisionamento instantâneo e preços de pagamento por ação.

Ele habilita os recursos do API Gateway para os seguintes casos de uso:

- Microserviços implementados usando tecnologias sem servidor, como [Funções do Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview) e [Aplicativos lógicos do Azure](https://azure.microsoft.com/services/logic-apps/).
- Recursos de serviço de suporte do Azure, como filas e tópicos do Service Bus, armazenamento do Azure e outros.
- Microserviços onde o tráfego tem picos ocasionais, mas permanece baixo na maioria das vezes.

O nível de consumo usa os mesmos componentes de Gerenciamento de API de serviço subjacente, mas emprega uma arquitetura totalmente diferente com base em recursos alocados dinamicamente. Ele se alinha perfeitamente com o modelo de computação sem servidor:

- Sem infra-estrutura para gerenciar.
- Sem capacidade ociosa.
- Alta disponibilidade.
- Escala automática.
- O custo é baseado no uso real.
  
O novo nível de consumo é uma ótima opção para sistemas nativos em nuvem que expõem recursos sem servidor como APIs.

> No momento da escrita, a camada de consumo está em visualização na nuvem do Azure.

## <a name="real-time-communication"></a>Comunicação em tempo real

A comunicação em tempo real, ou push, é outra opção para aplicativos front-end que se comunicam com sistemas nativos de nuvem back-end via HTTP. Aplicativos, como tickers financeiros, educação on-line, jogos e atualizações de progresso no trabalho, exigem respostas instantâneas e em tempo real do back-end. Com a comunicação HTTP normal, não há como o cliente saber quando novos dados estão disponíveis. O cliente deve *fazer uma pesquisa* contínua ou enviar solicitações ao servidor. Com a comunicação *em tempo real,* o servidor pode empurrar novos dados para o cliente a qualquer momento.

Os sistemas em tempo real são frequentemente caracterizados por fluxos de dados de alta frequência e um grande número de conexões simultâneas de clientes. A implementação manual da conectividade em tempo real pode rapidamente se tornar complexa, exigindo infra-estrutura não trivial para garantir escalabilidade e mensagens confiáveis aos clientes conectados. Você pode encontrar-se gerenciando uma instância do Azure Redis Cache e um conjunto de balanceadores de carga configurados com sessões pegajosas para afinidade com o cliente.

[O Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/) é um serviço Azure totalmente gerenciado que simplifica a comunicação em tempo real para seus aplicativos nativos da nuvem. Detalhes de implementação técnica, como provisionamento de capacidade, dimensionamento e conexões persistentes são abstratos. Eles são tratados para você com um contrato de 99,9% de nível de serviço. Você se concentra em recursos de aplicação, não em encanamento de infra-estrutura.

Uma vez ativado, um serviço HTTP baseado em nuvem pode empurrar atualizações de conteúdo diretamente para clientes conectados, incluindo aplicativos de navegador, celular e desktop. Os clientes são atualizados sem a necessidade de pesquisa no servidor. O Azure SignalR abstrai as tecnologias de transporte que criam conectividade em tempo real, incluindo WebSockets, Eventos do Lado do Servidor e Votação Longa. Os desenvolvedores se concentram em enviar mensagens para todos ou subconjuntos específicos de clientes conectados.

A Figura 4-7 mostra um conjunto de Clientes HTTP conectados a um aplicativo nativo da Nuvem com o Azure SignalR ativado.

![Azure SignalR](./media/azure-signalr-service.png)

**Figura 4-7.** Azure SignalR

Outra vantagem do Azure SignalR Service vem com a implementação de serviços nativos na nuvem sem servidor. Talvez seu código seja executado sob demanda com os gatilhos do Azure Functions. Esse cenário pode ser complicado porque seu código não mantém conexões longas com clientes. O Serviço Azure SignalR pode lidar com essa situação, uma vez que o serviço já gerencia conexões para você.

O Azure SignalR Service integra-se de perto com outros serviços do Azure, como O Banco de Dados SQL do Azure, Service Bus ou Redis Cache, abrindo muitas possibilidades para seus aplicativos nativos na nuvem.

>[!div class="step-by-step"]
>[Próximo](communication-patterns.md)
>[anterior](service-to-service-communication.md)
