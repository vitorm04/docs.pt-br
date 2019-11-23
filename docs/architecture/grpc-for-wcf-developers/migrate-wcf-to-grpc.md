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
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrar uma solução WCF para o gRPC

Este capítulo examinará como trabalhar com os projetos ASP.NET Core 3,0 gRPC e demonstrará a migração de diferentes tipos de serviço WCF para o equivalente gRPC:

- Crie um projeto ASP.NET Core gRPC 3,0.
- Operações simples de solicitação-resposta para RPC unário gRPC.
- Operações unidirecionais para RPC de streaming de cliente gRPC.
- Serviços Full duplex para RPC de streaming bidirecional gRPC.

Também há uma comparação entre usar serviços de streaming versus campos repetidos para retornar conjuntos de dados e o uso de bibliotecas de cliente no final do capítulo.

O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de negociação de estoque, usando a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada *Autofac* para injeção de dependência. Ele inclui três serviços, um para cada tipo de serviço do WCF. Os serviços serão discutidos mais detalhadamente nas seções a seguir. As soluções podem ser baixadas de [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github. Os serviços usam dados falsos para minimizar dependências externas.

Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.

>[!div class="step-by-step"]
>[Anterior](ws-protocols.md)
>[Próximo](create-project.md)
