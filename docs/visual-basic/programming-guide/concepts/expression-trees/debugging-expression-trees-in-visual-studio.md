---
title: Depurando árvores de expressão no Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879813"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Depurando árvores de expressão no Visual Studio (Visual Basic)
Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão. Para obter uma visão geral da estrutura de árvore de expressão, você pode usar o `DebugView` propriedade, que representa as árvores de expressão usando uma sintaxe especial descrita [abaixo](#debugview-syntax). (Observe que `DebugView` está disponível apenas no modo de depuração.)  

![DebugView de árvore de expressão no depurador do Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Pois `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de texto** de lupa ícone ao lado de `DebugView` rótulo.

 ![Visualizador de texto aplicado aos resultados de 'DebugView'](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão:

* [Expressões legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), processa a árvore de expressão como C# código:

  ![Visualizador de expressões legível](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Visualizador de árvore de expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), fornece uma exibição gráfica de árvore de expressão, suas propriedades e objetos relacionados; e pode processar a árvore de expressão usando o código do Visual Basic:

  ![Visualizador de ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Para abrir um visualizador para uma árvore de expressão  
  
1. Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, um **inspeção** janela, o **Autos** janela, ou o **locais** janela.  
  
     É exibida uma lista de visualizadores disponíveis.: 

      ![Visualizadores de abertura do Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Clique no visualizador que você deseja usar.  

## <a name="debugview-syntax"></a>`DebugView` Sintaxe 

Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.

## <a name="parameterexpressions"></a>ParameterExpressions

Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com o símbolo "$" no início.

Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    Propriedade `DebugView`

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    Propriedade `DebugView`

    `$var1`

## <a name="constantexpressions"></a>ConstantExpressions
 Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    Propriedade `DebugView`

    10

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    Propriedade `DebugView`

    10D

## <a name="blockexpression"></a>BlockExpression

Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >). Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    Propriedade `DebugView`

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    Propriedade `DebugView`

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a>LambdaExpression

Objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com seus tipos delegados.

Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    Propriedade `DebugView`

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    Propriedade `DebugView`

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a>LabelExpression

Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.

O token `.Label` indica o início do rótulo. O token `.LabelTarget` indica o local para o qual o destino deve saltar.

Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    Propriedade `DebugView`

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    Propriedade `DebugView`

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a>Operadores verificados

Os operadores verificados são exibidos com o símbolo "#" na frente do operador. Por exemplo, o operador de adição verificado é exibido como `#+`.

### <a name="examples"></a>Exemplos

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    Propriedade `DebugView`

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    Propriedade `DebugView`

    `#(System.Int32)10D`

## <a name="see-also"></a>Consulte também

- [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Criar visualizadores personalizados](/visualstudio/debugger/create-custom-visualizers-of-data)
