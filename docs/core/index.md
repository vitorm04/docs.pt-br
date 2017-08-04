---
title: .NET Core
description: "O .NET core é uma implementação modular de alto desempenho do .NET para a criação de aplicativos do Windows, Linux e Mac. Saiba mais sobre o .NET Core para começar."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f2b312cb-f80c-4b0d-9101-93908f06a6fa
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0e002411d9856bc5f98566ed1bd9d8122e884d5d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="net-core"></a>.NET Core

> Confira os [Tutoriais de "Introdução"](get-started.md) para aprender a criar um aplicativo .NET Core simples. Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.

O .NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no [GitHub](https://github.com/dotnet/core). Ele é de plataforma cruza e dá suporte ao Windows, macOS e Linux, e podendo ser usado no dispositivo, na nuvem e em cenários inserido/IoT. 

As seguintes características são as que melhor definem o .NET Core:

- **Implantação flexível:** pode ser incluído no seu aplicativo ou ser instalado lado a lado no usuário ou em todos os computadores.
- **Plataforma cruzada:** executa em Windows, macOS e Linux e pode ser transferida para outros sistemas operacionais. Os [sistemas operacionais com suporte](https://github.com/dotnet/core/blob/master/roadmap.md), CPUs e cenários de aplicação serão ampliados com os passar do tempo, fornecidos pela Microsoft, outras empresas e outros indivíduos.
- **Ferramentas de linha de comando:** todos os cenários de produto podem ser exercidos na linha de comando. 
- **Compatibilidade:** o .NET Core é compatível com .NET Framework, Xamarin e Mono por meio da [.NET Standard](../standard/net-standard.md).
- **Código-fonte aberto:** a plataforma do .NET Core é um software livre que usa licenças do MIT e Apache 2. A documentação é licenciada por [CC-BY](https://creativecommons.org/licenses/by/4.0/). O .NET Core é um projeto do [.NET Foundation](https://dotnetfoundation.org/).
- **Suporte da Microsoft:** .NET Core tem suporte pela Microsoft, pelo [Suporte do .NET Core](https://www.microsoft.com/net/core/support/)

## <a name="composition"></a>Composição

O .NET Core é composto pelas seguintes partes:

- Um [tempo de execução .NET](https://github.com/dotnet/coreclr) que fornece um sistema de tipo, carregamento de assembly, coletor de lixo, interoperabilidade nativa e outros serviços básicos. 
- Um conjunto de [bibliotecas de estruturas](https://github.com/dotnet/corefx) que fornece tipos de dados primitivos, tipos de composição de aplicativos e utilitários fundamentais. 
- Um [conjunto de ferramentas do SDK](https://github.com/dotnet/cli) e [compiladores de linguagem](https://github.com/dotnet/roslyn) que habilitam a experiência de desenvolvedor básica disponível no [SDK do .NET Core](sdk.md).
- O host de aplicativo “dotnet”, que é usado para iniciar aplicativos .NET Core. Ele seleciona e hospeda o tempo de execução, fornece um assembly para carregar a política e inicia o aplicativo. O mesmo host também é usado para abrir as ferramentas de SDK da mesma maneira.

### <a name="languages"></a>Linguagens

As linguagens C# e F# (o Visual Basic virá em breve) podem ser usadas para criar aplicativos e bibliotecas para .NET Core. Os compiladores são executados no .NET Core, permitindo que você desenvolva soluções para .NET Core em qualquer lugar ele é executado. Em geral, você não usará os compiladores diretamente, mas sim indiretamente, usando as ferramentas do SDK.

Os compiladores C# e F# e as ferramentas do .NET Core são ou podem ser integradas em vários editores de texto e IDEs, incluindo o Visual Studio, [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text e Vim, tornando o desenvolvimento no .NET Core uma boa opção nos seus ambientes de codificação e sistemas operacionais favoritos. Essa integração é fornecida, em parte, pelo pessoal do [projeto OmniSharp](http://www.omnisharp.net/).

### <a name="net-apis-and-compatibility"></a>APIs e compatibilidade do .NET

O .NET Core pode ser pensado como uma versão de plataforma cruzada do .NET Framework, na camada da BCL (Biblioteca de Classes Base) do .NET Framework. Ele implementa a especificação [.NET Standard](../standard/net-standard.md). O .NET Core fornece um subconjunto das APIs que estão disponíveis no .NET Framework ou Mono/Xamarin. Em alguns casos, os tipos não são implementados completamente (alguns membros não estão disponíveis ou foram movidos).

Examine o [Roteiro do .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md) para saber mais sobre o roteiro da API do .NET Core.

### <a name="relationship-to-net-standard"></a>Relacionamento com o .NET padrão

A [.NET Standard](../standard/net-standard.md) é uma especificação de API que descreve o conjunto coerente de APIs .NET que os desenvolvedores podem esperar em cada implementação do .NET. Implementações do .NET precisam implantar essa especificação para serem consideradas em conformidade com o .NET Standard e para dar suporte a bibliotecas voltadas para o .NET Standard. 

O .NET Core implementa o .NET Standard e, portanto, dá suporte a bibliotecas do .NET Standard.

### <a name="workloads"></a>Cargas de trabalho

Por si só, o .NET Core inclui um modelo de aplicativo único, os aplicativos de console, que são úteis para ferramentas, serviços locais e os jogos baseados em texto. Modelos de aplicativo adicionais foram criados junto ao .NET Core para estender sua funcionalidade, como:

- [ASP.NET Core](/aspnet/core/)
- [Plataforma Universal do Windows (UWP) do Windows 10](https://developer.microsoft.com/windows)
- [Xamarin.Forms ao direcionar para a UWP](https://www.xamarin.com/forms)

### <a name="open-source"></a>Software Livre

O [.NET Core](https://github.com/dotnet/core) é um software livre (licença MIT) e foi concedido ao [.NET Foundation](https://dotnetfoundation.org) pela Microsoft em 2014. Agora ele é um dos projetos mais ativos do .NET Foundation. Ele pode ser adotado livremente por pessoas e empresas, incluindo para fins pessoais, comerciais ou acadêmicos. Várias empresas usam o .NET Core como parte de aplicativos, ferramentas, novas plataformas e serviços de hospedagem. Algumas dessas empresas fazer contribuições significativas para o .NET Core no GitHub e fornecem diretrizes sobre a direção de produto como parte do [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

## <a name="acquisition"></a>Aquisição

O .NET Core é distribuído de duas maneiras principais, como pacotes no NuGet.org e como distribuições autônomas.

### <a name="distributions"></a>Distribuições

Você pode baixar o .NET Core na página [Introdução ao .NET Core](https://www.microsoft.com/net/core).

- A distribuição *Microsoft .NET Core* inclui o tempo de execução do CoreCLR, bibliotecas associadas, um host de aplicativo de console e o inicializador de aplicativos do `dotnet`. Ele é descrito pelo metapacote [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App).
- A distribuição do *SDK do Microsoft .NET Core* inclui o .NET Core e um conjunto de ferramentas para restaurar pacotes NuGet e compilar e criar aplicativos. 

Normalmente, você primeiro instala a introdução ao SDK do .NET Core com desenvolvimento de .NET Core. Você pode optar por instalar compilações adicionais (talvez pré-lançamento) do .NET Core.

### <a name="packages"></a>Pacotes

- [Pacotes do .NET Core](packages.md) contêm o tempo de execução e as bibliotecas do .NET Core (implementações e assemblies de referência). Por exemplo, [System.Net.Http](https://www.nuget.org/packages/System.Net.Http/).
- [Metapacotes do .NET Core](packages.md) descrevem várias camadas e modelos de aplicativo referenciando o conjunto apropriado de pacotes de biblioteca com versão.

## <a name="architecture"></a>Arquitetura

O .NET Core é uma implementação de plataforma cruzada do .NET. As principais questões de arquitetura exclusivas do .NET Core são referentes a implementações específicas de plataforma para as plataformas com suporte.

### <a name="environments"></a>Ambientes

O .NET Core tem suporte com o Microsoft no Windows, macOS e Linux. No Linux, a Microsoft dá suporte principalmente ao .NET Core em execução em famílias de distribuição do RHEL (Red Hat Enterprise Linux) ou Debian.

O .NET Core dá suporte a CPUs X64 no momento. No Windows, também há suporte para X86. O suporte para ARM64 e ARM32 está em andamento.

O [Roteiro do .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md) fornece informações mais detalhadas sobre a carga de trabalho e suporte e planos do ambiente do sistema operacional e de CPU.

Outras empresas ou grupos podem dar suporte a .NET Core para outros tipos de aplicativos e ambientes.

### <a name="designed-for-adaptability"></a>Projetado para adaptação

O .NET Core foi criado como um produto muito semelhante, porém único, em relação a outros produtos .NET. Ele foi projetado para possibilitar ampla adaptação a novas plataformas, para novas cargas de trabalho e com novas cadeias de ferramentas do compilador. Ele tem portas de vários sistemas operacionais e CPU em andamento e pode ser levado para muitos outros. Um exemplo é o projeto [LLILC](https://github.com/dotnet/llilc), que é um protótipo inicial da compilação nativa para .NET Core por meio do compilador [LLVM](http://llvm.org/).

O produto é dividido em várias partes, permitindo que essas sejam adaptadas para novas plataformas em diferentes agendas. O tempo de execução e as bibliotecas fundamentais específicas de plataformas devem ser transportados como uma unidade. Bibliotecas independentes de plataforma devem funcionar no estado em que se encontra em todas as plataformas como-está em todas as plataformas desde a construção. Há uma tendência de projeto em reduzir as implementações específicas de plataforma para aumentar a eficiência dos desenvolvedores, preferindo código C# neutro com relação à plataforma sempre que um algoritmo ou API puder ser implementado dessa maneira de forma total ou parcial.

As pessoas geralmente perguntam como o .NET Core é implementado para dar suporte a vários sistemas operacionais. Eles normalmente perguntam se há implementações separadas ou se a [compilação condicional](https://en.wikipedia.org/wiki/Conditional_compilation) é usada. Ambos, com uma fonte tendência para compilação condicional.

Você pode ver no gráfico abaixo que a grande maioria dos [CoreFX](https://github.com/dotnet/corefx) neutros em relação à plataforma são compartilhados entre todas as plataformas. O código neutro com relação à plataforma pode ser implementado como um único assembly portátil usado em todas as plataformas.

![CoreFX: Linhas de código por plataforma](../images/corefx-platforms-loc.png)

Implementações de Windows e Unix são semelhantes em tamanho. O Windows tem uma implementação maior, pois o CoreFX implementa alguns recursos exclusivos do Windows como o [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry), mas ainda não implementa nenhum conceito exclusivo do Unix. Você também verá que a maioria das implementações do Linux e do macOS são compartilhadas com uma implementação do Unix, enquanto as implementações específicas de Linux e macOS são semelhantes em tamanho.


Há uma combinação de bibliotecas específicas ou neutras de plataforma no .NET Core. Você pode observar esse padrão em alguns exemplos:

- O [CoreCLR](https://github.com/dotnet/coreclr) é específico de plataforma. Ele é criado em C/C++, portanto é específico a uma plataforma desde sua criação.
- O [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) e o [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) são específicas de plataforma, considerando que as APIs de armazenamento e de criptografia diferem significativamente em cada sistema operacional. 
- O [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) e [System.LINQ](https://github.com/dotnet/corefx/tree/master/src/System.Linq) são neutros de plataforma, considerando que eles podem criar e operar em estruturas de dados.

## <a name="comparisons-to-other-net-platforms"></a>Comparações com outras plataformas .NET

Talvez seja mais fácil entender o tamanho e a forma do .NET Core ao compará-lo com as plataformas .NET existentes. 

### <a name="comparison-with-net-framework"></a>Comparação com o .NET Framework

A plataforma .NET foi anunciada pela primeira vez pela Microsoft em 2000, evoluindo a partir daí. O .NET Framework foi o principal produto .NET produzido pela Microsoft durante esse período de 15 anos. 

Principais diferenças entre o .NET Core e o .NET Framework: 

- **Modelos de aplicativo** – O .NET Core não dá suporte a todos os modelos de aplicativo .NET Framework, em parte porque muitos deles são criados em tecnologias do Windows, como o WPF (baseado no DirectX). O console e os modelos de aplicativo do ASP.NET Core tem suporte com ambos o .NET Core e o .NET Framework. 
- **APIs** – O.NET Core contém vários das mesmas APIs que o .NET Framework, porém em menor quantidade e com um cálculo diferentes (nomes de assembly são diferentes e a forma de tipo difere nos casos principais). No momento, essas diferenças normalmente exigem alterações na origem de porta para o .NET Core. O .NET Core implementa a API [.NET Standard](../standard/net-standard.md), que crescerá para incluir mais funcionalidades da API BCL do .NET Framework ao longo do tempo.
- **Subsistemas** – O.NET Core implementa um subconjunto dos subsistemas no .NET Framework com o objetivo de proporcionar uma implementação e um modelo de programação mais simples. Por exemplo, não há suporte para CAS (Segurança de Acesso do Código), porém há suporte para reflexão.
- **Plataformas** – O .NET Framework dá suporte a Windows e Windows Server, enquanto o .NET Core também dá suporte a macOS e Linux.
- **Software Livre** – O.NET Core é um software livre, enquanto um [subconjunto somente leitura do .NET Framework](https://github.com/microsoft/referencesource) é um software livre.

Embora o .NET Core seja único e apresente diferenças significativas do .NET Framework e outras plataformas .NET, é muito fácil compartilhar o código usando técnicas de compartilhamento de código-fonte ou de binário. 

### <a name="comparison-with-mono"></a>Comparação com Mono

O [Mono](http://www.mono-project.com/) é a implementação .NET de plataforma cruzada e de [software livre](https://github.com/mono/mono) original, sendo fornecido pela primeira vez em 2004. Ele pode ser considerado um clone de comunidade do .NET Framework. A equipe de projeto do Mono contava com [padrões .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (especificamente o ECMA 335) publicados pela Microsoft a fim de fornecer uma implementação compatível.

Principais diferenças entre o .NET Core e o Mono:

- **Modelos de aplicativo** – O Mono dá suporte a um subconjunto de modelos de aplicativo do .NET Framework (por exemplo, o Windows Forms) e a alguns outros (como o [Xamarin.iOS](https://www.xamarin.com/platform)) por meio do produto Xamarin. O .NET Core não dá suporte a eles.
- **APIs** – O Mono dá suporte a um [grande subconjunto](http://docs.go-mono.com/?link=root%3a%2fclasslib) das APIs do .NET Framework, usando os mesmos nomes de assembly e fatoração.
- **Plataformas** – O Mono dá suporte a várias plataformas e CPUs.
- **Software Livre** – O Mono e o .NET Core usam a licença MIT e são projetos do .NET Foundation.
- **Foco** – O principal foco do Mono nos últimos anos são as plataformas móveis, enquanto o .NET Core é voltado para cargas de trabalho na nuvem.

