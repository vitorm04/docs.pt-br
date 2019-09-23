---
title: serviços de streaming gRPC versus campos repetidos-gRPC para desenvolvedores do WCF
description: Comparando campos repetidos aos serviços de streaming como maneiras de passar coleções de dados com gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7dc3c8f5bf2efc304da7d50661ba47db500e67a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184067"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>serviços de streaming gRPC versus campos repetidos

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

os serviços gRPCs fornecem duas maneiras de retornar conjuntos de valores ou listas de objetos. A especificação de mensagem buffers de protocolo `repeated` usa a palavra-chave para declarar listas ou matrizes de mensagens em outra mensagem. A especificação de serviço gRPC usa `stream` a palavra-chave para declarar uma conexão persistente de execução longa sobre a qual várias mensagens são enviadas e pode ser processada individualmente. O `stream` recurso também pode ser usado para dados temporais de longa execução, como notificações ou mensagens de log, mas este capítulo considerará seu uso para retornar um único conjunto de dado.

Que você deve usar depende de vários fatores, como o tamanho geral do conjunto de data, o tempo necessário para criar o conjunto de um cliente ou servidor de extremidade, e se o consumidor do conjunto de um pode começar a agir assim que o primeiro item estiver disponível ou precisa que o conjunto de dado completo faça algo útil.

## <a name="when-to-use-repeated-fields"></a>Quando usar `repeated` campos

Para qualquer conjunto de data restrito em tamanho e que possa ser gerado em sua totalidade em um curto tempo – digamos, em um segundo, você deve usar um `repeated` campo em uma mensagem Protobuf regular. Por exemplo, em um sistema de comércio eletrônico, para criar uma lista de itens em um pedido é provavelmente rápido e a lista não será muito grande. Retornar uma única mensagem com um `repeated` campo é uma ordem de magnitude mais rápida do que `stream` usar um e incorre em menos sobrecarga de rede.

Se o cliente precisar de todos os dados antes de começar a processá-lo e se o conjunto for pequeno o suficiente para construir na `repeated` memória, considere usar um campo mesmo se a criação real do conjunto de dados na memória no servidor for mais lenta.

## <a name="when-to-use-stream-methods"></a>Quando usar `stream` métodos

Os conjuntos de valores em que os objetos de mensagem são potencialmente muito grandes são transferidos melhor usando solicitações de streaming ou respostas. É mais eficiente construir um objeto grande na memória, gravá-lo na rede e, em seguida, liberar os recursos. Essa abordagem melhorará a escalabilidade do seu serviço.

Da mesma forma, os conjuntos de datas de tamanho irrestrito devem ser enviados por fluxos para evitar a ausência de memória ao construí-los.

Para conjuntos de valores em que cada item individual pode ser processado separadamente pelo consumidor, você deve considerar o uso de um fluxo se isso significa que o progresso pode ser indicado para o usuário final. Isso pode melhorar a capacidade de resposta aparente de um aplicativo, embora isso deva ser equilibrado em relação ao desempenho geral do aplicativo.

Outro cenário em que os fluxos podem ser úteis é onde uma mensagem está sendo processada em vários serviços. Se cada serviço em uma cadeia retornar um fluxo, o serviço de terminal (ou seja, o último na cadeia) poderá começar a retornar mensagens que podem ser processadas e passadas de volta ao longo da cadeia para o solicitante original, que pode retornar um fluxo ou agregar o resulta em uma única mensagem de resposta. Essa abordagem se presta bem a padrões como mapear/reduzir.

>[!div class="step-by-step"]
>[Anterior](migrate-duplex-services.md)
>[Próximo](client-libraries.md)
