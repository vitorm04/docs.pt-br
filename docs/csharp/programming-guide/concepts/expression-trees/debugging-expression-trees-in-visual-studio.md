---
title: Depurando árvores de expressão no Visual Studio (C#)
description: Saiba mais sobre a propriedade DebugView no Visual Studio. Consulte como usar essa propriedade para analisar a estrutura e o conteúdo das árvores de expressão.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5dcf56f96ecdbfdc3f4cb171fdb30b96456b59c9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154126"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="84da8-104">Depurando árvores de expressão no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="84da8-104">Debugging Expression Trees in Visual Studio (C#)</span></span>

<span data-ttu-id="84da8-105">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="84da8-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="84da8-106">Para obter uma visão geral da estrutura de árvore de expressão, você pode usar a propriedade `DebugView`, que representa as árvores de expressão [usando uma sintaxe especial](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="84da8-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="84da8-107">(Observe que `DebugView` está disponível apenas no modo de depuração.)</span><span class="sxs-lookup"><span data-stu-id="84da8-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Captura de tela da DebugView de uma árvore de expressão dentro do depurador do VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="84da8-109">Uma vez que `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de Texto interno](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de Texto** do ícone de lupa ao lado do rótulo `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="84da8-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Captura de tela do Visualizador de texto aplicado aos resultados de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="84da8-111">Como alternativa, você pode instalar e usar [um visualizador personalizado](/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão, como:</span><span class="sxs-lookup"><span data-stu-id="84da8-111">Alternatively, you can install and use [a custom visualizer](/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="84da8-112">As [expressões legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderiza a árvore de expressão como código passíveis C#, com várias opções de renderização:</span><span class="sxs-lookup"><span data-stu-id="84da8-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Captura de tela do Visualizador de expressões legíveis.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="84da8-114">O [Visualizador de árvore de expressões](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licença MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) fornece uma exibição de árvore da árvore de expressão e seus nós individuais:</span><span class="sxs-lookup"><span data-stu-id="84da8-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Captura de tela do Visualizador de árvore de expressão.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="84da8-116">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="84da8-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="84da8-117">Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.</span><span class="sxs-lookup"><span data-stu-id="84da8-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="84da8-118">É exibida uma lista de visualizadores disponíveis:</span><span class="sxs-lookup"><span data-stu-id="84da8-118">A list of available visualizers is displayed.:</span></span>

    ![Captura de tela mostrando a abertura de visualizadores do Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="84da8-120">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="84da8-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84da8-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="84da8-121">See also</span></span>

- [<span data-ttu-id="84da8-122">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="84da8-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="84da8-123">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="84da8-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="84da8-124">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="84da8-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="84da8-125">`DebugView` sintaxe</span><span class="sxs-lookup"><span data-stu-id="84da8-125">`DebugView` syntax</span></span>](debugview-syntax.md)
