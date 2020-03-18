---
ms.openlocfilehash: 975edd1bda507b46da353db788d9730560f9b573
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632106"
---
> [!NOTE]
> <span data-ttu-id="41e3e-101">Começando com o .NET Core 2.0 SDK, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) você não precisa ser executado porque é executado implicitamente `dotnet new` `dotnet build` por `dotnet run`todos os comandos que requerem uma restauração para ocorrer, tais como , e .</span><span class="sxs-lookup"><span data-stu-id="41e3e-101">Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`.</span></span>
> <span data-ttu-id="41e3e-102">Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="41e3e-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
