---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179978"
---
> [!NOTE]
> <span data-ttu-id="677e7-101">Começando com o .NET Core 2.0, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) você não precisa ser executado porque é executado implicitamente `dotnet build` por `dotnet run`todos os comandos que requerem uma restauração para ocorrer, como e .</span><span class="sxs-lookup"><span data-stu-id="677e7-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="677e7-102">Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="677e7-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="677e7-103">Este comando também é compatível com as opções `dotnet restore` quando passado no formato longo (por exemplo, `--source`).</span><span class="sxs-lookup"><span data-stu-id="677e7-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="677e7-104">Opções de formato curto, como `-s`, não são compatíveis.</span><span class="sxs-lookup"><span data-stu-id="677e7-104">Short form options, such as `-s`, are not supported.</span></span>
