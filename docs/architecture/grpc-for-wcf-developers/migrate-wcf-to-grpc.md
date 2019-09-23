---
title: Migrar uma solução WCF para o gRPC-gRPC para desenvolvedores do WCF
description: Como migrar diferentes tipos de serviço WCF para o equivalente no gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184291"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="f3856-103">Migrar uma solução WCF para o gRPC</span><span class="sxs-lookup"><span data-stu-id="f3856-103">Migrate a WCF solution to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f3856-104">Este capítulo examinará como trabalhar com os projetos ASP.NET Core 3,0 gRPC e demonstrará a migração de diferentes tipos de serviço WCF para o equivalente gRPC:</span><span class="sxs-lookup"><span data-stu-id="f3856-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="f3856-105">Crie um projeto ASP.NET Core gRPC 3,0.</span><span class="sxs-lookup"><span data-stu-id="f3856-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="f3856-106">Operações simples de solicitação-resposta para RPC unário gRPC.</span><span class="sxs-lookup"><span data-stu-id="f3856-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="f3856-107">Operações unidirecionais para RPC de streaming de cliente gRPC.</span><span class="sxs-lookup"><span data-stu-id="f3856-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="f3856-108">Serviços Full duplex para RPC de streaming bidirecional gRPC.</span><span class="sxs-lookup"><span data-stu-id="f3856-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="f3856-109">Também há uma comparação entre usar serviços de streaming versus campos repetidos para retornar conjuntos de dados e o uso de bibliotecas de cliente no final do capítulo.</span><span class="sxs-lookup"><span data-stu-id="f3856-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="f3856-110">O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de negociação de estoque, usando a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada *Autofac* para injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="f3856-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="f3856-111">Ele inclui três serviços, um para cada tipo de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="f3856-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="f3856-112">Os serviços serão discutidos mais detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="f3856-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="f3856-113">As soluções podem ser baixadas de [RendleLabs/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github.</span><span class="sxs-lookup"><span data-stu-id="f3856-113">The solutions can be downloaded from [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="f3856-114">Os serviços usam dados falsos para minimizar dependências externas.</span><span class="sxs-lookup"><span data-stu-id="f3856-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="f3856-115">Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.</span><span class="sxs-lookup"><span data-stu-id="f3856-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3856-116">[Anterior](ws-protocols.md)
>[Próximo](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="f3856-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
