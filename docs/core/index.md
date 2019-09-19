---
title: Guia do .NET Core
description: O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: a6112851a3d9b46f02c26313e6537170786df10b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117076"
---
# <a name="net-core-guide"></a>Guia do .NET Core

O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core). É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.

Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.

Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples. Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento. Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.

## <a name="download-net-core-22"></a>Baixe o .NET Core 2.2

Baixe o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download) para experimentar o .NET Core em seu computador Windows, macOS ou Linux. Acesse [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) se preferir usar contêineres do Docker.

Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core) se você estiver procurando por outra versão.

## <a name="net-core-22"></a>.NET Core 2.2

O [.NET Core 2.2](whats-new/dotnet-core-2-2.md) é a versão mais recente. Os novos recursos incluem: implantações dependentes de estrutura, ganchos de inicialização, autenticação do AAD com o Azure SQL e suporte para Windows para ARM32.

## <a name="create-your-first-application"></a>Criar seu primeiro aplicativo

Após instalar o SDK do .NET Core, abra um prompt de comando. Digite os seguintes comandos `dotnet` para criar e executar um aplicativo C#.

```dotnetcli
dotnet new console
dotnet run
```

Você deverá ver a seguinte saída:

```output
Hello World!
```

## <a name="support"></a>Suporte

A [Microsoft disponibiliza](https://dotnet.microsoft.com/platform/support/policy) o .NET Core para Windows, no macOS e no Linux. Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.

As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.

A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL). A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.
