---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632106"
---
> [!NOTE]
> Começando com o .NET Core 2.0 SDK, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) você não precisa ser executado porque é executado implicitamente `dotnet new` `dotnet build` por `dotnet run`todos os comandos que requerem uma restauração para ocorrer, tais como , e .
> Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.
