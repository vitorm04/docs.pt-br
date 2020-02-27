---
title: Migrar uma solução WCF para o gRPC-gRPC para desenvolvedores do WCF
description: Como migrar diferentes tipos de serviços WCF para o equivalente em gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628508"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="a6d7a-103">Migrar uma solução WCF para o gRPC</span><span class="sxs-lookup"><span data-stu-id="a6d7a-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="a6d7a-104">Este capítulo descreverá como trabalhar com projetos ASP.NET Core 3,0 gRPC e demonstrar a migração de diferentes tipos de serviços de Windows Communication Foundation (WCF) para o equivalente gRPC:</span><span class="sxs-lookup"><span data-stu-id="a6d7a-104">This chapter will describe how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="a6d7a-105">Crie um projeto ASP.NET Core gRPC 3,0.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="a6d7a-106">Operações simples de solicitação-resposta para RPC unário gRPC.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="a6d7a-107">Operações unidirecionais para RPC de streaming de cliente gRPC.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="a6d7a-108">Serviços Full duplex para RPC de streaming bidirecional gRPC.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="a6d7a-109">Também há uma comparação entre usar os serviços de streaming versus campos repetidos para retornar conjuntos de valores, e há uma discussão sobre o uso de bibliotecas de cliente no final do capítulo.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="a6d7a-110">O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de comércio de estoque.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="a6d7a-111">Ele usa a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada Autofac para injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="a6d7a-112">Ele inclui três serviços, um para cada tipo de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="a6d7a-113">Os serviços serão discutidos mais detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="a6d7a-114">Você pode baixar as soluções de [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="a6d7a-115">Os serviços usam dados falsos para minimizar dependências externas.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="a6d7a-116">Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.</span><span class="sxs-lookup"><span data-stu-id="a6d7a-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a6d7a-117">[Anterior](ws-protocols.md)
>[Próximo](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="a6d7a-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
