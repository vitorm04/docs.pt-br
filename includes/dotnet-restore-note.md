---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102730"
---
Você não precisa correr [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) porque é executado implicitamente por todos os comandos `dotnet new`que `dotnet build` `dotnet run`requerem `dotnet test` `dotnet publish`uma `dotnet pack`restauração para ocorrer, tais como, , , , e . Para desativar a restauração `--no-restore` implícita, use a opção.

O `dotnet restore` comando ainda é útil em certos cenários onde a restauração explícita faz sentido, como [compilações de integração contínua em Serviços Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de construção que precisam controlar explicitamente quando a restauração ocorre.

Para obter informações sobre como gerenciar feeds NuGet, consulte a [ `dotnet restore` documentação](../docs/core/tools/dotnet-restore.md).
