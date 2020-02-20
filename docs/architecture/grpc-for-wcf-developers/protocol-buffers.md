---
title: Buffers de protocolo-gRPC para desenvolvedores do WCF
description: Introdução ao formato de conexão de buffers de protocolo usado para rede gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503449"
---
# <a name="protocol-buffers"></a>Buffers de protocolo

os serviços gRPCs enviam e recebem dados como *mensagens de buffer de protocolo (Protobuf)* , semelhantes aos contratos de dados no Windows Communication Foundation (WCF). O Protobuf é uma maneira eficiente de serializar dados estruturados para que as máquinas sejam lidas e gravadas, sem a sobrecarga de que os formatos legíveis, como XML ou JSON, incorrem.

Este capítulo aborda como o Protobuf funciona e como definir suas próprias mensagens Protobuf.

## <a name="how-protobuf-works"></a>Como o Protobuf funciona

A maioria das técnicas de serialização de objeto do .NET, incluindo os contratos de dados do WCF, trabalha usando a reflexão para analisar a estrutura do objeto em tempo de execução. Por outro lado, a maioria das bibliotecas Protobuf exige que você defina a estrutura com antecedência usando uma linguagem dedicada (*linguagem de buffer de protocolo*) em um arquivo de `.proto`. Em seguida, um compilador usa esse arquivo para gerar código para qualquer uma das plataformas com suporte. As plataformas com suporte incluem .NET, Java,C++C/, JavaScript e muito mais. 

O compilador Protobuf, `protoc`, é mantido pelo Google, embora haja implementações alternativas disponíveis. O código gerado é eficiente e otimizado para serialização rápida e desserialização de dados.

O formato de fio Protobuf é uma codificação binária. Ele usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens. O conhecimento do formato de codificação binária não é necessário para usar o Protobuf. Mas, se você estiver interessado, poderá aprender mais sobre ele no [site buffers de protocolo](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Anterior](why-grpc.md)
>[Próximo](protobuf-messages.md)
