---
title: 'Como: Analisar tinta com dicas de análise'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
ms.openlocfilehash: c0071620c406c5907bbb656269729a5aad98eede
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748668"
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a><span data-ttu-id="f0a02-102">Como: Analisar tinta com dicas de análise</span><span class="sxs-lookup"><span data-stu-id="f0a02-102">How to: Analyze Ink with Analysis Hints</span></span>
<span data-ttu-id="f0a02-103">Uma [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) fornece uma dica para o [InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) à qual ela está associada.</span><span class="sxs-lookup"><span data-stu-id="f0a02-103">An [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) provides a hint for the [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) to which it is attached.</span></span>  <span data-ttu-id="f0a02-104">A dica se aplica a área especificada pela [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) propriedade da [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) e fornece um contexto extra para o analisador de tinta Melhore a precisão do reconhecimento.</span><span class="sxs-lookup"><span data-stu-id="f0a02-104">The hint applies to the area specified by the [System.Windows.Ink.ContextNode.Location%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594508(v=vs.90)) property of the [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) and provides extra context to the ink analyzer to improve recognition accuracy.</span></span> <span data-ttu-id="f0a02-105">O [InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) aplica essas informações de contexto quando analisando a tinta obtida dentro da área de dica.</span><span class="sxs-lookup"><span data-stu-id="f0a02-105">The [System.Windows.Ink.InkAnalyzer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms616754(v=vs.90)) applies this context information when analyzing ink obtained from within the hint's area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a02-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0a02-106">Example</span></span>  
 <span data-ttu-id="f0a02-107">O exemplo a seguir é um aplicativo que usa vários [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) objetos em um formulário que aceita entrada de tinta.</span><span class="sxs-lookup"><span data-stu-id="f0a02-107">The following example is an application that uses multiple [System.Windows.Ink.AnalysisHintNode](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms610344(v=vs.90)) objects on a form that accepts ink input.</span></span> <span data-ttu-id="f0a02-108">O aplicativo usa o [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) propriedade para fornecer informações de contexto para cada entrada no formulário.</span><span class="sxs-lookup"><span data-stu-id="f0a02-108">The application uses the [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms594341(v=vs.90)) property to provide context information for each entry on the form.</span></span>  <span data-ttu-id="f0a02-109">O aplicativo usa a análise de plano de fundo para analisar a tinta e limpa o formulário de toda a tinta de cinco segundos após o usuário para a adição de tinta.</span><span class="sxs-lookup"><span data-stu-id="f0a02-109">The application uses background analysis to analyze the ink and clears the form of all ink five seconds after the user stops adding ink.</span></span>  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
