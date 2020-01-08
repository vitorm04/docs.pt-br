---
title: Guia do .NET Core
description: O .NET Core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos para Windows, Linux e macOS. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 80a3b12972e24c3022ac2aa14406aa60635815a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341361"
---
# <a name="net-core-guide"></a>Guia do .NET Core

O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core). É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.

Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.

Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples. Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento. Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.

## <a name="download-net-core"></a>Baixe o .NET Core

Baixe o [SDK do .NET Core](https://www.microsoft.com/net/download) para experimentar o .NET Core em seu computador com Windows, MacOS ou Linux. E se preferir usar contêineres do Docker, visite o [Hub do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).

Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core) se você estiver procurando por outra versão.

## <a name="net-core-31"></a>.NET Core 3,1

A versão mais recente é o .NET Core 3,1. 3,1 inclui pequenas melhorias no .NET Core 3,0, no entanto, o .NET Core 3,1 é uma [versão com suporte a longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). Para obter mais informações sobre a versão 3,1 do .NET Core, consulte [o que há de novo no .net core 3,1](./whats-new/dotnet-core-3-1.md).

## <a name="create-your-first-application"></a>Criar seu primeiro aplicativo

Após instalar o SDK do .NET Core, abra um prompt de comando. Insira os seguintes comandos de `dotnet` para criar e executar C# um aplicativo:

```dotnetcli
dotnet new console
dotnet run
```

Você deverá ver a seguinte saída:

```output
Hello World!
```

## <a name="support"></a>Suporte do

O .NET Core tem [suporte da Microsoft](https://dotnet.microsoft.com/platform/support/policy), no Windows, no MacOS e no Linux. Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.

As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.

A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL). A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.
