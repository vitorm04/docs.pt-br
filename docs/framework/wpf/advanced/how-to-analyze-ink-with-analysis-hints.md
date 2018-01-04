---
title: "Como analisar tinta com dicas de análise"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b97f7fe0314b6bf839e4e639e32a48f9261def73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a><span data-ttu-id="706a6-102">Como analisar tinta com dicas de análise</span><span class="sxs-lookup"><span data-stu-id="706a6-102">How to: Analyze Ink with Analysis Hints</span></span>
<span data-ttu-id="706a6-103">Um [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) fornece uma dica para o [InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) ao qual ele está conectado.</span><span class="sxs-lookup"><span data-stu-id="706a6-103">An [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) provides a hint for the [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) to which it is attached.</span></span>  <span data-ttu-id="706a6-104">A dica se aplica a área especificada pelo [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) propriedade o [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) e fornece um contexto extra para o analisador de tinta Melhore a precisão do reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="706a6-104">The hint applies to the area specified by the [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) property of the [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) and provides extra context to the ink analyzer to improve recognition accuracy.</span></span> <span data-ttu-id="706a6-105">O [InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) aplica essas informações de contexto quando analisando a tinta obtida dentro da área de dica.</span><span class="sxs-lookup"><span data-stu-id="706a6-105">The [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) applies this context information when analyzing ink obtained from within the hint's area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="706a6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="706a6-106">Example</span></span>  
 <span data-ttu-id="706a6-107">O exemplo a seguir é um aplicativo que usa vários [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objetos em um formulário que aceita entrada à tinta.</span><span class="sxs-lookup"><span data-stu-id="706a6-107">The following example is an application that uses multiple [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) objects on a form that accepts ink input.</span></span> <span data-ttu-id="706a6-108">O aplicativo usa o [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) propriedade para fornecer informações de contexto para cada entrada no formulário.</span><span class="sxs-lookup"><span data-stu-id="706a6-108">The application uses the [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) property to provide context information for each entry on the form.</span></span>  <span data-ttu-id="706a6-109">O aplicativo usa a análise em segundo plano para analisar a tinta e limpa o formulário de tinta todos os cinco segundos depois que o usuário interrompe a adição de tinta.</span><span class="sxs-lookup"><span data-stu-id="706a6-109">The application uses background analysis to analyze the ink and clears the form of all ink five seconds after the user stops adding ink.</span></span>  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
