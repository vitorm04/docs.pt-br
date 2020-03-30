---
title: Visão geral do .NET Core
description: Aprenda sobre as características e a composição do .NET Core e compare-o com outras implementações .NET.
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391163"
---
# <a name="net-core-overview"></a>Visão geral do .NET Core

O .NET Core tem as seguintes características:

- **Plataforma cruzada:** É executado em [sistemas operacionais](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS e Linux.
- **Código aberto:** A estrutura .NET Core é [de código aberto,](https://github.com/dotnet/core)usando licenças MIT e Apache 2. O .NET Core é um projeto do [.NET Foundation](https://dotnetfoundation.org/).
- **Moderno:** Implementa paradigmas modernos como programação assíncrona, padrões sem cópia usando estruturas e governança de recursos para contêineres.
- **Desempenho:**  Oferece [alto desempenho](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) com recursos como [intrínsecas de hardware,](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/) [compilação hierárquica](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)e [Span\<T>](../standard/memory-and-spans/index.md).
- **Consistente entre ambientes:** Execute seu código com o mesmo comportamento em vários sistemas operacionais e arquiteturas, incluindo x64, x86 e ARM.
- **Ferramentas de linha de comando:**  Inclui ferramentas de linha de comando fáceis de usar que podem ser usadas para o desenvolvimento local e para a integração contínua.
- **Implantação flexível:** Você pode incluir o .NET Core em seu aplicativo ou instalá-lo lado a lado (instalações em todo o usuário ou em todo o sistema). Pode ser usado com os [contêineres do Docker](docker/introduction.md).

## <a name="languages"></a>Languages

Os idiomas [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)e [F#](../fsharp/index.yml) podem ser usados para escrever aplicativos e bibliotecas para .NET Core. Esses idiomas podem ser usados no seu editor de texto favorito ou no Ambiente de Desenvolvimento Integrado (IDE), incluindo:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Código visual do estúdio](https://code.visualstudio.com/download)

A integração dos editores é fornecida, em parte, pelos colaboradores dos projetos [OmniSharp](https://www.omnisharp.net/) e [Ionide.](http://ionide.io)

## <a name="apis"></a>APIs

.NET Core expõe frameworks para a construção de qualquer tipo de aplicativo:

* Aplicativos em nuvem com [ASP.NET Core](/aspnet/core/)
* Aplicativos móveis com [Xamarin](/xamarin)
* Aplicativos IoT com [System.Device.GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Aplicativos cliente do Windows com [Formulários WPF](../desktop-wpf/overview/index.md) e Windows
* ML.NET de aprendizagem [de máquina](../machine-learning/index.yml)

Muitas APIs estão incluídas que satisfazem as necessidades comuns:

- Tipos primitivos, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>como e .
- Coleções, como <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Tipos de utilitário, como <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Tipos de dados, <xref:System.Data.DataSet?displayProperty=nameWithType> <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>como , e .
- Tipos de alto desempenho, como <xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Numerics.Vector?displayProperty=nameWithType>e [Pipelines](../standard/io/pipelines.md).

O .NET Core oferece compatibilidade com as APIs do .NET Framework e do Mono por meio da implementação da especificação [.NET Standard](../standard/net-standard.md).

## <a name="composition"></a>Composição

O .NET Core é composto pelas seguintes partes:

- O [tempo de execução do .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), que fornece um sistema de tipo, carregamento de montagem, um coletor de lixo, interop nativo e outros serviços básicos. [As bibliotecas de framework do .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) fornecem tipos de dados primitivos, tipos de composição de aplicativos e utilitários fundamentais.
- O [ASP.NET O tempo de execução do Core](https://github.com/dotnet/aspnetcore), que fornece uma estrutura para a construção de aplicativos modernos, baseados em nuvem e conectados à internet, como aplicativos web, aplicativos IoT e backends móveis.
- O [.NET Core SDK](https://github.com/dotnet/sdk) e os compiladores de idiomas[(Roslyn](https://github.com/dotnet/roslyn) e [F#)](https://github.com/microsoft/visualfsharp)que permitem a experiência do desenvolvedor .NET Core.
- O [comando dotnet](./tools/dotnet.md), que é usado para lançar aplicativos .NET Core e comandos CLI. Ele seleciona e hospeda o tempo de execução, fornece uma política de carregamento de montagem e lança aplicativos e ferramentas.

### <a name="open-source"></a>Código-fonte aberto

[.NET Core](about.md) é uma plataforma de desenvolvimento [de código aberto](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)e de uso geral. Você pode criar aplicativos .NET Core para windows, macOS e Linux para processadores x64, x86, ARM32 e ARM64. Estruturas e APIs são fornecidas para [nuvem,](/aspnet/core/) [IoT,](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) [ui cliente](../desktop-wpf/overview/index.md)e [machine learning](../machine-learning/index.yml).

## <a name="support"></a>Suporte

O .NET Core é [suportado pela Microsoft](https://dotnet.microsoft.com/platform/support/policy) no Windows, macOS e Linux. É atualizado para segurança e qualidade regularmente (a segunda terça-feira de cada mês).

As distribuições binárias do .NET Core da Microsoft são construídas e testadas em servidores mantidos pela Microsoft no Azure e seguem as práticas de engenharia e segurança da Microsoft.

A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL). A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.

[O Tizen suporta o .NET Core](https://developer.tizen.org/development/training/.net-application) nas plataformas Tizen.
