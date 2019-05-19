---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632106"
---
> [!NOTE]
> Começando com o SDK do .NET Core 2.0, não é necessário executar [`dotnet restore`](~/docs/core/tools/dotnet-restore.md), pois ele é executado implicitamente por todos os comandos que exigem uma restauração, como `dotnet new`, `dotnet build` e `dotnet run`.
> Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.
