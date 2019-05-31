---
title: Depurando árvores de expressão no Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 93b1b660181cd81c31055f5d30d43e535171bb55
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195982"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Depurando árvores de expressão no Visual Studio (C#)
Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão. Para obter uma visão geral da estrutura de árvore de expressão, você pode usar a propriedade `DebugView`, que representa as árvores de expressão [usando uma sintaxe especial](debugview-syntax.md). (Observe que `DebugView` está disponível apenas no modo de depuração.)  

![DebugView da árvore de expressão no depurador do Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Uma vez que `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de Texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de Texto** do ícone de lupa ao lado do rótulo `DebugView`.

 ![Visualizador de Texto aplicado aos resultados de 'DebugView'](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão, como:

* As [Expressões Legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença do MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) renderizam a árvore de expressão com código em C#:

  ![Visualizador de Expressões Legíveis](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* O [Visualizador de Árvore de Expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença do MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fornece uma exibição gráfica da árvore de expressão, suas propriedades e os objetos relacionados:

  ![Visualizador de ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Para abrir um visualizador para uma árvore de expressão  
  
1. Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.  
  
     É exibida uma lista de visualizadores disponíveis: 

      ![Abrindo visualizadores do Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Clique no visualizador que você deseja usar.  
  
## <a name="see-also"></a>Consulte também

- [Árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Criar visualizadores personalizados](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Sintaxe do `DebugView`](debugview-syntax.md)
