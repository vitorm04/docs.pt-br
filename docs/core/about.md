---
title: Sobre o .NET Core
description: Saiba mais sobre o .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 51e4f3784db58e23ab4293c2d9f4e52e0d6617b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093436"
---
# <a name="about-net-core"></a>Sobre o .NET Core

O .NET Core tem as seguintes características:

- **Plataforma cruzada:** É executado em [sistemas operacionais](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS e Linux.
- **Consistente entre arquiteturas:** executa o código com o mesmo comportamento em várias arquiteturas, incluindo x64, x86 e ARM.
- **Ferramentas de Linha de Comando:** inclui ferramentas de linha de comando fáceis de usar, para desenvolvimento local e em cenários de integração contínua.
- **Implantação flexível:** Pode ser incluído em seu aplicativo ou instalado lado a lado (instalações de todo o usuário ou do sistema). Pode ser usado com os [contêineres do Docker](docker/index.md).
- **Compatível:** o .NET Core é compatível com .NET Framework, Xamarin e mono, via [.net Standard](../standard/net-standard.md).
- **Código-fonte aberto:** a plataforma do .NET Core é um software livre que usa licenças do MIT e Apache 2. O .NET Core é um projeto do [.NET Foundation](https://dotnetfoundation.org/).
- **Suporte da Microsoft:** a Microsoft dá suporte ao .NET Core por meio do [Suporte do .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Linguagens

As linguagens C#, Visual Basic e F# podem ser usadas para escrever aplicativos e bibliotecas para o .NET Core. Essas linguagens podem ser usadas em seu editor de texto favorito ou IDE (ambiente de desenvolvimento integrado), incluindo:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- Texto sublime
- Vim
 
Essa integração é fornecida, em parte, pelos colaboradores dos projetos [OmniSharp](https://www.omnisharp.net/) e [Ionide](http://ionide.io) .

## <a name="apis"></a>APIs

O .NET Core expõe APIs para vários cenários, incluindo:

- Tipos primitivos, como [bool](../csharp/language-reference/keywords/bool.md) e [int](../csharp/language-reference/builtin-types/integral-numeric-types.md).
- Coleções, como <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Tipos de utilitário, como <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Tipos de dados, como <xref:System.Data.DataSet?displayProperty=nameWithType>, e [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Tipos de alto desempenho, como <xref:System.Numerics.Vector?displayProperty=nameWithType> e [pipelines](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/).

O .NET Core oferece compatibilidade com as APIs do .NET Framework e do Mono por meio da implementação da especificação [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Estruturas

Várias estruturas já foram criadas com base no .NET Core:

- [ASP.NET Core](/aspnet/core/)
- [Plataforma Universal do Windows (UWP) do Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composição

O .NET Core é composto pelas seguintes partes:

- O [tempo de execução do .NET Core](https://github.com/dotnet/coreclr), que fornece um sistema de tipos, carregamento de assembly, coletor de lixo, interoperabilidade nativa e outros serviços básicos. As [bibliotecas do .NET Core Framework](https://github.com/dotnet/corefx) fornecem tipos de dados primitivos, tipos de composição de aplicativo e utilitários fundamentais.
- O [tempo de execução do ASP.net](https://github.com/aspnet/home), que fornece uma estrutura para a criação de aplicativos conectados à Internet modernos baseados em nuvem, como aplicativos Web, aplicativos de IOT e back-ends móveis.
- As [ferramentas da CLI do .NET Core](https://github.com/dotnet/cli) e os compiladores de linguagem ([Roslyn](https://github.com/dotnet/roslyn) e [F#](https://github.com/microsoft/visualfsharp)) que permitem a experiência de desenvolvedor do .NET Core.
- A [ferramenta dotnet](https://github.com/dotnet/core-setup), que é usada para iniciar aplicativos do .NET Core e ferramentas da CLI. Ele seleciona o tempo de execução e hospeda o tempo de execução, fornece uma política de carregamento de assembly e inicia aplicativos e ferramentas.

Esses componentes são distribuídos das seguintes maneiras:

- [Tempo de execução do .NET Core](https://dotnet.microsoft.com/download) – inclui as bibliotecas de tempo de execução e de estruturas do .NET Core.
- [Tempo de execução do ASP.NET Core](https://dotnet.microsoft.com/download) – inclui bibliotecas de tempo de execução e de estruturas do ASP.NET Core e do .NET Core.
- [SDK do .NET Core](https://dotnet.microsoft.com/download) – inclui as ferramentas da CLI do .NET, o tempo de execução do ASP.NET Core e o tempo de execução e a estrutura do .NET Core.

### <a name="open-source"></a>Código Aberto

O [.NET Core](https://github.com/dotnet/core) é um software livre ([licença MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) que foi concedido ao [.NET Foundation](https://dotnetfoundation.org) pela Microsoft em 2014. Agora é um dos projetos mais ativos do .NET Foundation. Ele pode ser usado por indivíduos e empresas, inclusive para fins pessoais, acadêmicos ou comerciais. Várias empresas usam o .NET Core como parte de aplicativos, ferramentas, novas plataformas e serviços de hospedagem. Algumas dessas empresas fazer contribuições significativas para o .NET Core no GitHub e fornecem diretrizes sobre a direção de produto como parte do [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Projetado para adaptabilidade

O .NET Core foi criado como um produto muito semelhante, mas exclusivo, comparado a outros produtos .NET. Ele foi projetado para permitir maior adaptabilidade a novas plataformas e cargas de trabalho e tem várias portas de sistema operacional e CPU disponíveis (e pode ser portada para muitos outros).

O produto é dividido em várias partes que podem se adaptar a novas plataformas em momentos diferentes. O tempo de execução e as bibliotecas fundamentais específicas de plataformas devem ser transportados como uma unidade. Bibliotecas independentes de plataforma devem funcionar no estado em que se encontra em todas as plataformas como-está em todas as plataformas desde a construção. Há uma tendência de projeto em relação à redução de implementações específicas da plataforma para aumentar a eficiência do desenvolvedor C# , o código de plataforma neutra de preferência sempre que um algoritmo ou API pode ser implementado de forma completa ou parcial.

As pessoas geralmente perguntam como o .NET Core é implementado para dar suporte a vários sistemas operacionais. Eles normalmente perguntam se há implementações separadas ou se a [compilação condicional](https://en.wikipedia.org/wiki/Conditional_compilation) é usada. A resposta é ambas, com uma forte tendência para a compilação condicional.

Veja no gráfico a seguir que a maior parte do [CoreFX](https://github.com/dotnet/corefx) é um código neutro compartilhado entre todas as plataformas. O código neutro de plataforma pode ser implementado como um único assembly portátil usado em todas as plataformas.

![CoreFX: Linhas de código por plataforma](../images/corefx-platforms-loc.png)

Implementações de Windows e Unix são semelhantes em tamanho. O Windows tem uma implementação maior, já que o CoreFX implementa alguns recursos somente do Windows, como [Microsoft. Win32. Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , mas ainda não implementa muitos conceitos somente para UNIX. Você também verá que a maioria das implementações do Linux e do macOS é compartilhada em uma implementação do UNIX, enquanto as implementações específicas do Linux e do macOS são aproximadamente semelhantes em termos de tamanho.

Há uma combinação de bibliotecas específicas de plataforma e de plataforma neutra no .NET Core. Você pode observar esse padrão em alguns exemplos:

- O [CoreCLR](https://github.com/dotnet/coreclr) é específico de plataforma. Ele é baseado nos subsistemas do sistema operacional, como o gerenciador de memória e o agendador de thread.
- O [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) e o [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) são específicos da plataforma, pois as APIs de armazenamento e de criptografia são diferentes em cada sistema operacional.
- O [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) e [System.LINQ](https://github.com/dotnet/corefx/tree/master/src/System.Linq) são neutros de plataforma, considerando que eles podem criar e operar em estruturas de dados.

## <a name="comparisons-to-other-net-implementations"></a>Comparações com outras implementações do .NET

Provavelmente é mais fácil entender o tamanho e a forma do .NET Core comparando-os com as implementações existentes do .NET.

### <a name="comparison-with-net-framework"></a>Comparação com o .NET Framework

O .NET foi anunciado pela primeira vez pela Microsoft em 2000 e continuou evoluindo a partir daí. O .NET Framework foi a principal implementação do .NET produzida pela Microsoft durante esse período de quase duas décadas.

Principais diferenças entre o .NET Core e o .NET Framework:

- Os **modelos de aplicativo** --. NET Core não dão suporte a todos os .NET Framework modelos de aplicativos. Ele não dá suporte especificamente a Web Forms do ASP.NET e a ASP.NET MVC, mas dá suporte ao ASP.NET Core MVC. E, a partir do .NET Core 3,0, o .NET Core também oferece suporte ao WPF e Windows Forms somente no Windows.
- **APIs** – o .NET Core contém um grande subconjunto da biblioteca de classes base .NET Framework, com aspectos diferentes (os nomes de assembly são diferentes, os membros expostos nos tipos são diferentes em casos principais). Em alguns casos, essas diferenças exigem alterações na origem da porta para o .NET Core. Para obter mais informações, consulte [o .net Portability Analyzer](../standard/analyzers/portability-analyzer.md). O .NET Core implementa a especificação de API [.NET Standard](../standard/net-standard.md).
- **Subsistemas** – O.NET Core implementa um subconjunto dos subsistemas no .NET Framework com o objetivo de proporcionar uma implementação e um modelo de programação mais simples. Por exemplo, a CAS (segurança de acesso do código) não tem suporte, enquanto a reflexão tem suporte.
- **Plataformas** – O .NET Framework dá suporte a Windows e Windows Server, enquanto o .NET Core também dá suporte a macOS e Linux.
- **Software Livre** – O .NET Core é um software livre, enquanto apenas um [subconjunto somente leitura do .NET Framework](https://github.com/microsoft/referencesource) é um software livre.

Embora o .NET Core seja exclusivo e tenha diferenças significativas no .NET Framework e em outras implementações do .NET, é simples compartilhar o código entre essas implementações, usando técnicas de compartilhamento de origem ou binária.

Como o .NET Core é compatível com a instalação lado a lado, e seu tempo de execução é completamente independente do .NET Framework, ele pode ser instalado em computadores com o .NET Framework instalado sem problemas.

### <a name="comparison-with-mono"></a>Comparação com Mono

O [mono](https://www.mono-project.com/) é a implementação original de plataforma cruzada do .net. Ele começou [como uma alternativa de software](https://github.com/mono/mono) livre para .NET Framework e transicionado para direcionar dispositivos móveis, já que dispositivos IOS e Android se tornaram populares. Ele pode ser considerado um clone de comunidade do .NET Framework. A equipe do projeto mono dependia dos [padrões .net](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) abertos (notavelmente ECMA 335) publicados pela Microsoft para fornecer uma implementação compatível.

Principais diferenças entre o .NET Core e o Mono:

- **App-Models** --o mono dá suporte a um subconjunto do .NET Framework modelos de aplicativo (por exemplo, Windows Forms) e alguns outros para desenvolvimento móvel (por exemplo, [Xamarin. Ios](https://www.xamarin.com/platform)) por meio do produto xamarin. O .NET Core não dá suporte ao Xamarin.
- **APIs** – O Mono dá suporte a um [grande subconjunto](http://docs.go-mono.com/?link=root%3a%2fclasslib) das APIs do .NET Framework, usando os mesmos nomes de assembly e assinaturas.
- **Plataformas** – O Mono dá suporte a várias plataformas e CPUs.
- **Software Livre** – O Mono e o .NET Core usam a licença MIT e são projetos do .NET Foundation.
- **Foco** – o principal foco do Mono nos últimos anos são as plataformas móveis, enquanto o .NET Core se concentra em cargas de trabalho de nuvem e da área de trabalho.

## <a name="the-future"></a>O futuro

Foi anunciado que o .NET 5 será a próxima versão do .NET Core e representa uma unificação da plataforma. O projeto visa melhorar o .NET de algumas maneiras principais:

- Produzir um único tempo de execução e estrutura .NET que possam ser usados em todo lugar e que tenha comportamentos de tempo de execução uniformes e experiências de desenvolvedor.
- Expanda os recursos do .NET adotando o melhor do .NET Core, .NET Framework, Xamarin e mono.
- Crie esse produto a partir de uma base de código única que os desenvolvedores (a Microsoft e a Comunidade) possam trabalhar e expandir juntos e que melhorem todos os cenários.

Para obter mais detalhes sobre o que está sendo planejado para o .NET 5, consulte [apresentando o .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
