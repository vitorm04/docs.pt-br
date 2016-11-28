---
title: O .NET Portability Analyzer | .NET
description: "Saiba como usar a ferramenta .NET Portability Analyzer para avaliar a portabilidade do seu código entre várias plataformas .NET."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
manager: wpickett
ms.date: 07/05/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
translationtype: Human Translation
ms.sourcegitcommit: 8599be1eadcd6f005ef344bf173e8c06fce80725
ms.openlocfilehash: 9e35fd4dff15cec688ee11f98682eb7cb96e9403

---

# <a name="the-net-portability-analyzer"></a>O .NET Portability Analyzer

Deseja tornar suas bibliotecas multiplataforma? Deseja ver a quantidade de trabalho necessário para tornar seu aplicativo compatível com outras plataformas do .NET? O [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) é uma ferramenta que fornece um relatório detalhado sobre a flexibilidade do seu programa nas plataformas do .NET mediante a análise de assemblies. O Portability Analyzer é oferecido como uma extensão do Visual Studio e um aplicativo de console.

## <a name="new-targets"></a>Novos destinos

*   [.NET Core](https://www.dotnetfoundation.org/netcore): tem um design modular, utiliza lado a lado e está direcionado a cenários de plataforma cruzada. O lado a lado permite adotar novas versões do .NET Core sem interromper outros aplicativos.
*   [ASP.NET Core](https://www.dotnetfoundation.org/aspnet-core): é uma estrutura Web moderna criada no .NET Core, proporcionando os mesmos benefícios aos desenvolvedores.
*   [.NET Native](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): melhore o desempenho dos seus aplicativos da Windows Store executados em computadores x64 e ARM usando a compilação estática do .NET Native.

## <a name="how-to-use-portability-analyzer"></a>Como usar o Portability Analyzer

Para começar a usar o .NET Portability Analyzer, baixe e instale a extensão da [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=507467). É possível configurá-lo no Visual Studio via **Ferramentas** > **Opções** > **.NET Portability Analyzer** e selecionar suas Plataformas de Destino. Por enquanto, use o ASP.NET Core como proxy para todas as plataformas baseadas em .NET Core (por exemplo, [aplicativos UAP Windows 10 do .NET](http://blogs.windows.com/buildingapps/2015/03/02/a-first-look-at-the-windows-10-universal-app-platform/)).

![Captura de tela de portabilidade](./media/portability-analyzer/portability-screenshot.png)

Para analisar todo o projeto, clique com o botão direito do mouse em seu projeto no **Gerenciador de Soluções** e selecione **Analisar** > **Analisar Portabilidade do Assembly**. Caso contrário, acesse o menu **Analyze** e selecione **Analisar Portabilidade do Assembly**. Em seguida, selecione o executável do seu projeto ou DLL.

![Gerenciador de Soluções de Portabilidade](./media/portability-analyzer/portability-solution-explorer.png)

Depois de executar a análise, você verá o relatório de portabilidade do .NET. Somente tipos que não tem suporte em uma plataforma de destino serão exibidos na lista; você pode examinar as recomendações na guia **Mensagens** em **Lista de Erros**. Também é possível saltar diretamente para áreas de problemas na guia **Mensagens**.

![Relatório de portabilidade](./media/portability-analyzer/portability-report.png)

Não quer usar o Visual Studio? Também é possível usar o Portability Analyzer no prompt de comando. Basta baixar o [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).

*   Digite o seguinte comando para analisar o diretório atual: `\...\ApiPort.exe .`
*   Para analisar uma lista específica de arquivos. dll, digite o seguinte comando: `\...\ApiPort.exe first.dll second.dll third.dll`

O relatório de portabilidade do .NET será salvo como um arquivo Excel (*.xlsx*) no seu diretório atual. A guia **Details** na pasta de trabalho do Excel conterá mais informações.

Para obter mais informações sobre o .NET Portability Analyzer, consulte o artigo [Aproveitando código existente entre plataformas .NET](https://blogs.msdn.microsoft.com/dotnet/2014/08/06/leveraging-existing-code-across-net-platforms/), no blog do .NET.



<!--HONumber=Nov16_HO4-->


