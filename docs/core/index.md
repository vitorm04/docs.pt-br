---
title: Guia do .NET Core
description: O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 448edabf624f04311695e8b8c224f653b9939966
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199455"
---
# <a name="net-core-guide"></a>Guia do .NET Core

O [.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core). É uma plataforma cruzada (compatível com Windows, macOS e Linux) que pode ser usada no desenvolvimento de dispositivos, na nuvem e em aplicativos de IoT.

Consulte [Sobre o .NET Core](about.md) para saber mais sobre o .NET Core, incluindo suas características, idiomas compatíveis, estruturas e APIs essenciais.

Consulte os [Tutoriais do .NET Core](tutorials/index.md) para aprender a criar um aplicativo .NET Core simples. Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento. Consulte o tutorial online [Números em C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) caso deseje experimentar o .NET Core no seu navegador.

## <a name="download-net-core-21"></a>Faça o download do .NET Core 2.1

Faça o download do [SDK do .NET Core 2.1](https://www.microsoft.com/net/download) para experimentar o .NET Core em seu computador Windows, macOS ou Linux. Visite [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) se preferir usar contêineres do Docker.

Todas as versões do .NET Core estão disponíveis em [Downloads do .NET Core](https://www.microsoft.com/net/download/archives) se você estiver procurando por outra versão.

## <a name="net-core-21"></a>.NET Core 2.1

O [.NET Core 2.1](whats-new/dotnet-core-2-1.md) é a versão mais recente. Os novos recursos incluem: ferramentas globais, APIs de alto desempenho (como <xref:System.Span%601?displayProperty=nameWithType>), compilação JIT em camadas, [build](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) e [melhorias de desempenho no tempo de execução](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), e suporte para Alpine e ARM32.

## <a name="create-your-first-application"></a>Criar seu primeiro aplicativo

Após instalar o SDK do .NET Core, abra um prompt de comando. Digite os seguintes comandos `dotnet` para criar e executar um aplicativo C#.

```console
dotnet new console
dotnet run
```

Você deverá ver a seguinte saída:

```console
Hello World!
```

## <a name="support"></a>Suporte

A [Microsoft disponibiliza](https://www.microsoft.com/net/support/policy) o .NET Core para Windows, no macOS e no Linux. Ele é atualizado para segurança e qualidade várias vezes ao ano, normalmente mensalmente.

As distribuições de binários do .NET Core são criadas e testadas em servidores mantidos pela Microsoft no Azure e têm suporte como qualquer produto da Microsoft.

A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL). A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.
