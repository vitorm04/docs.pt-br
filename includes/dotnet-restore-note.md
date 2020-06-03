---
ms.openlocfilehash: e140b375f4f289df895052aa093f03f381d62488
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102730"
---
<span data-ttu-id="4f1dd-101">Você não precisa executar [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) o porque ele é executado implicitamente por todos os comandos que exigem a ocorrência de uma restauração, como,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` e `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="4f1dd-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="4f1dd-102">Para desabilitar a restauração implícita, use a `--no-restore` opção.</span><span class="sxs-lookup"><span data-stu-id="4f1dd-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="4f1dd-103">O `dotnet restore` comando ainda é útil em determinados cenários em que a restauração explícita faz sentido, como [compilações de integração contínua em Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de compilação que precisam controlar explicitamente quando a restauração ocorre.</span><span class="sxs-lookup"><span data-stu-id="4f1dd-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="4f1dd-104">Para obter informações sobre como gerenciar feeds do NuGet, consulte a [ `dotnet restore` documentação](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="4f1dd-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
