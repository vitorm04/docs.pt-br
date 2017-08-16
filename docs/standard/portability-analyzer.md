---
title: O .NET Portability Analyzer | .NET
description: "Saiba como usar a ferramenta .NET Portability Analyzer para avaliar a portabilidade do seu código entre várias plataformas .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
translationtype: Human Translation
ms.sourcegitcommit: 2dcfc9e725a9776e810f23a505e2c6fb157161c4
ms.openlocfilehash: dd14dc23b14e45569f0fdb9a37954b34c4e654d1
ms.lasthandoff: 02/21/2017

---

# <a name="the-net-portability-analyzer"></a>O .NET Portability Analyzer

Deseja tornar suas bibliotecas multiplataforma? Deseja ver a quantidade de trabalho necessário para tornar seu aplicativo compatível com outras plataformas do .NET? O [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) é uma ferramenta que fornece um relatório detalhado sobre a flexibilidade do seu programa nas plataformas do .NET mediante a análise de assemblies. O Analisador de Portabilidade é oferecido como uma Extensão do Visual Studio 2015 e como um aplicativo de console.

## <a name="new-targets"></a>Novos destinos

*   [.NET Core](https://www.dotnetfoundation.org/netcore): tem um design modular, utiliza lado a lado e está direcionado a cenários de plataforma cruzada. O lado a lado permite adotar novas versões do .NET Core sem interromper outros aplicativos.
*   [ASP.NET Core](https://www.dotnetfoundation.org/aspnet-core): é uma estrutura Web moderna criada no .NET Core, proporcionando os mesmos benefícios aos desenvolvedores.
*   [.NET Native](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): melhore o desempenho dos seus aplicativos da Windows Store executados em computadores x64 e ARM usando a compilação estática do .NET Native.

## <a name="how-to-use-portability-analyzer"></a>Como usar o Portability Analyzer

Para começar a usar o .NET Portability Analyzer, baixe e instale a extensão da [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=507467). É possível configurá-lo no Visual Studio por meio de **Analisar** > **Configurações do Analisador de Portabilidade** e selecionar as Plataformas de Destino.

![Captura de tela de portabilidade](./media/portability-analyzer/portability-screenshot.png)

Para analisar todo o projeto, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e selecione **Analisar Portabilidade do Assembly**. Caso contrário, acesse o menu **Analyze** e selecione **Analisar Portabilidade do Assembly**. Em seguida, selecione o executável do seu projeto ou DLL.

![Gerenciador de Soluções de Portabilidade](./media/portability-analyzer/portability-solution-explorer.png)

Depois de executar a análise, você verá o relatório de portabilidade do .NET. Somente tipos que não tem suporte em uma plataforma de destino serão exibidos na lista; você pode examinar as recomendações na guia **Mensagens** em **Lista de Erros**. Também é possível saltar diretamente para áreas de problemas na guia **Mensagens**.

![Relatório de portabilidade](./media/portability-analyzer/portability-report.png)

Não quer usar o Visual Studio? Também é possível usar o Portability Analyzer no prompt de comando. Basta baixar o [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).

*   Digite o seguinte comando para analisar o diretório atual: `\...\ApiPort.exe analyze -f .`
*   Para analisar uma lista específica de arquivos. dll, digite o seguinte comando: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`

O relatório de portabilidade do .NET será salvo como um arquivo Excel (*.xlsx*) no seu diretório atual. A guia **Details** na pasta de trabalho do Excel conterá mais informações.

Para obter mais informações sobre o Analisador de Portabilidade do .NET, acesse a [documentação do GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) e assista ao vídeo [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Uma análise breve do Analisador de Portabilidade do .NET) do Channel 9.
