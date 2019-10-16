---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179978"
---
> [!NOTE]
> A partir do .NET Core 2,0, você não precisa executar [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) porque ele é executado implicitamente por todos os comandos que exigem a ocorrência de uma restauração, como `dotnet build` e `dotnet run`. Ainda é um comando válido em determinados cenários em que realizar uma restauração explícita faz sentido, como [builds de integração contínua no Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) ou em sistemas de build que precisam controlar explicitamente o horário em que a restauração ocorrerá.
>
> Este comando também é compatível com as opções `dotnet restore` quando passado no formato longo (por exemplo, `--source`). Opções de formato curto, como `-s`, não são compatíveis.
