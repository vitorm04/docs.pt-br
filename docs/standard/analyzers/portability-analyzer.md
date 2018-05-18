---
title: O .NET Portability Analyzer – .NET
description: Saiba como usar a ferramenta .NET Portability Analyzer para avaliar a portabilidade do seu código entre as várias implementações de .NET, incluindo .NET Core, .NET Standard, UWP e Xamarin.
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: f310e5fe45315dfa41d596c92d9412dc6b3bc125
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="the-net-portability-analyzer"></a>O .NET Portability Analyzer

Deseja tornar suas bibliotecas multiplataforma? Deseja ver a quantidade de trabalho necessário para tornar o aplicativo compatível com outras implementações do .NET e perfis, incluindo .NET Core, .NET Standard, UWP e Xamarin para iOS, Android e Mac? O [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) é uma ferramenta que fornece um relatório detalhado sobre a flexibilidade do seu programa nas implementações do .NET mediante a análise de assemblies. O Portability Analyzer é oferecido como uma extensão do Visual Studio e um aplicativo de console.

## <a name="new-targets"></a>Novos destinos

* [.NET Core](../../core/index.md): tem um design modular, utiliza lado a lado e está direcionado a cenários de plataforma cruzada. O lado a lado permite adotar novas versões do .NET Core sem interromper outros aplicativos.
* [ASP.NET Core](/aspnet/core): é uma estrutura Web moderna criada no .NET Core, proporcionando os mesmos benefícios aos desenvolvedores.
* [Plataforma Universal do Windows](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): melhore o desempenho dos seus Aplicativos da Windows Store executados em computadores x64 e ARM usando a compilação estática do .NET Native. 
* .NET Core + extensões de plataforma: inclui as APIs do .NET Core além de outras APIs do ecossistema do .NET como WCF, ASP.NET Core, FSharp e Azure.
* .NET Standard + extensões de plataforma: inclui as APIs do .NET Standard além de outras do ecossistema do .NET, como WCF, ASP.NET Core, FSharp e Azure.

## <a name="how-to-use-portability-analyzer"></a>Como usar o Portability Analyzer

Para começar a usar o .NET Portability Analyzer, primeiro baixe e instale a extensão do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer). Ele funciona no Visual Studio 2015 e no Visual Studio 2017. É possível configurá-lo no Visual Studio por meio de **Analisar** > **Configurações do Analisador de Portabilidade** e selecionar as Plataformas de Destino.

![Captura de tela de portabilidade](./media/portability-analyzer/portability-screenshot.png)

Para analisar todo o projeto, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Analisar Portabilidade do Assembly**. Caso contrário, acesse o menu **Analyze** e selecione **Analisar Portabilidade do Assembly**. Em seguida, selecione o executável do seu projeto ou DLL.

![Gerenciador de Soluções de Portabilidade](./media/portability-analyzer/portability-solution-explorer.png)

Depois de executar a análise, você verá o relatório de portabilidade do .NET. Somente tipos que não tem suporte em uma plataforma de destino são exibidos na lista; você pode examinar as recomendações na guia **Mensagens** na **Lista de Erros**. Também é possível saltar diretamente para áreas de problemas na guia **Mensagens**.

![Relatório de portabilidade](./media/portability-analyzer/portability-report.png)

Não quer usar o Visual Studio? Também é possível usar o Portability Analyzer no prompt de comando. Basta baixar o [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).

*   Digite o seguinte comando para analisar o diretório atual: `\...\ApiPort.exe analyze -f .`
*   Para analisar uma lista específica de arquivos. dll, digite o seguinte comando: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

O relatório de portabilidade do .NET será salvo como um arquivo Excel (*.xlsx*) no seu diretório atual. A guia **Details** na pasta de trabalho do Excel contém mais informações.

Para obter mais informações sobre o Analisador de Portabilidade do .NET, acesse a [documentação do GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) e assista ao vídeo [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Uma análise breve do Analisador de Portabilidade do .NET) do Channel 9.
