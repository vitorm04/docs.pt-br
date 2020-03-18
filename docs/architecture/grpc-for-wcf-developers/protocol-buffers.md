---
title: Buffers de protocolo - gRPC para desenvolvedores WCF
description: Introdução ao formato de fio Protocol Buffers usado para rede gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147926"
---
# <a name="protocol-buffers"></a>Buffers de protocolo

Os serviços gRPC enviam e recebem dados como *mensagens de Buffer de Protocolo (Protobuf),* semelhantes aos contratos de dados na Windows Communication Foundation (WCF). Protobuf é uma maneira eficiente de serializar dados estruturados para as máquinas lerem e escreverem, sem a sobrecarga que formatos leíveis por humanos como XML ou JSON incorrem.

Este capítulo abrange como o Protobuf funciona e como definir suas próprias mensagens Protobuf.

## <a name="how-protobuf-works"></a>Como funciona o Protobuf

A maioria das técnicas de serialização de objetos .NET, incluindo os contratos de dados do WCF, funciona usando a reflexão para analisar a estrutura do objeto em tempo de execução. Em contraste, a maioria das bibliotecas Protobuf exige que você defina a estrutura `.proto` na frente usando uma linguagem dedicada *(Protocol Buffer Language)* em um arquivo. Em seguida, um compilador usa este arquivo para gerar código para qualquer uma das plataformas suportadas. As plataformas suportadas incluem .NET, Java, C/C++, JavaScript e muito mais.

O compilador Protobuf `protoc`é mantido pelo Google, embora implementações alternativas estejam disponíveis. O código gerado é eficiente e otimizado para rápida serialização e desserialização de dados.

O formato de fio Protobuf é uma codificação binária. Ele usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens. O conhecimento do formato de codificação binária não é necessário para usar o Protobuf. Mas se você estiver interessado, você pode aprender mais sobre isso [no site do Protocol Buffers](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Próximo](why-grpc.md)
>[anterior](protobuf-messages.md)
