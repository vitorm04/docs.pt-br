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
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrar uma solução WCF para o gRPC

Este capítulo descreverá como trabalhar com projetos ASP.NET Core 3,0 gRPC e demonstrar a migração de diferentes tipos de serviços de Windows Communication Foundation (WCF) para o equivalente gRPC:

- Crie um projeto ASP.NET Core gRPC 3,0.
- Operações simples de solicitação-resposta para RPC unário gRPC.
- Operações unidirecionais para RPC de streaming de cliente gRPC.
- Serviços Full duplex para RPC de streaming bidirecional gRPC.

Também há uma comparação entre usar os serviços de streaming versus campos repetidos para retornar conjuntos de valores, e há uma discussão sobre o uso de bibliotecas de cliente no final do capítulo.

O aplicativo WCF de exemplo é um stub mínimo de um conjunto de serviços de comércio de estoque. Ele usa a biblioteca de contêineres IoC (inversão de controle de código aberto) chamada Autofac para injeção de dependência. Ele inclui três serviços, um para cada tipo de serviço do WCF. Os serviços serão discutidos mais detalhadamente nas seções a seguir. Você pode baixar as soluções de [dotnet-Architecture/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) no github. Os serviços usam dados falsos para minimizar dependências externas.

Os exemplos incluem as implementações do WCF e do gRPC de cada serviço.

>[!div class="step-by-step"]
>[Anterior](ws-protocols.md)
>[Próximo](create-project.md)
