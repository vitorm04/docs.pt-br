---
title: Serviços de streaming versus campos repetidos-gRPC para desenvolvedores do WCF
description: Compare campos repetidos com serviços de streaming como maneiras de passar coleções de dados usando gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503377"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>serviços de streaming gRPC versus campos repetidos

os serviços gRPCs fornecem duas maneiras de retornar conjuntos de valores ou listas de objetos. A especificação de mensagem buffers de protocolo usa a palavra-chave `repeated` para declarar listas ou matrizes de mensagens em outra mensagem. A especificação de serviço gRPC usa a palavra-chave `stream` para declarar uma conexão persistente de execução longa. Através dessa conexão, várias mensagens são enviadas e podem ser processadas individualmente. 

Você também pode usar o recurso `stream` para dados temporais de longa execução, como notificações ou mensagens de log. Mas este capítulo considerará seu uso para retornar um único conjunto de um.

Que você deve usar depende de fatores como:

- O tamanho geral do conjunto de datas.
- O tempo necessário para criar o conjunto de um DataSet no cliente ou no servidor final.
- Se o consumidor do conjunto de dado pode começar a agir assim que o primeiro item estiver disponível ou precisar que o conjunto de dado completo faça algo útil.

## <a name="when-to-use-repeated-fields"></a>Quando usar campos de `repeated`

Para qualquer conjunto de banco de forma restrito em tamanho e que possa ser gerado em sua totalidade em um curto tempo – digamos, em um segundo, você deve usar um campo de `repeated` em uma mensagem de Protobuf comum. Por exemplo, em um sistema de comércio eletrônico, para criar uma lista de itens em um pedido é provavelmente rápido e a lista não será muito grande. Retornar uma única mensagem com um campo de `repeated` é uma ordem de magnitude mais rápido do que usar `stream` e incorre em menos sobrecarga de rede.

Se o cliente precisar de todos os dados antes de começar a processá-lo e se o conjunto for pequeno o suficiente para construir na memória, considere usar um campo de `repeated`. Considere-o mesmo se a criação do conjunto de uma na memória no servidor for mais lenta.

## <a name="when-to-use-stream-methods"></a>Quando usar os métodos de `stream`

Quando os objetos de mensagem em seus conjuntos de valores são potencialmente muito grandes, é melhor transferi-los usando solicitações de streaming ou respostas. É mais eficiente construir um objeto grande na memória, gravá-lo na rede e, em seguida, liberar os recursos. Essa abordagem melhorará a escalabilidade do seu serviço.

Da mesma forma, você deve enviar conjuntos de datas de tamanho irrestrito sobre fluxos para evitar ficar sem memória ao construí-los.

Para conjuntos de clientes em que o consumidor pode processar cada item separadamente, você deve considerar o uso de um fluxo se isso significa que o progresso pode ser indicado para o usuário. O uso de um fluxo pode melhorar a capacidade de resposta de um aplicativo, mas você deve equilibrá-lo em relação ao desempenho geral do aplicativo.

Outro cenário em que os fluxos podem ser úteis é onde uma mensagem está sendo processada em vários serviços. Se cada serviço em uma cadeia retornar um fluxo, o serviço de terminal (ou seja, o último na cadeia) poderá começar a retornar mensagens. Essas mensagens podem ser processadas e passadas de volta ao longo da cadeia para o solicitante original. O solicitante pode retornar um fluxo ou agregar os resultados em uma única mensagem de resposta. Essa abordagem se presta bem a padrões como o MapReduce.

>[!div class="step-by-step"]
>[Anterior](migrate-duplex-services.md)
>[Próximo](client-libraries.md)
