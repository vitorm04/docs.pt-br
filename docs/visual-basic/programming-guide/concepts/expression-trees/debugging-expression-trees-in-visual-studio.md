---
title: Depurando árvores de expressão no Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 51579c74ecbebbfb7da8bf20bef7592980ec437c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320343"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="692a0-102">Depurando árvores de expressão no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="692a0-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="692a0-103">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="692a0-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="692a0-104">Para obter uma visão geral da estrutura de árvore de expressão, você pode usar a propriedade `DebugView`, que representa as árvores de expressão [usando uma sintaxe especial](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="692a0-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="692a0-105">(Observe que `DebugView` está disponível apenas no modo de depuração.)</span><span class="sxs-lookup"><span data-stu-id="692a0-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Captura de tela da DebugView da árvore de expressão.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="692a0-107">Uma vez que `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de Texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de Texto** do ícone de lupa ao lado do rótulo `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="692a0-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Captura de tela do Visualizador de texto aplicado aos resultados de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="692a0-109">Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão, como:</span><span class="sxs-lookup"><span data-stu-id="692a0-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="692a0-110">As [Expressões Legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença do MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) renderizam a árvore de expressão com código em C#:</span><span class="sxs-lookup"><span data-stu-id="692a0-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Captura de tela do Visualizador de expressões legíveis.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="692a0-112">O [Visualizador de árvore de expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fornece uma exibição gráfica da árvore de expressão, suas propriedades e objetos relacionados; e pode renderizar a árvore de expressão usando Visual Basic código:</span><span class="sxs-lookup"><span data-stu-id="692a0-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![Captura de tela do Visualizador de ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="692a0-114">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="692a0-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="692a0-115">Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.</span><span class="sxs-lookup"><span data-stu-id="692a0-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="692a0-116">É exibida uma lista de visualizadores disponíveis:</span><span class="sxs-lookup"><span data-stu-id="692a0-116">A list of available visualizers is displayed.:</span></span> 

    ![Captura de tela do usuário abrindo os visualizadores do Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="692a0-118">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="692a0-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="692a0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="692a0-119">See also</span></span>

- [<span data-ttu-id="692a0-120">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="692a0-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="692a0-121">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="692a0-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="692a0-122">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="692a0-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="692a0-123">Sintaxe do `DebugView`</span><span class="sxs-lookup"><span data-stu-id="692a0-123">`DebugView` syntax</span></span>](debugview-syntax.md)
