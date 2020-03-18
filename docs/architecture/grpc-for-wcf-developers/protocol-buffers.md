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
# <a name="protocol-buffers"></a><span data-ttu-id="4d522-103">Buffers de protocolo</span><span class="sxs-lookup"><span data-stu-id="4d522-103">Protocol buffers</span></span>

<span data-ttu-id="4d522-104">Os serviços gRPC enviam e recebem dados como *mensagens de Buffer de Protocolo (Protobuf),* semelhantes aos contratos de dados na Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4d522-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="4d522-105">Protobuf é uma maneira eficiente de serializar dados estruturados para as máquinas lerem e escreverem, sem a sobrecarga que formatos leíveis por humanos como XML ou JSON incorrem.</span><span class="sxs-lookup"><span data-stu-id="4d522-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="4d522-106">Este capítulo abrange como o Protobuf funciona e como definir suas próprias mensagens Protobuf.</span><span class="sxs-lookup"><span data-stu-id="4d522-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="4d522-107">Como funciona o Protobuf</span><span class="sxs-lookup"><span data-stu-id="4d522-107">How Protobuf works</span></span>

<span data-ttu-id="4d522-108">A maioria das técnicas de serialização de objetos .NET, incluindo os contratos de dados do WCF, funciona usando a reflexão para analisar a estrutura do objeto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4d522-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="4d522-109">Em contraste, a maioria das bibliotecas Protobuf exige que você defina a estrutura `.proto` na frente usando uma linguagem dedicada *(Protocol Buffer Language)* em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4d522-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="4d522-110">Em seguida, um compilador usa este arquivo para gerar código para qualquer uma das plataformas suportadas.</span><span class="sxs-lookup"><span data-stu-id="4d522-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="4d522-111">As plataformas suportadas incluem .NET, Java, C/C++, JavaScript e muito mais.</span><span class="sxs-lookup"><span data-stu-id="4d522-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span>

<span data-ttu-id="4d522-112">O compilador Protobuf `protoc`é mantido pelo Google, embora implementações alternativas estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="4d522-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="4d522-113">O código gerado é eficiente e otimizado para rápida serialização e desserialização de dados.</span><span class="sxs-lookup"><span data-stu-id="4d522-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="4d522-114">O formato de fio Protobuf é uma codificação binária.</span><span class="sxs-lookup"><span data-stu-id="4d522-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="4d522-115">Ele usa alguns truques inteligentes para minimizar o número de bytes usados para representar mensagens.</span><span class="sxs-lookup"><span data-stu-id="4d522-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="4d522-116">O conhecimento do formato de codificação binária não é necessário para usar o Protobuf.</span><span class="sxs-lookup"><span data-stu-id="4d522-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="4d522-117">Mas se você estiver interessado, você pode aprender mais sobre isso [no site do Protocol Buffers](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="4d522-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4d522-118">[Próximo](why-grpc.md)
>[anterior](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="4d522-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
