---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102730"
---
<span data-ttu-id="328b2-101">Você não precisa correr [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) porque é executado implicitamente por todos os comandos `dotnet new`que `dotnet build` `dotnet run`requerem `dotnet test` `dotnet publish`uma `dotnet pack`restauração para ocorrer, tais como, , , , e .</span><span class="sxs-lookup"><span data-stu-id="328b2-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="328b2-102">Para desativar a restauração `--no-restore` implícita, use a opção.</span><span class="sxs-lookup"><span data-stu-id="328b2-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="328b2-103">O `dotnet restore` comando ainda é útil em certos cenários onde a restauração explícita faz sentido, como [compilações de integração contínua em Serviços Azure DevOps](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de construção que precisam controlar explicitamente quando a restauração ocorre.</span><span class="sxs-lookup"><span data-stu-id="328b2-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="328b2-104">Para obter informações sobre como gerenciar feeds NuGet, consulte a [ `dotnet restore` documentação](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="328b2-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
