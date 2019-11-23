---
title: Migrar uma solução WCF para o gRPC-gRPC para desenvolvedores do WCF
description: Como migrar diferentes tipos de serviço WCF para o equivalente no gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 33823d20e1593323a03da12981c5a4534c4d491a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971768"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="49306-103">Migrar uma solução WCF para o gRPC</span><span class="sxs-lookup"><span data-stu-id="49306-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="49306-104">Este capítulo examinará como trabalhar com os projetos ASP.NET Core 3,0 gRPC e demonstrará a migração de diferentes tipos de serviço WCF para o equivalente gRPC:</span><span class="sxs-lookup"><span data-stu-id="49306-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="49306-105">Crie um projeto ASP.NET Core gRPC 3,0.</span><span class="sxs-lookup"><span data-stu-id="49306-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="49306-106">Operações simples de solicitação-resposta para RPC unário gRPC.</span><span class="sxs-lookup"><span data-stu-id="49306-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="49306-107">Operações unidirecionais para RPC de streaming de cliente gRPC.</span><span class="sxs-lookup"><span data-stu-id="49306-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="49306-108">Serviços Full duplex para RPC de streaming bidirecional gRPC.</span><span class="sxs-lookup"><span data-stu-id="49306-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="49306-109">Também há uma comparação entre usar serviços de streaming versus campos repetidos para retornar conjuntos de dados e o uso de bibliotecas de cliente no final do capítulo.</span><span class="sxs-lookup"><span data-stu-id="49306-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="49306-110">O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de negociação de estoque, usando a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada *Autofac* para injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="49306-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="49306-111">Ele inclui três serviços, um para cada tipo de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="49306-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="49306-112">Os serviços serão discutidos mais detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="49306-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="49306-113">As soluções podem ser baixadas de [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github.</span><span class="sxs-lookup"><span data-stu-id="49306-113">The solutions can be downloaded from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="49306-114">Os serviços usam dados falsos para minimizar dependências externas.</span><span class="sxs-lookup"><span data-stu-id="49306-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="49306-115">Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.</span><span class="sxs-lookup"><span data-stu-id="49306-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49306-116">[Anterior](ws-protocols.md)
>[Próximo](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="49306-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
