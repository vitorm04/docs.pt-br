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
# <a name="protocol-buffers"></a><span data-ttu-id="b52d9-103">Buffers de protocolo</span><span class="sxs-lookup"><span data-stu-id="b52d9-103">Protocol buffers</span></span>

<span data-ttu-id="b52d9-104">os serviços gRPCs enviam e recebem dados como *mensagens de buffer de protocolo (Protobuf)* , semelhantes aos contratos de dados no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b52d9-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b52d9-105">O Protobuf é uma maneira eficiente de serializar dados estruturados para que as máquinas sejam lidas e gravadas, sem a sobrecarga de que os formatos legíveis, como XML ou JSON, incorrem.</span><span class="sxs-lookup"><span data-stu-id="b52d9-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="b52d9-106">Este capítulo aborda como o Protobuf funciona e como definir suas próprias mensagens Protobuf.</span><span class="sxs-lookup"><span data-stu-id="b52d9-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="b52d9-107">Como o Protobuf funciona</span><span class="sxs-lookup"><span data-stu-id="b52d9-107">How Protobuf works</span></span>

<span data-ttu-id="b52d9-108">A maioria das técnicas de serialização de objeto do .NET, incluindo os contratos de dados do WCF, trabalha usando a reflexão para analisar a estrutura do objeto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b52d9-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="b52d9-109">Por outro lado, a maioria das bibliotecas Protobuf exige que você defina a estrutura com antecedência usando uma linguagem dedicada (*linguagem de buffer de protocolo*) em um arquivo de `.proto`.</span><span class="sxs-lookup"><span data-stu-id="b52d9-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="b52d9-110">Em seguida, um compilador usa esse arquivo para gerar código para qualquer uma das plataformas com suporte.</span><span class="sxs-lookup"><span data-stu-id="b52d9-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="b52d9-111">As plataformas com suporte incluem .NET, Java,C++C/, JavaScript e muito mais.</span><span class="sxs-lookup"><span data-stu-id="b52d9-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span> 

<span data-ttu-id="b52d9-112">O compilador Protobuf, `protoc`, é mantido pelo Google, embora haja implementações alternativas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b52d9-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="b52d9-113">O código gerado é eficiente e otimizado para serialização rápida e desserialização de dados.</span><span class="sxs-lookup"><span data-stu-id="b52d9-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="b52d9-114">O formato de fio Protobuf é uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="b52d9-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="b52d9-115">Ele usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens.</span><span class="sxs-lookup"><span data-stu-id="b52d9-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="b52d9-116">O conhecimento do formato de codificação binária não é necessário para usar o Protobuf.</span><span class="sxs-lookup"><span data-stu-id="b52d9-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="b52d9-117">Mas, se você estiver interessado, poderá aprender mais sobre ele no [site buffers de protocolo](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="b52d9-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b52d9-118">[Anterior](why-grpc.md)
>[Próximo](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="b52d9-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
