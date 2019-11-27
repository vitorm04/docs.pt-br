---
title: Depurar árvores de expressão no Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: ff56a10b6c25f3165066edb727829cc460f3e96c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344733"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Depurando árvores de expressão no Visual Studio (Visual Basic)
Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão. Para obter uma visão geral da estrutura de árvore de expressão, você pode usar a propriedade `DebugView`, que representa as árvores de expressão [usando uma sintaxe especial](debugview-syntax.md). (Observe que `DebugView` está disponível apenas no modo de depuração.)  

![Captura de tela da DebugView da árvore de expressão.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Uma vez que `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de Texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de Texto** do ícone de lupa ao lado do rótulo `DebugView`.

 ![Captura de tela do Visualizador de texto aplicado aos resultados de DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão, como:

- As [Expressões Legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença do MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) renderizam a árvore de expressão com código em C#:

  ![Captura de tela do Visualizador de expressões legíveis.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- O [Visualizador de árvore de expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fornece uma exibição gráfica da árvore de expressão, suas propriedades e objetos relacionados; e pode renderizar a árvore de expressão usando Visual Basic código:

  ![Captura de tela do Visualizador de ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Para abrir um visualizador para uma árvore de expressão  
  
1. Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.  
  
    É exibida uma lista de visualizadores disponíveis: 

    ![Captura de tela do usuário abrindo os visualizadores do Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Clique no visualizador que você deseja usar.  

## <a name="see-also"></a>Consulte também

- [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Depurando no Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Criar visualizadores personalizados](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Sintaxe do `DebugView`](debugview-syntax.md)
