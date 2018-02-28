---
title: Componentes de arquitetura do .NET
description: "Descreve os componentes de arquitetura do .NET, como o .NET Standard, as implementações do .NET, os tempos de execução do .NET e as ferramentas."
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a17d4c36d9c1942166b9ad889103a7942f1813d
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="net-architectural-components"></a>Componentes de arquitetura do .NET

Um aplicativo .NET é desenvolvido para e é executado em uma ou mais *implementações do .NET*.  Implementações do .NET incluem o .NET Framework, o .NET Core e o Mono. Há uma especificação de API comum a todas as implementações de .NET que é chamada de .NET Standard. Este artigo fornece uma breve introdução a cada um desses conceitos.

## <a name="net-standard"></a>.NET Standard

O .NET Standard é um conjunto de APIs que são implementadas pela Biblioteca de classes base de uma implementação do .NET. De maneira mais formal, é uma especificação das APIs do .NET que compõem um conjunto uniforme de contratos nos quais você compila seu código. Esses contratos são implementados em cada implementação do .NET. Isso permite a portabilidade entre diferentes implementações de .NET, possibilitando efetivamente que seu código seja executado em qualquer lugar.

O .NET Standard também é uma [estrutura de destino](glossary.md#target-framework). Se seu código se destina a uma versão do .NET Standard, ele pode ser executado em qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.

Para saber mais sobre o NET Standard e como destinar a ele, consulte o tópico [.NET Standard](net-standard.md).

## <a name="net-implementations"></a>Implementações do .NET

Cada implementação do .NET inclui os seguintes componentes:

- Um ou mais tempos de execução. Exemplos: o CLR para o .NET Framework, o CoreCLR e o CoreRT para o .NET Core.
- Uma biblioteca de classes que implemente o .NET Standard e possa implementar APIs adicionais. Exemplos: biblioteca de classes base do NET Framework, biblioteca de classes base do .NET Core.
- Opcionalmente, uma ou mais estruturas de aplicativo. Exemplos: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md) e [WPF (Windows Presentation Foundation)](../framework/wpf/index.md) estão incluídos no .NET Framework.
- Opcionalmente, ferramentas de desenvolvimento. Algumas ferramentas de desenvolvimento são compartilhadas entre várias implementações.

Há quatro implementações principais de .NET que a Microsoft desenvolve e mantém ativamente: .NET Core, .NET Framework, Mono e UWP.

### <a name="net-core"></a>.NET Core

O .NET Core é uma implementação multiplataforma do .NET, projetado para lidar com cargas de trabalho de servidor e na nuvem em escala. Ele é executado no Windows, no Linux e no macOS. Ele implementa o .NET Standard, portanto o código direcionado para o .NET Standard pode ser executados no .NET Core. O ASP.NET Core é executado no .NET Core. 

Para saber mais sobre o .NET Core, consulte a [Guia .NET Core](../core/index.md) e [Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

O.NET Framework é a implementação original do .NET que existe desde 2002. É o mesmo .NET Framework que os desenvolvedores do .NET sempre usaram. As versões 4.5 e posteriores implementam o .NET Standard, assim, o código que se destina ao .NET Standard pode ser executado nessas versões do .NET Framework. Ele contém APIs adicionais específicas do Windows, como APIs para desenvolvimento de área de trabalho do Windows com o Windows Forms e o WPF. O .NET Framework é otimizado para a compilação de aplicativos da área de trabalho do Windows.

Para saber mais sobre o .NET Framework, consulte o [Guia do .NET Framework](../framework/index.md).

### <a name="mono"></a>Mono

O Mono é uma implementação do .NET que é usada principalmente quando um pequeno tempo de execução é necessário. É o tempo de execução que impulsiona aplicativos Xamarin no Android, Mac, iOS, tvOS e watchOS e concentra-se principalmente em um impacto pequeno. O Mono também é plataforma para jogos criados com o mecanismo Unity.

Ele dá suporte a todas as versões do .NET Standard publicadas atualmente.

Historicamente, o Mono implementava a maior API do .NET Framework e emulava alguns dos recursos mais populares do Unix. Às vezes, ele é usado para executar aplicativos .NET que dependem desses recursos no Unix.

O Mono normalmente é usado com um compilador Just-In-Time, mas ele também apresenta um compilador estático completo (compilação Ahead Of Time) que é usado em plataformas como iOS.

Para saber mais sobre o Mono, consulte a [Documentação do Mono](http://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>UWP (Plataforma Universal do Windows)

A UWP é uma implementação do .NET que é usada para criar aplicativos do Windows modernos e sensíveis ao toque, bem como software para a IoT (Internet das Coisas). Ela foi projetada para unificar os diferentes tipos de dispositivos que você talvez tenha como destinho, incluindo PCs, tablets, phablets, telefones e até mesmo ao Xbox. A UWP fornece muitos serviços, como um repositório centralizado de aplicativos, um ambiente de execução (AppContainer) e um conjunto de APIs do Windows para usar em vez das APIS do Win32 (WinRT). Os aplicativos podem ser escritos em C++, C#, VB.NET e JavaScript. Ao usar o C# e VB.NET, as APIs do .NET são fornecidas pelo .NET Core.

Para saber mais sobre a UWP, consulte [Introdução à Plataforma Universal do Windows](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Tempos de execução do .NET

Um tempo de execução é o ambiente de execução de um programa gerenciado. O SO faz parte do ambiente do tempo de execução, mas não faz parte do tempo de execução do .NET. Aqui estão alguns exemplos de tempos de execução do .NET:
 
 - CLR (Common Language Runtime) para o .NET Framework
 - Core Common Language Runtime (CoreCLR) para o .NET Core
 - .NET Native para a Plataforma Universal do Windows 
 - O tempo de execução Mono para Xamarin.iOS, Xamarin.Android, Xamarin.Mac e a estrutura de área de trabalho do Mono

## <a name="net-tooling-and-common-infrastructure"></a>Ferramentas do .NET e infraestrutura comum

Você tem acesso a um amplo conjunto de ferramentas e componentes de infraestrutura que funcionam com todas as implementações do .NET. Elas incluem, mas não são limitadas a, o seguinte:

- As linguagens do .NET e seus compiladores
- O sistema de projetos do .NET (com base em arquivos *.csproj*, *.vbproj* e *.fsproj*)
- [MSBuild](/visualstudio/msbuild/msbuild), o mecanismo de build usado para compilar projetos
- [NuGet](/nuget/), o gerenciador de pacotes da Microsoft para o .NET
- Ferramentas de orquestração de build em software livre, como [CAKE](http://cakebuild.net/) e [FAKE](https://fake.build/)

## <a name="see-also"></a>Consulte também
[Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor](choosing-core-framework-server.md)   
[.NET Standard](net-standard.md)  
[Guia do .NET Core](../core/index.md)  
[Guia do .NET Framework](../framework/index.md)  
[Guia do C#](../csharp/index.md)  
[Guia do F#](../fsharp/index.md)  
[Guia do VB.NET](../visual-basic/index.md)  

