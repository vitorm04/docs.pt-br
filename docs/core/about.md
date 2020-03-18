---
title: Sobre o .NET Core
description: Saiba mais sobre o .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147354"
---
# <a name="about-net-core"></a>Sobre o .NET Core

O .NET Core tem as seguintes características:

- **Multiplataforma:** É executado em [sistemas operacionais](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS e Linux.
- **Consistente entre arquiteturas:** executa o código com o mesmo comportamento em várias arquiteturas, incluindo x64, x86 e ARM.
- **Ferramentas de Linha de Comando:** inclui ferramentas de linha de comando fáceis de usar, para desenvolvimento local e em cenários de integração contínua.
- **Implantação flexível:** Pode ser incluído em seu aplicativo ou instalado lado a lado (instalações em todo o usuário ou em todo o sistema). Pode ser usado com os [contêineres do Docker](docker/introduction.md).
- **Compatível:** .NET Core é compatível com .NET Framework, Xamarin e Mono, via [.NET Standard](../standard/net-standard.md).
- **Código-fonte aberto:** a plataforma do .NET Core é um software livre que usa licenças do MIT e Apache 2. O .NET Core é um projeto do [.NET Foundation](https://dotnetfoundation.org/).
- **Suporte da Microsoft:** a Microsoft dá suporte ao .NET Core por meio do [Suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Languages

As linguagens C#, Visual Basic e F# podem ser usadas para escrever aplicativos e bibliotecas para o .NET Core. Esses idiomas podem ser usados no seu editor de texto favorito ou no Ambiente de Desenvolvimento Integrado (IDE), incluindo:

- [Estúdio Visual](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Código visual do estúdio](https://code.visualstudio.com/download)
- Sublime Text
- Vim

Essa integração é proporcionada, em parte, pelos colaboradores dos projetos [OmniSharp](https://www.omnisharp.net/) e [Ionide.](http://ionide.io)

## <a name="apis"></a>APIs

O .NET Core expõe APIs para vários cenários, incluindo:

- Tipos primitivos, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>como e .
- Coleções, como <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Tipos de utilitário, como <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Tipos de dados, como <xref:System.Data.DataSet?displayProperty=nameWithType> e [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Tipos de alto desempenho, como <xref:System.Numerics.Vector?displayProperty=nameWithType> e [Pipelines](../standard/io/pipelines.md).

O .NET Core oferece compatibilidade com as APIs do .NET Framework e do Mono por meio da implementação da especificação [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Estruturas

Várias estruturas já foram criadas com base no .NET Core:

- [ASP.NET Core](/aspnet/core/)
- [Plataforma Universal do Windows (UWP) do Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composição

O .NET Core é composto pelas seguintes partes:

- O [tempo de execução do .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), que fornece um sistema de tipo, carregamento de montagem, um coletor de lixo, interop nativo e outros serviços básicos. [As bibliotecas de framework do .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) fornecem tipos de dados primitivos, tipos de composição de aplicativos e utilitários fundamentais.
- O [ASP.NET O tempo de execução do Core](https://github.com/dotnet/aspnetcore), que fornece uma estrutura para a construção de aplicativos modernos baseados em internet, como aplicativos web, aplicativos de IoT e backends móveis.
- O [.NET Core SDK](https://github.com/dotnet/sdk) e os compiladores de idiomas[(Roslyn](https://github.com/dotnet/roslyn) e [F#)](https://github.com/microsoft/visualfsharp)que permitem a experiência do desenvolvedor .NET Core.
- O [comando dotnet](./tools/dotnet.md), que é usado para lançar aplicativos .NET Core e comandos CLI. Ele seleciona o tempo de execução e hospeda o tempo de execução, fornece uma política de carregamento de montagem e lança aplicativos e ferramentas.

Esses componentes são distribuídos das seguintes maneiras:

- [runtime do .NET Core](https://dotnet.microsoft.com/download) – inclui as bibliotecas de runtime e de estruturas do .NET Core.
- [runtime do ASP.NET Core](https://dotnet.microsoft.com/download) – inclui bibliotecas de runtime e de estruturas do ASP.NET Core e do .NET Core.
- [O .NET Core SDK](https://dotnet.microsoft.com/download) inclui o .NET Core CLI, ASP.NET Core runtime e o .NET Core runtime and framework.

### <a name="open-source"></a>Código-fonte aberto

O [.NET Core](https://github.com/dotnet/core) é um software livre ([licença MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) que foi concedido ao [.NET Foundation](https://dotnetfoundation.org) pela Microsoft em 2014. É agora um dos projetos mais ativos da Fundação .NET. Pode ser usado por indivíduos e empresas, inclusive para fins pessoais, acadêmicos ou comerciais. Várias empresas usam o .NET Core como parte de aplicativos, ferramentas, novas plataformas e serviços de hospedagem. Algumas dessas empresas fazer contribuições significativas para o .NET Core no GitHub e fornecem diretrizes sobre a direção de produto como parte do [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Projetado para adaptabilidade

.NET Core foi construído como um produto similar, mas único em comparação com outros produtos .NET. Ele foi projetado para permitir ampla adaptabilidade a novas plataformas e cargas de trabalho e tem várias portas de SO e CPU disponíveis (e pode ser portada para muitas mais).

O produto é dividido em várias partes que podem se adaptar a novas plataformas em momentos diferentes. O runtime e as bibliotecas fundamentais específicas de plataformas devem ser transportados como uma unidade. Bibliotecas independentes de plataforma devem funcionar no estado em que se encontra em todas as plataformas como-está em todas as plataformas desde a construção. Há um viés de projeto para reduzir implementações específicas da plataforma para aumentar a eficiência do desenvolvedor, preferindo o código C# neutro da plataforma sempre que um algoritmo ou API pode ser implementado integralmente ou parcialmente dessa forma.

As pessoas geralmente perguntam como o .NET Core é implementado para dar suporte a vários sistemas operacionais. Eles normalmente perguntam se há implementações separadas ou se a [compilação condicional](https://en.wikipedia.org/wiki/Conditional_compilation) é usada. A resposta é ambas, com uma forte tendência para a compilação condicional.

Você pode ver no gráfico a seguir que a grande maioria das [bibliotecas .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) é um código neutro de plataforma que é compartilhado em todas as plataformas. O código neutro com relação à plataforma pode ser implementado como um único assembly portátil usado em todas as plataformas.

![CoreFX: Linhas de código por plataforma](../images/corefx-platforms-loc.png)

Implementações de Windows e Unix são semelhantes em tamanho. O Windows tem uma implementação maior, já que as bibliotecas do .NET Core implementam alguns recursos somente do Windows, como [o Microsoft.Win32.Registry,](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) mas ainda não implementa muitos conceitos somente do Unix. Você também verá que a maioria das implementações do Linux e macOS são compartilhadas através de uma implementação do Unix, enquanto as implementações específicas para Linux e macOS são aproximadamente semelhantes em tamanho.

Há uma mistura de bibliotecas específicas para plataformas e plataformas neutras no .NET Core. Você pode observar esse padrão em alguns exemplos:

- O [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) é específico de plataforma. Ele é baseado nos subsistemas do sistema operacional, como o gerenciador de memória e o agendador de thread.
- O [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) e o [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) são específicos da plataforma, pois as APIs de armazenamento e de criptografia são diferentes em cada sistema operacional.
- O [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) e [System.LINQ](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) são neutros de plataforma, considerando que eles podem criar e operar em estruturas de dados.

## <a name="comparisons-to-other-net-implementations"></a>Comparações com outras implementações do .NET

Provavelmente é mais fácil entender o tamanho e a forma do .NET Core, comparando-o com as implementações .NET existentes.

### <a name="comparison-with-net-framework"></a>Comparação com o .NET Framework

O .NET foi anunciado pela primeira vez pela Microsoft em 2000 e continuou evoluindo a partir daí. O .NET Framework foi a principal implementação do .NET produzida pela Microsoft durante esse período de quase duas décadas.

Principais diferenças entre o .NET Core e o .NET Framework:

- **Os modelos de** aplicativos -- .NET Core não suporta todos os modelos de aplicativos do .NET Framework. Ele não dá suporte especificamente a Web Forms do ASP.NET e a ASP.NET MVC, mas dá suporte ao ASP.NET Core MVC. E começando com .NET Core 3.0, o .NET Core também suporta Formulários WPF e Windows somente no Windows.
- **APIs** – o .NET Core contém um grande subconjunto da biblioteca de classes base .NET Framework, com aspectos diferentes (os nomes de assembly são diferentes, os membros expostos nos tipos são diferentes em casos principais). Em alguns casos, essas diferenças exigem alterações na fonte de porta para .NET Core. Para obter mais informações, consulte [O Analisador de Portabilidade .NET](../standard/analyzers/portability-analyzer.md). O .NET Core implementa a especificação de API [.NET Standard](../standard/net-standard.md).
- **Subsistemas** – O.NET Core implementa um subconjunto dos subsistemas no .NET Framework com o objetivo de proporcionar uma implementação e um modelo de programação mais simples. Por exemplo, o CAS (Code Access Security, segurança de acesso ao código) não é suportado, enquanto a reflexão é suportada.
- **Plataformas** – O .NET Framework dá suporte a Windows e Windows Server, enquanto o .NET Core também dá suporte a macOS e Linux.
- **Software Livre** – O.NET Core é um software livre, enquanto um [subconjunto somente leitura do .NET Framework](https://github.com/microsoft/referencesource) é um software livre.

Embora o .NET Core seja único e tenha diferenças significativas em relação ao .NET Framework e outras implementações .NET, é simples compartilhar código entre essas implementações, usando técnicas de compartilhamento de origem ou binárias.

Como o .NET Core é compatível com a instalação lado a lado, e seu runtime é completamente independente do .NET Framework, ele pode ser instalado em computadores com o .NET Framework instalado sem problemas.

### <a name="comparison-with-mono"></a>Comparação com Mono

[Mono](https://www.mono-project.com/) é a implementação multiplataforma original do .NET. Começou como uma alternativa [de código aberto](https://github.com/mono/mono) ao .NET Framework e passou para a segmentação de dispositivos móveis à medida que dispositivos iOS e Android se tornaram populares. Ele pode ser considerado um clone de comunidade do .NET Framework. A equipe do projeto Mono se baseou nos padrões abertos [.NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (notavelmente ECMA 335) publicados pela Microsoft para fornecer uma implementação compatível.

Principais diferenças entre o .NET Core e o Mono:

- **Modelos de** aplicativos -- A Mono suporta um subconjunto dos modelos de aplicativos .NET Framework (por exemplo, Windows Forms) e alguns adicionais para desenvolvimento móvel (por exemplo, [Xamarin.iOS)](https://www.xamarin.com/platform)através do produto Xamarin. O .NET Core não suporta Xamarin.
- **APIs** – O Mono dá suporte a um [grande subconjunto](http://docs.go-mono.com/?link=root%3a%2fclasslib) das APIs do .NET Framework, usando os mesmos nomes de assembly e fatoração.
- **Plataformas** – O Mono dá suporte a várias plataformas e CPUs.
- **Software Livre** – O Mono e o .NET Core usam a licença MIT e são projetos do .NET Foundation.
- **Foco** – o principal foco do Mono nos últimos anos são as plataformas móveis, enquanto o .NET Core se concentra em cargas de trabalho de nuvem e da área de trabalho.

## <a name="the-future"></a>O futuro

Foi anunciado que o .NET 5 será o próximo lançamento do .NET Core e representa uma unificação da plataforma. O projeto tem como objetivo melhorar o .NET de algumas maneiras-chave:

- Produza um único tempo de execução .NET e uma estrutura que pode ser usada em todos os lugares e que tenha comportamentos uniformes de tempo de execução e experiências de desenvolvedor.
- Expanda os recursos do .NET, tirando o melhor do .NET Core, .NET Framework, Xamarin e Mono.
- Construa esse produto a partir de uma única base de código que os desenvolvedores (Microsoft e a comunidade) podem trabalhar e expandir juntos e que melhora todos os cenários.

Para obter mais detalhes sobre o que está sendo planejado para .NET 5, consulte [Introdução .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
