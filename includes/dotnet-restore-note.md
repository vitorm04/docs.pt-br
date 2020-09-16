---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537724"
---
<span data-ttu-id="83457-101">Você não precisa executar [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) o porque ele é executado implicitamente por todos os comandos que exigem a ocorrência de uma restauração, como,,,, `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` e `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="83457-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="83457-102">Para desabilitar a restauração implícita, use a `--no-restore` opção.</span><span class="sxs-lookup"><span data-stu-id="83457-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="83457-103">O `dotnet restore` comando ainda é útil em determinados cenários em que a restauração explícita faz sentido, como [compilações de integração contínua em Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de compilação que precisam controlar explicitamente quando a restauração ocorre.</span><span class="sxs-lookup"><span data-stu-id="83457-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="83457-104">Para obter informações sobre como gerenciar feeds do NuGet, consulte a [ `dotnet restore` documentação](../docs/core/tools/dotnet-restore.md).</span><span class="sxs-lookup"><span data-stu-id="83457-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
