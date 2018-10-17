---
title: Exemplos de design sem servidor - aplicativos sem servidor
description: Entenda a variedade de cenários com suporte pelo arquiteturas sem servidor, de agendamento e processamento baseado em evento para os gatilhos de arquivo e o processo de fluxo.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 0261b9f17f133942d635cf331d8cef414378bd90
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369604"
---
# <a name="serverless-design-examples"></a>Exemplos de design sem servidor

Há vários padrões de design que existem para sem servidor. Esta seção captura alguns cenários comuns que usam sem servidor. O que todos os exemplos têm em comum é a combinação fundamental de uma evento gatilho e lógica de negócios.

## <a name="scheduling"></a>Agendamento

Agendamento de tarefas é uma função comum. O diagrama a seguir mostra um banco de dados herdado que não tem as verificações de integridade apropriado. O banco de dados deve ser removido periodicamente. A função sem servidor localiza dados inválidos e limpa a ele. O gatilho é um temporizador que executa o código em um agendamento.

![Agendamento sem servidor](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Comando e segregação de responsabilidade de consulta (CQRS)

Comando e segregação de responsabilidade de consulta (CQRS) é um padrão que fornece dados de interfaces diferentes para leitura (ou consulta) e operações que modificam dados. Ele aborda vários problemas comuns. Em sistemas tradicionais de criar leitura Update Delete (CRUD) com base, conflitos podem surgir de alto volume de leituras e gravações para o mesmo armazenamento de dados. O bloqueio pode ocorrer com frequência e reduzir drasticamente a velocidade de leituras. Muitas vezes, os dados são apresentados como uma composição de vários objetos de domínio e as operações de leitura deve combinar dados de entidades diferentes.

Usando o CQRS, uma leitura pode envolver uma entidade "nivelada" especial que modela a maneira como ele é consumido de dados. A leitura é tratada de maneira diferente de como ele é armazenado. Por exemplo, embora o banco de dados pode armazenar um contato como um registro de cabeçalho com um registro de endereço filho, a leitura pode envolver uma entidade com o cabeçalho e propriedades de endereço. Há várias abordagens para criar o modelo de leitura. Ele pode ser materializado de modos de exibição. Operações de atualização podem ser encapsuladas como eventos isolados que, em seguida, disparam atualizações para os dois modelos diferentes. Existem modelos separados para leitura e gravação.

![Exemplo CQRS](./media/cqrs-example.png)

Sem servidor pode acomodar o padrão CQRS, fornecendo os pontos de extremidade segregados. Uma função sem servidor acomoda consultas ou leituras e trata de uma função sem servidor diferente ou um conjunto de funções de operações de atualização. Uma função sem servidor também pode ser responsável por manter o modelo de leitura atualizada e pode ser disparada pelo banco de dados [o feed de alterações](https://docs.microsoft.com/azure/cosmos-db/change-feed). Desenvolvimento de front-end é simplificado para conectar-se aos pontos de extremidade necessários. Processamento de eventos é tratado no back-end. Esse modelo também é bem dimensionada para projetos grandes pois equipes diferentes podem trabalhar em operações diferentes.

## <a name="event-based-processing"></a>Processamento baseado em evento

Em sistemas baseados em mensagens, os eventos são coletados com frequência em filas ou tópicos de publicador/assinante a ser afetado. Esses eventos podem disparar funções sem servidor para executar uma parte da lógica de negócios. Um exemplo de processamento com base em eventos é sistemas de origem de evento. Um "evento" é gerado para marcar uma tarefa como concluída. Uma função sem servidor disparada pelo evento atualiza o documento de banco de dados apropriado. Uma segunda função sem servidor pode usar o evento para atualizar o modelo de leitura para o sistema. [A grade de eventos do Azure](https://docs.microsoft.com/azure/event-grid/overview) fornece uma maneira de integrar eventos com funções como assinantes.

> Os eventos são mensagens informativas. Para obter mais informações, consulte [padrão de fornecimento do evento](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Os gatilhos de arquivo e transformações

Extração, transformação e carregamento (ETL) é uma função comercial comum. Sem servidor é uma ótima solução para ETL porque ele permite que o código ser disparado como parte de um pipeline. Componentes individuais de código podem abordar vários aspectos. Uma função sem servidor pode baixar o arquivo, outro se aplica a transformação e outra carrega os dados. O código pode ser testado e implantado independentemente, tornando mais fácil de manter e dimensionar quando necessário.

![As transformações e os gatilhos de arquivo sem servidor](./media/serverless-file-triggers.png)

No diagrama, "armazenamento esporádico" fornece dados que são analisados em [do Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Todos os problemas encontrados no fluxo de dados disparam uma função do Azure para tratar da anomalia.

## <a name="asynchronous-background-processing-and-messaging"></a>Processamento assíncrono em segundo plano e o sistema de mensagens

Mensagens assíncronas e processamento em segundo plano permitem que aplicativos disparar processos sem ter de esperar. Um exemplo de processamento assíncrono é um aplicativo de OCR. Uma imagem é enviada e enfileirada para processamento. Digitalizar a imagem para extrair o texto pode levar tempo e quando ele tiver terminado de uma notificação é enviada. Sem servidor pode lidar com a invocação e o resultado nesse cenário.

## <a name="web-apps-and-apis"></a>Aplicativos web e APIs

Um cenário comum para sem servidor é N-camadas aplicativos, mais comumente os onde a camada de interface do usuário é um aplicativo web. A popularidade dos aplicativos de página única (SPA) tem aumentaram recentemente. Aplicativos SPA renderizam uma única página, em seguida, contam com chamadas de API e os dados retornados para renderizar dinamicamente a nova interface do usuário sem recarregar uma página inteira. Renderização do lado do cliente fornece um aplicativo muito mais rápido e mais responsivo ao usuário final.

Pontos de extremidade sem servidor disparados por chamadas HTTP podem ser usados para manipular as solicitações de API. Por exemplo, uma empresa de serviços do ad pode chamar uma função sem servidor com as informações de perfil do usuário para solicitar anúncios personalizados. A função sem servidor retorna ad personalizado e renderiza-o a página da web.

![API da web sem servidor](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Pipeline de dados

Funções sem servidor podem ser usadas para facilitar a um pipeline de dados. Neste exemplo, um arquivo dispara uma função para converter dados em um arquivo CSV para linhas de dados em uma tabela. A tabela organizada permite um dashboard do Power BI apresentar a análise para o usuário final.

![Pipeline de dados sem servidor](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Processamento de Stream

Dispositivos e sensores geralmente geram fluxos de dados que devem ser processados em tempo real. Há várias tecnologias que podem capturar mensagens e fluxos a partir de [dos Hubs de eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) e [IoT Hub](https://docs.microsoft.com/azure/iot-hub) para [do barramento de serviço](/service-bus). Independentemente do transporte, sem servidor é um mecanismo ideal para processar as mensagens e os fluxos de dados conforme eles chegam. Sem servidor pode ser dimensionados rapidamente para atender à demanda de grandes volumes de dados. O código sem servidor pode aplicar a lógica de negócios para analisar os dados e a saída em um formato estruturado para análise e ação.

![Processamento de fluxo sem servidor](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Gateway de API

Um gateway de API fornece um único ponto de entrada para os clientes e, em seguida, inteligentemente encaminha solicitações para serviços de back-end. É útil gerenciar grandes conjuntos de serviços. Ele também pode lidar com o controle de versão e simplificar o desenvolvimento por conectar facilmente os clientes com ambientes diferentes. Sem servidor pode lidar com o back-end de dimensionamento de microsserviços individuais ao apresentar um único front-end por meio de um gateway de API.

![Gateway de API sem servidor](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Recursos recomendados

* [Grade de Eventos do Azure](https://docs.microsoft.com/azure/event-grid/overview)
* [Hub IoT do Azure](https://docs.microsoft.com/azure/iot-hub)
* [Desafios e soluções de gerenciamento de dados distribuídos](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md)
* [Criando microsserviços: identificando limites de microsserviço](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Hubs de eventos](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Padrão de fornecimento do evento](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Implementando o padrão de disjuntor](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [Hub IoT](https://docs.microsoft.com/azure/iot-hub)
* [Barramento de serviço](https://docs.microsoft.com/azure/service-bus)
* [Trabalhando com a alteração de feed de suporte no Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
[Anterior](serverless-architecture-considerations.md)
[Próximo](azure-serverless-platform.md)