---
title: Visão geral do .NET Core
description: Aprenda sobre as características e a composição do .NET Core e compare-o com outras implementações .NET.
ms.date: 09/17/2019
ms.openlocfilehash: f2f97fe6a5f822266582c443fd916c270cb0cb6a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345195"
---
# <a name="net-core-overview"></a>Visão geral do .NET Core

O .NET Core tem as seguintes características:

- **Multiplataforma:** É executado em [sistemas operacionais](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS e Linux.
- **Consistente entre arquiteturas:** executa o código com o mesmo comportamento em várias arquiteturas, incluindo x64, x86 e ARM.
- **Ferramentas de Linha de Comando:** inclui ferramentas de linha de comando fáceis de usar, para desenvolvimento local e em cenários de integração contínua.
- **Implantação flexível:** Pode ser incluído em seu aplicativo ou instalado lado a lado (instalações em todo o usuário ou em todo o sistema). Pode ser usado com os [contêineres do Docker](docker/introduction.md).
- **Compatível:** .NET Core é compatível com as implementações .NET Framework, Xamarin e Mono via [.NET Standard](../standard/net-standard.md).
- **Código-fonte aberto:** a plataforma do .NET Core é um software livre que usa licenças do MIT e Apache 2. O .NET Core é um projeto do [.NET Foundation](https://dotnetfoundation.org/).
- **Suportado pela Microsoft:** .NET Core é [suportado pela Microsoft](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Languages

As linguagens C#,Visual Basic e F# podem ser usadas para escrever aplicativos e bibliotecas para o .NET Core. Esses idiomas podem ser usados no seu editor de texto favorito ou no Ambiente de Desenvolvimento Integrado (IDE), incluindo:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Código visual do estúdio](https://code.visualstudio.com/download)
- Sublime Text
- Vim

A integração dos editores é fornecida, em parte, pelos colaboradores dos projetos [OmniSharp](https://www.omnisharp.net/) e [Ionide.](http://ionide.io)

## <a name="apis"></a>APIs

Muitas APIs estão incluídas que satisfazem necessidades comuns, tais como:

- Tipos primitivos, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>como e .
- Coleções, como <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Tipos de utilitário, como <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Tipos de dados, como <xref:System.Data.DataSet?displayProperty=nameWithType> e [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Tipos de alto desempenho, como <xref:System.Numerics.Vector?displayProperty=nameWithType> e [Pipelines](../standard/io/pipelines.md).

O .NET Core oferece compatibilidade com as APIs do .NET Framework e do Mono por meio da implementação da especificação [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Estruturas

Várias estruturas foram construídas em cima do .NET Core, incluindo:

- [ASP.NET Core](/aspnet/core/)
- [UWP (Plataforma Universal do Windows)](/windows/uwp/)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composição

O .NET Core é composto pelas seguintes partes:

- O [tempo de execução do .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), que fornece um sistema de tipo, carregamento de montagem, um coletor de lixo, interop nativo e outros serviços básicos. [As bibliotecas de framework do .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) fornecem tipos de dados primitivos, tipos de composição de aplicativos e utilitários fundamentais.
- O [ASP.NET O tempo de execução do Core](https://github.com/dotnet/aspnetcore), que fornece uma estrutura para a construção de aplicativos modernos, baseados em nuvem e conectados à internet, como aplicativos web, aplicativos IoT e backends móveis.
- O [.NET Core SDK](https://github.com/dotnet/sdk) e os compiladores de idiomas[(Roslyn](https://github.com/dotnet/roslyn) e [F#)](https://github.com/microsoft/visualfsharp)que permitem a experiência do desenvolvedor .NET Core.
- O [comando dotnet](./tools/dotnet.md), que é usado para lançar aplicativos .NET Core e comandos CLI. Ele seleciona e hospeda o tempo de execução, fornece uma política de carregamento de montagem e lança aplicativos e ferramentas.

Esses componentes são distribuídos das seguintes maneiras:

- [runtime do .NET Core](https://dotnet.microsoft.com/download) – inclui as bibliotecas de runtime e de estruturas do .NET Core.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) -- inclui os tempos de execução do ASP.NET Core e .NET Core e bibliotecas-estruturas.
- [O .NET Core SDK](https://dotnet.microsoft.com/download) inclui o .NET Core CLI, ASP.NET Core runtime e o .NET Core runtime and framework.

### <a name="open-source"></a>Código-fonte aberto

[.NET Core](https://github.com/dotnet/core) é de código aberto[(licença do MIT)](https://github.com/dotnet/core/blob/master/LICENSE.TXT)e foi contribuído para a [.NET Foundation](https://dotnetfoundation.org) pela Microsoft em 2014. É agora um dos projetos mais ativos da Fundação .NET. Pode ser usado por indivíduos e empresas, inclusive para fins pessoais, acadêmicos ou comerciais. Várias empresas usam o .NET Core como parte de aplicativos, ferramentas, novas plataformas e serviços de hospedagem. Algumas dessas empresas fazer contribuições significativas para o .NET Core no GitHub e fornecem diretrizes sobre a direção de produto como parte do [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Projetado para adaptabilidade

.NET Core foi construído como um produto similar, mas único em comparação com outros produtos .NET. Ele foi projetado para permitir ampla adaptabilidade a novas plataformas e cargas de trabalho, e tem várias portas de SO e CPU disponíveis (e pode ser portada para muitas mais).

O produto é dividido em várias partes que podem se adaptar a novas plataformas em momentos diferentes. O runtime e as bibliotecas fundamentais específicas de plataformas devem ser transportados como uma unidade. Bibliotecas independentes de plataforma devem funcionar no estado em que se encontra em todas as plataformas como-está em todas as plataformas desde a construção. Há um viés de projeto para reduzir implementações específicas da plataforma para aumentar a eficiência do desenvolvedor, preferindo o código C# neutro da plataforma sempre que um algoritmo ou API pode ser implementado integralmente ou parcialmente dessa forma.

As pessoas geralmente perguntam como o .NET Core é implementado para dar suporte a vários sistemas operacionais. Eles normalmente perguntam se há implementações separadas ou se a [compilação condicional](https://en.wikipedia.org/wiki/Conditional_compilation) é usada. A resposta é ambas, com uma forte tendência para a compilação condicional.

Você pode ver no gráfico a seguir que a grande maioria das [bibliotecas .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) são compiladas a partir de código neutro de plataforma que é compartilhado em todas as plataformas. O código neutro da plataforma pode ser implementado como um único conjunto portátil que é usado em todas as plataformas.

![CoreFX: Linhas de código por plataforma](../images/corefx-platforms-loc.png)

As implementações do Windows e do Unix são semelhantes em tamanho. A implementação do Windows contém alguns recursos somente do Windows, como [o Microsoft.Win32.Registry,](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry)mas ainda não implementa muitos conceitos somente do Unix. Grande parte das implementações de Linux e macOS é compartilhada através de uma implementação do Unix. As implementações específicas do Linux e do macOS são semelhantes em tamanho.

Há uma mistura de bibliotecas específicas para plataformas e plataformas neutras no .NET Core. Você pode observar esse padrão em alguns exemplos:

- O [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) é específico de plataforma. Ele é baseado nos subsistemas do sistema operacional, como o gerenciador de memória e o agendador de thread.
- O [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) e o [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) são específicos da plataforma, pois as APIs de armazenamento e de criptografia são diferentes em cada sistema operacional.
- O [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) e [System.LINQ](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) são neutros de plataforma, considerando que eles podem criar e operar em estruturas de dados.

## <a name="comparisons-to-other-net-implementations"></a>Comparações com outras implementações do .NET

Para entender o tamanho e a forma do .NET Core, as seções a seguir comparam-na com as implementações .NET existentes.

### <a name="net-core-vs-net-framework"></a>.NET Core vs. .NET Framework

.NET foi anunciado pela Microsoft pela primeira vez em 2000 e evoluiu a partir daí. O .NET Framework foi a principal implementação .NET produzida pela Microsoft durante esse período de quase duas décadas.

As principais diferenças entre o .NET Core e o .NET Framework são:

- **Os modelos de** aplicativos -- .NET Core não suporta todos os modelos de aplicativos do .NET Framework. Ele não dá suporte especificamente a Web Forms do ASP.NET e a ASP.NET MVC, mas dá suporte ao ASP.NET Core MVC. E começando com .NET Core 3.0, o .NET Core também suporta Formulários WPF e Windows somente no Windows.
- **APIs** – o .NET Core contém um grande subconjunto da biblioteca de classes base .NET Framework, com aspectos diferentes (os nomes de assembly são diferentes, os membros expostos nos tipos são diferentes em casos principais). Em alguns casos, essas diferenças exigem alterações na fonte de porta para .NET Core. Para obter mais informações, consulte [O Analisador de Portabilidade .NET](../standard/analyzers/portability-analyzer.md). O .NET Core implementa a especificação de API [.NET Standard](../standard/net-standard.md).
- **Os subsistemas** -- .NET Core implementam um subconjunto dos subsistemas no Framework .NET, com o objetivo de um modelo de implementação e programação mais simples. Por exemplo, o CAS (Code Access Security, segurança de acesso ao código) não é suportado, enquanto a reflexão é suportada.
- **Plataformas** -- .NET Framework suporta Windows e Windows Server, enquanto o .NET Core também suporta macOS e Linux.
- **O -- .NET** Core de código aberto é de código aberto, enquanto um [subconjunto somente leitura do .NET Framework](https://github.com/microsoft/referencesource) é de código aberto.

Embora o .NET Core seja único e tenha diferenças significativas em relação ao .NET Framework e outras implementações .NET, é simples compartilhar código entre essas implementações, usando técnicas de compartilhamento de origem ou binárias.

Como o .NET Core suporta a instalação lado a lado e seu tempo de execução é completamente independente do .NET Framework, ele pode ser instalado em máquinas que tenham o .NET Framework instalado sem problemas.

### <a name="net-core-vs-mono"></a>.NET Core vs. Mono

[Mono](https://www.mono-project.com/) é a implementação multiplataforma original do .NET. Começou como uma alternativa [de código aberto](https://github.com/mono/mono) ao .NET Framework e passou para a segmentação de dispositivos móveis à medida que dispositivos iOS e Android se tornaram populares. Ele pode ser considerado como um clone da comunidade do .NET Framework. Para fornecer uma implementação compatível, a equipe do projeto Mono contou com os padrões abertos [.NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (notavelmente ECMA 335) publicados pela Microsoft.

As principais diferenças entre .NET Core e Mono são:

- **Modelos de** aplicativos -- A Mono suporta um subconjunto dos modelos de aplicativos .NET Framework (por exemplo, Windows Forms) e alguns adicionais para desenvolvimento móvel (por exemplo, [Xamarin.iOS)](https://www.xamarin.com/platform)através do produto Xamarin. O .NET Core não suporta Xamarin.
- **APIs** – O Mono dá suporte a um [grande subconjunto](http://docs.go-mono.com/?link=root%3a%2fclasslib) das APIs do .NET Framework, usando os mesmos nomes de assembly e fatoração.
- **Plataformas** – O Mono dá suporte a várias plataformas e CPUs.
- **Software Livre** – O Mono e o .NET Core usam a licença MIT e são projetos do .NET Foundation.
- **Foco** – o principal foco do Mono nos últimos anos são as plataformas móveis, enquanto o .NET Core se concentra em cargas de trabalho de nuvem e da área de trabalho.

## <a name="support"></a>Suporte

O .NET Core é [suportado pela Microsoft](https://dotnet.microsoft.com/platform/support/policy) no Windows, macOS e Linux. É atualizado para segurança e qualidade regularmente (segunda terça-feira de cada mês).

As distribuições binárias do .NET Core da Microsoft são construídas e testadas em servidores mantidos pela Microsoft no Azure e seguem as práticas de engenharia e segurança da Microsoft.

A [Red Hat oferece suporte ao .NET Core](http://redhatloves.net/) no Red Hat Enterprise Linux (RHEL). A Red Hat compila o .NET Core da origem e o disponibiliza nas [Coleções de Software do Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat e Microsoft colaboram para garantir que o .NET Core funcione bem no RHEL.

[O Tizen suporta o .NET Core](https://developer.tizen.org/development/training/.net-application) nas plataformas Tizen.
