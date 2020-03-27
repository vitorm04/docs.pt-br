---
title: Componentes de arquitetura do .NET
description: Descreve os componentes de arquitetura do .NET, como o .NET Standard, as implementações do .NET, os runtimes do .NET e as ferramentas.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 027fdb4cec47550f88f6930a4bbdff4ab5cdfb36
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344158"
---
# <a name="net-architectural-components"></a>Componentes de arquitetura do .NET

Um aplicativo .NET é desenvolvido para e é executado em uma ou mais *implementações do .NET*.  Implementações do .NET incluem o .NET Framework, o .NET Core e o Mono. Há uma especificação de API comum a todas as implementações de .NET que é chamada de .NET Standard. Este artigo fornece uma breve introdução a cada um desses conceitos.

## <a name="net-standard"></a>.NET Standard

.NET Standard é um conjunto de APIs que são implementadas pela Biblioteca de Classe Base de uma implementação .NET. De maneira mais formal, é uma especificação das APIs do .NET que compõem um conjunto uniforme de contratos nos quais você compila seu código. Esses contratos são implementados em cada implementação do .NET. Isso permite a portabilidade entre diferentes implementações de .NET, possibilitando efetivamente que seu código seja executado em qualquer lugar.

.NET Standard também é uma [estrutura de destino](glossary.md#target-framework). Se o código tiver como alvo uma versão do .NET Standard, ele poderá ser executado em qualquer implementação .NET que suporte essa versão do .NET Standard.

Para saber mais sobre o .NET Standard e como segmentá-lo, consulte [.NET Standard](net-standard.md).

## <a name="net-implementations"></a>Implementações do .NET

Cada implementação do .NET inclui os seguintes componentes:

- Um ou mais runtimes. Exemplos: o CLR para o .NET Framework, o CoreCLR e o CoreRT para o .NET Core.
- Uma biblioteca de classes que implemente o .NET Standard e possa implementar APIs adicionais. Exemplos: biblioteca de classes base do NET Framework, biblioteca de classes base do .NET Core.
- Opcionalmente, uma ou mais estruturas de aplicativo. Exemplos: [ASP.NET,](https://www.asp.net/) [Windows Forms](../framework/winforms/windows-forms-overview.md)e [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) estão incluídos no .NET Framework e no .NET Core.
- Opcionalmente, ferramentas de desenvolvimento. Algumas ferramentas de desenvolvimento são compartilhadas entre várias implementações.

Há quatro implementações principais de .NET que a Microsoft desenvolve e mantém ativamente: .NET Core, .NET Framework, Mono e UWP.

### <a name="net-core"></a>.NET Core

O .NET Core é uma implementação multiplataforma do .NET, projetado para lidar com cargas de trabalho de servidor e na nuvem em escala. Ele é executado no Windows, macOS e Linux. Ele implementa o .NET Standard, portanto o código direcionado para o .NET Standard pode ser executados no .NET Core. O [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), o [Windows Forms](../framework/winforms/windows-forms-overview.md) e o [WPF (Windows Presentation Foundation)](../framework/wpf/index.md) são executados no .NET Core.

Para saber mais sobre o .NET Core, consulte a [Guia .NET Core](../core/index.yml) e [Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework é a implementação original do .NET que existe desde 2002. As versões 4.5 e posteriores implementam o .NET Standard, de modo que o código que tem como alvo o .NET Standard pode ser executado nessas versões do .NET Framework. Ele contém APIs adicionais específicas do Windows, como APIs para desenvolvimento de área de trabalho do Windows com o Windows Forms e o WPF. O .NET Framework é otimizado para a compilação de aplicativos da área de trabalho do Windows.

Para saber mais sobre o .NET Framework, consulte o [Guia de Quadro .NET](../framework/index.yml).

### <a name="mono"></a>Mono

O Mono é uma implementação do .NET que é usada principalmente quando um pequeno runtime é necessário. É o tempo de execução que alimenta os aplicativos Xamarin no Android, macOS, iOS, tvOS e watchOS e é focado principalmente em uma pequena pegada. O Mono também é plataforma para jogos criados com o mecanismo Unity.

Ele dá suporte a todas as versões do .NET Standard publicadas atualmente.

Historicamente, o Mono implementava a maior API do .NET Framework e emulava alguns dos recursos mais populares do Unix. Às vezes, ele é usado para executar aplicativos .NET que dependem desses recursos no Unix.

O Mono normalmente é usado com um compilador Just-In-Time, mas ele também apresenta um compilador estático completo (compilação Ahead Of Time) que é usado em plataformas como iOS.

Para saber mais sobre o Mono, consulte a [Documentação do Mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>UWP (Plataforma Universal do Windows)

A UWP é uma implementação do .NET que é usada para criar aplicativos do Windows modernos e sensíveis ao toque, bem como software para a IoT (Internet das Coisas). Ele foi projetado para unificar os diferentes tipos de dispositivos que você pode querer segmentar, incluindo PCs, tablets, telefones e até mesmo o Xbox. A UWP fornece muitos serviços, como um repositório centralizado de aplicativos, um ambiente de execução (AppContainer) e um conjunto de APIs do Windows para usar em vez das APIS do Win32 (WinRT). Os aplicativos podem ser escritos em C++, C#, Visual Basic e JavaScript. Ao usar C# e Visual Basic, as APIs .NET são fornecidas pelo .NET Core.

Para saber mais sobre a UWP, consulte [Introdução à Plataforma Universal do Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Runtimes do .NET

Um runtime é o ambiente de execução de um programa gerenciado. O SO faz parte do ambiente do runtime, mas não faz parte do runtime do .NET. Aqui estão alguns exemplos de runtimes do .NET:

- CLR (Common Language Runtime) para o .NET Framework
- Core Common Language Runtime (CoreCLR) para o .NET Core
- .NET Native para a Plataforma Universal do Windows
- O runtime Mono para Xamarin.iOS, Xamarin.Android, Xamarin.Mac e a estrutura de área de trabalho do Mono

## <a name="net-tooling-and-common-infrastructure"></a>Ferramentas do .NET e infraestrutura comum

Você tem acesso a um amplo conjunto de ferramentas e componentes de infraestrutura que funcionam com todas as implementações do .NET. Essas ferramentas e componentes incluem:

- As linguagens do .NET e seus compiladores
- O sistema de projetos do .NET (com base em arquivos *.csproj*, *.vbproj* e *.fsproj*)
- [MSBuild](/visualstudio/msbuild/msbuild), o mecanismo de construção usado para construir projetos
- [NuGet](/nuget/), gerenciador de pacotes da Microsoft para .NET
- Ferramentas de orquestração de build em software livre, como [CAKE](https://cakebuild.net/) e [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>Normas aplicáveis

As especificações c# Language e common language infrastructure (CLI) são padronizadas através [da Ecma&reg;International](https://www.ecma-international.org/). As primeiras edições dessas normas foram publicadas pela ECMA em dezembro de 2001.

As revisões subseqüentes das normas foram desenvolvidas pelos grupos de tarefas TC49-TG2 (C#) e TC49-TG3 (CLI) dentro do Comitê Técnico de Linguagens de Programação ([TC49),](https://www.ecma-international.org/memento/tc49.htm)e adotadas pela Assembléia Geral da ECMA e, posteriormente, pela ISO/IEC JTC 1 através do processo ISO Fast-Track.

### <a name="latest-standards"></a>Últimos padrões

Os seguintes documentos oficiais da ECMA estão disponíveis para [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) e para a [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) [(TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)):

- **O C# Language Standard (versão 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **A Infra-estrutura de linguagem comum**: Disponível em [forma pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) e [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) form.
- **Informações derivadas do arquivo Partição IV XML**: Disponível em [formatos pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) e [zip.](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip)

Os documentos iso/iec oficiais estão disponíveis na página [Normas Disponíveis publicamente](https://standards.iso.org/ittf/PubliclyAvailableStandards/) da ISO/IEC. Esses links são diretos dessa página:

- **Tecnologia da informação - Linguagens de programação - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Tecnologia da informação — Infra-estrutura de linguagem comum (CLI) Partições I a VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Tecnologia da informação — Infra-estrutura de linguagem comum (CLI) — Relatório Técnico sobre informações derivadas da Partição IV Arquivo XML**: [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Confira também

- [Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [.NET Core Guide](../core/index.yml)
- [.NET Framework Guide](../framework/index.yml)
- [Guia C#](../csharp/index.yml)
- [Guia F#](../fsharp/index.yml)
- [Guia Básico Visual](../visual-basic/index.yml)
