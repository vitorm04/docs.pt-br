---
title: Buffers de protocolo-gRPC para desenvolvedores do WCF
description: Introdução ao formato de conexão de buffers de protocolo usado para rede gRPC.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184165"
---
# <a name="protocol-buffers"></a>Buffers de protocolo

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

os serviços gRPCs enviam e recebem dados como *mensagens de buffer de protocolo (Protobuf)* , semelhantes aos contratos de dados do WCF. O Protobuf é uma maneira eficiente de serializar dados estruturados para que as máquinas sejam lidas e gravadas, sem a sobrecarga de que os formatos legíveis, como XML ou JSON, incorrem.

Este capítulo aborda como o Protobuf funciona e como definir suas próprias mensagens Protobuf.

## <a name="how-protobuf-works"></a>Como o Protobuf funciona

A maioria das técnicas de serialização de objeto do .NET, incluindo os contratos de dados do WCF, trabalha usando a reflexão para analisar a estrutura do objeto em tempo de execução. Por outro lado, a maioria das bibliotecas Protobuf exige que você defina a estrutura com antecedência usando uma linguagem dedicada (linguagem de buffer `.proto` de*protocolo*) em um arquivo. Esse arquivo é usado por um compilador para gerar código para qualquer uma das plataformas com suporte, incluindo .NET, Java, C/C++, JavaScript e muito mais. O compilador Protobuf, `protoc`, é mantido pelo Google, embora haja implementações alternativas disponíveis. O código gerado é eficiente e otimizado para serialização rápida e desserialização de dados.

O formato de conexão de Protobuf em si é uma codificação binária, que usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens. O conhecimento do formato de codificação binária não é necessário para usar o Protobuf, mas se você estiver interessado, poderá saber mais sobre ele no [site buffers de protocolo](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Anterior](why-grpc.md)
>[Próximo](protobuf-messages.md)
