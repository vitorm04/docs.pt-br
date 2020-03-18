---
title: Exemplos de design sem servidor - Aplicativos sem servidor
description: Entenda a variedade de cenários suportados por arquiteturas sem servidor, desde agendamento e processamento baseado em eventos até gatilhos de arquivos e processo de fluxo.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093549"
---
# <a name="serverless-design-examples"></a>Exemplos de design sem servidor

Existem muitos padrões de design que existem para sem servidor. Esta seção captura alguns cenários comuns que usam sem servidor. O que todos os exemplos têm em comum é a combinação fundamental de um gatilho de evento e lógica de negócios.

## <a name="scheduling"></a>Agendamento

Agendar tarefas é uma função comum. O diagrama a seguir mostra um banco de dados legado que não tem verificações de integridade apropriadas. O banco de dados deve ser limpo periodicamente. A função sem servidor encontra dados inválidos e os limpa. O gatilho é um temporizador que executa o código em um cronograma.

![Agendamento sem servidor](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Comando e segregação de responsabilidade de consulta (CQRS)

A Segregação de Responsabilidade de Comando e Consulta (CQRS) é um padrão que fornece diferentes interfaces para leitura (ou consulta) de dados e operações que modificam dados. Aborda vários problemas comuns. Nos sistemas tradicionais baseados em Create Read Update Delete (CRUD), os conflitos podem surgir do alto volume de leituras e gravações para o mesmo armazenamento de dados. O bloqueio pode ocorrer frequentemente e diminuir drasticamente as leituras. Muitas vezes, os dados são apresentados como um composto de vários objetos de domínio e as operações de leitura devem combinar dados de diferentes entidades.

Usando o CQRS, uma leitura pode envolver uma entidade especial "achatada" que modela dados da maneira como é consumido. A leitura é tratada de forma diferente do que é armazenada. Por exemplo, embora o banco de dados possa armazenar um contato como um registro de cabeçalho com um registro de endereço filho, a leitura pode envolver uma entidade com propriedades de cabeçalho e endereço. Há uma miríade de abordagens para criar o modelo de leitura. Pode ser materializado a partir de pontos de vista. As operações de atualização podem ser encapsuladas como eventos isolados que, em seguida, acionam atualizações para dois modelos diferentes. Existem modelos separados para leitura e escrita.

![Exemplo de CQRS](./media/cqrs-example.png)

Sem servidor pode acomodar o padrão CQRS fornecendo os pontos finais segregados. Uma função sem servidor acomoda consultas ou leituras, e uma função ou conjunto de funções sem servidor diferente lida com as operações de atualização. Uma função sem servidor também pode ser responsável por manter o modelo de leitura atualizado e pode ser acionada pelo feed de [alterações](https://docs.microsoft.com/azure/cosmos-db/change-feed)do banco de dados . O desenvolvimento front-end é simplificado para conectar-se aos pontos finais necessários. O processamento dos eventos é tratado na parte de trás. Este modelo também é bom para grandes projetos porque diferentes equipes podem trabalhar em diferentes operações.

## <a name="event-based-processing"></a>Processamento baseado em eventos

Em sistemas baseados em mensagens, os eventos são frequentemente coletados em filas ou tópicos de editor/assinante a serem acionados. Esses eventos podem desencadear funções sem servidor para executar uma parte da lógica de negócios. Um exemplo de processamento baseado em eventos são sistemas de origem de eventos. Um "evento" é levantado para marcar uma tarefa tão completa. Uma função sem servidor desencadeada pelo evento atualiza o documento de banco de dados apropriado. Uma segunda função sem servidor pode usar o evento para atualizar o modelo de leitura para o sistema. [A Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) oferece uma maneira de integrar eventos com funções como assinantes.

> Eventos são mensagens informantes. Para obter mais informações, consulte [o padrão Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Gatilhos e transformações de arquivos

Extrair, Transformar e Carregar (ETL) é uma função comercial comum. Serverless é uma ótima solução para ETL porque permite que o código seja acionado como parte de um pipeline. Os componentes de código individuais podem abordar vários aspectos. Uma função sem servidor pode baixar o arquivo, outra aplica a transformação e outra carrega os dados. O código pode ser testado e implantado independentemente, facilitando a manutenção e escala quando necessário.

![Gatilhos e transformações de arquivos sem servidor](./media/serverless-file-triggers.png)

No diagrama, "cool storage" fornece dados analisados no [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Quaisquer problemas encontrados no fluxo de dados acionam uma função Azure para resolver a anomalia.

## <a name="asynchronous-background-processing-and-messaging"></a>Processamento de antecedentes assíncronos e mensagens

Mensagens assíncronas e processamento em segundo plano permitem que os aplicativos iniciem processos sem ter que esperar. Um exemplo de processamento assíncrono é um aplicativo OCR. Uma imagem é submetida e enfileirada para processamento. A varredura da imagem para extrair texto pode levar tempo e, uma vez concluída, uma notificação é enviada. O Serverless pode lidar tanto com a invocação quanto com o resultado neste cenário.

## <a name="web-apps-and-apis"></a>APIs e aplicativos Web

Um cenário popular para sem servidor são os aplicativos n-tier, mais comumente aqueles em que a camada de interface do usuário é um aplicativo web. A popularidade do Single Page Applications (SPA) aumentou recentemente. Os aplicativos SPA renderizam uma única página e, em seguida, dependem de chamadas de API e os dados retornados para renderizar dinamicamente a nova interface do usuário sem recarregar uma página completa. A renderização do lado do cliente fornece um aplicativo muito mais rápido e responsivo ao usuário final.

Os pontos finais sem servidor acionados por chamadas HTTP podem ser usados para lidar com as solicitações de API. Por exemplo, uma empresa de serviços de anúncios pode chamar uma função sem servidor com informações de perfil do usuário para solicitar publicidade personalizada. A função sem servidor retorna o anúncio personalizado e a página da Web o torna.

![API web sem servidor](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Pipeline de dados

Funções sem servidor podem ser usadas para facilitar um pipeline de dados. Neste exemplo, um arquivo aciona uma função para traduzir dados em um arquivo CSV para linhas de dados em uma tabela. A tabela organizada permite que um painel Power BI apresente análises ao usuário final.

![Pipeline de dados sem servidor](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Processamento de fluxo

Dispositivos e sensores muitas vezes geram fluxos de dados que devem ser processados em tempo real. Existem uma série de tecnologias que podem capturar mensagens e fluxos de [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) e [IoT Hub](https://docs.microsoft.com/azure/iot-hub) para [Service Bus](https://docs.microsoft.com/azure/service-bus). Independentemente do transporte, o serverless é um mecanismo ideal para processar as mensagens e fluxos de dados à medida que entram. Sem servidor pode escalar rapidamente para atender à demanda de grandes volumes de dados. O código sem servidor pode aplicar a lógica de negócios para analisar os dados e a saída em um formato estruturado para ação e análise.

![Processamento de fluxo sem servidor](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Gateway de API

Um gateway de API fornece um único ponto de entrada para clientes e, em seguida, direciona de forma inteligente as solicitações para serviços back-end. É útil gerenciar grandes conjuntos de serviços. Ele também pode lidar com a versão e simplificar o desenvolvimento conectando facilmente clientes a ambientes diferentes. O Serverless pode lidar com o dimensionamento back-end de microsserviços individuais enquanto apresenta um único front-end através de um gateway de API.

![Gateway de API sem servidor](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Recursos recomendados

- [Grade de Eventos Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Desafios e soluções de gerenciamento de dados distribuídos](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Projetando microsserviços: identificando limites de microsserviços](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Hubs de Eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Padrão de Sourcing de Eventos](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Implementando o padrão de Disjuntor](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [Hub IoT](https://docs.microsoft.com/azure/iot-hub)
- [Barramento de Serviço](https://docs.microsoft.com/azure/service-bus)
- [Trabalhando com o suporte ao feed de alterações no Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Próximo](serverless-architecture-considerations.md)
>[anterior](azure-serverless-platform.md)
