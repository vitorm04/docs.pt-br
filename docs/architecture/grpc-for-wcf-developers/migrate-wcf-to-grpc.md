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
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrar uma solução WCF para o gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Este capítulo examinará como trabalhar com os projetos ASP.NET Core 3,0 gRPC e demonstrará a migração de diferentes tipos de serviço WCF para o equivalente gRPC:

- Crie um projeto ASP.NET Core gRPC 3,0.
- Operações simples de solicitação-resposta para RPC unário gRPC.
- Operações unidirecionais para RPC de streaming de cliente gRPC.
- Serviços Full duplex para RPC de streaming bidirecional gRPC.

Também há uma comparação entre usar serviços de streaming versus campos repetidos para retornar conjuntos de dados e o uso de bibliotecas de cliente no final do capítulo.

O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de negociação de estoque, usando a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada *Autofac* para injeção de dependência. Ele inclui três serviços, um para cada tipo de serviço do WCF. Os serviços serão discutidos mais detalhadamente nas seções a seguir. As soluções podem ser baixadas de [RendleLabs/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github. Os serviços usam dados falsos para minimizar dependências externas.

Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.

>[!div class="step-by-step"]
>[Anterior](ws-protocols.md)
>[Próximo](create-project.md)
