---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72179978"
---
> [!NOTE]
> Começando com o .NET Core 2.0, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) você não precisa ser executado porque é executado implicitamente `dotnet build` por `dotnet run`todos os comandos que requerem uma restauração para ocorrer, como e . Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.
>
> Este comando também é compatível com as opções `dotnet restore` quando passado no formato longo (por exemplo, `--source`). Opções de formato curto, como `-s`, não são compatíveis.
