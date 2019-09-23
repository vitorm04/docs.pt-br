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
# <a name="protocol-buffers"></a><span data-ttu-id="14d1f-103">Buffers de protocolo</span><span class="sxs-lookup"><span data-stu-id="14d1f-103">Protocol buffers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="14d1f-104">os serviços gRPCs enviam e recebem dados como *mensagens de buffer de protocolo (Protobuf)* , semelhantes aos contratos de dados do WCF.</span><span class="sxs-lookup"><span data-stu-id="14d1f-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="14d1f-105">O Protobuf é uma maneira eficiente de serializar dados estruturados para que as máquinas sejam lidas e gravadas, sem a sobrecarga de que os formatos legíveis, como XML ou JSON, incorrem.</span><span class="sxs-lookup"><span data-stu-id="14d1f-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="14d1f-106">Este capítulo aborda como o Protobuf funciona e como definir suas próprias mensagens Protobuf.</span><span class="sxs-lookup"><span data-stu-id="14d1f-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="14d1f-107">Como o Protobuf funciona</span><span class="sxs-lookup"><span data-stu-id="14d1f-107">How Protobuf works</span></span>

<span data-ttu-id="14d1f-108">A maioria das técnicas de serialização de objeto do .NET, incluindo os contratos de dados do WCF, trabalha usando a reflexão para analisar a estrutura do objeto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="14d1f-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="14d1f-109">Por outro lado, a maioria das bibliotecas Protobuf exige que você defina a estrutura com antecedência usando uma linguagem dedicada (linguagem de buffer `.proto` de*protocolo*) em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="14d1f-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="14d1f-110">Esse arquivo é usado por um compilador para gerar código para qualquer uma das plataformas com suporte, incluindo .NET, Java, C/C++, JavaScript e muito mais.</span><span class="sxs-lookup"><span data-stu-id="14d1f-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="14d1f-111">O compilador Protobuf, `protoc`, é mantido pelo Google, embora haja implementações alternativas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="14d1f-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="14d1f-112">O código gerado é eficiente e otimizado para serialização rápida e desserialização de dados.</span><span class="sxs-lookup"><span data-stu-id="14d1f-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="14d1f-113">O formato de conexão de Protobuf em si é uma codificação binária, que usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens.</span><span class="sxs-lookup"><span data-stu-id="14d1f-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="14d1f-114">O conhecimento do formato de codificação binária não é necessário para usar o Protobuf, mas se você estiver interessado, poderá saber mais sobre ele no [site buffers de protocolo](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="14d1f-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="14d1f-115">[Anterior](why-grpc.md)
>[Próximo](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="14d1f-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
