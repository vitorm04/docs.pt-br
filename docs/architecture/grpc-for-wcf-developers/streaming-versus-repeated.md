---
title: Serviços de streaming vs. campos repetidos - gRPC para desenvolvedores WCF
description: Compare campos repetidos com serviços de streaming como formas de passar coletas de dados usando gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147744"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>Serviços de streaming gRPC versus campos repetidos

Os serviços gRPC fornecem duas maneiras de retornar conjuntos de dados ou listas de objetos. A especificação de mensagem `repeated` Buffers de protocolo usa a palavra-chave para declarar listas ou matrizes de mensagens em outra mensagem. A especificação de serviço `stream` gRPC usa a palavra-chave para declarar uma conexão persistente de longa duração. Sobre essa conexão, várias mensagens são enviadas e podem ser processadas individualmente.

Você também pode `stream` usar o recurso para dados temporais de longa duração, como notificações ou mensagens de registro. Mas este capítulo considerará seu uso para retornar um único conjunto de dados.

O que você deve usar depende de fatores como:

- O tamanho geral do conjunto de dados.
- O tempo que levou para criar o conjunto de dados no cliente ou no final do servidor.
- Se o consumidor do conjunto de dados pode começar a agir sobre ele assim que o primeiro item estiver disponível, ou precisa do conjunto de dados completo para fazer qualquer coisa útil.

## <a name="when-to-use-repeated-fields"></a>Quando usar `repeated` campos

Para qualquer conjunto de dados que esteja limitado em tamanho e que possa ser gerado em sua totalidade `repeated` em um curto espaço de tempo — digamos, em menos de um segundo — você deve usar um campo em uma mensagem Protobuf regular. Por exemplo, em um sistema de comércio eletrônico, construir uma lista de itens dentro de um pedido é provavelmente rápido e a lista não será muito grande. Devolver uma única mensagem com um `repeated` campo é `stream` uma ordem de magnitude mais rápida do que usar e incorre em menos sobrecarga de rede.

Se o cliente precisar de todos os dados antes de começar a processá-los `repeated` e o conjunto de dados for pequeno o suficiente para construir na memória, então considere usar um campo. Considere-o mesmo que a criação do conjunto de dados na memória no servidor seja mais lenta.

## <a name="when-to-use-stream-methods"></a>Quando usar `stream` métodos

Quando os objetos de mensagem em seus conjuntos de dados são potencialmente muito grandes, é melhor transferi-los usando solicitações de streaming ou respostas. É mais eficiente construir um objeto grande na memória, escrevê-lo para a rede e, em seguida, liberar os recursos. Essa abordagem melhorará a escalabilidade do seu serviço.

Da mesma forma, você deve enviar conjuntos de dados de tamanho não restrito sobre fluxos para evitar ficar sem memória ao construí-los.

Para conjuntos de dados onde o consumidor pode processar separadamente cada item, você deve considerar o uso de um fluxo se isso significar que o progresso pode ser indicado para o usuário. O uso de um fluxo pode melhorar a capacidade de resposta de um aplicativo, mas você deve equilibrá-lo em relação ao desempenho geral do aplicativo.

Outro cenário onde os fluxos podem ser úteis é onde uma mensagem está sendo processada em vários serviços. Se cada serviço em uma cadeia retornar um fluxo, então o serviço de terminal (ou seja, o último da cadeia) pode começar a retornar mensagens. Essas mensagens podem ser processadas e transmitidas ao longo da cadeia para o solicitante original. O solicitante pode retornar um fluxo ou agregar os resultados em uma única mensagem de resposta. Essa abordagem se presta bem a padrões como MapReduce.

>[!div class="step-by-step"]
>[Próximo](migrate-duplex-services.md)
>[anterior](client-libraries.md)
