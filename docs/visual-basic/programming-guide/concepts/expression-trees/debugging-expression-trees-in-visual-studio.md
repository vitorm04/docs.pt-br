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
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="190cd-102">Depurando árvores de expressão no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190cd-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="190cd-103">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="190cd-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="190cd-104">Para obter uma visão geral da estrutura de árvore de expressão, você pode usar o `DebugView` propriedade, que representa as árvores de expressão usando uma sintaxe especial descrita [abaixo](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="190cd-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="190cd-105">(Observe que `DebugView` está disponível apenas no modo de depuração.)</span><span class="sxs-lookup"><span data-stu-id="190cd-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView de árvore de expressão no depurador do Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="190cd-107">Pois `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de texto** de lupa ícone ao lado de `DebugView` rótulo.</span><span class="sxs-lookup"><span data-stu-id="190cd-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Visualizador de texto aplicado aos resultados de 'DebugView'](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="190cd-109">Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão:</span><span class="sxs-lookup"><span data-stu-id="190cd-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="190cd-110">[Expressões legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), processa a árvore de expressão como C# código:</span><span class="sxs-lookup"><span data-stu-id="190cd-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Visualizador de expressões legível](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="190cd-112">[Visualizador de árvore de expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), fornece uma exibição gráfica de árvore de expressão, suas propriedades e objetos relacionados; e pode processar a árvore de expressão usando o código do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="190cd-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![Visualizador de ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="190cd-114">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="190cd-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="190cd-115">Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, um **inspeção** janela, o **Autos** janela, ou o **locais** janela.</span><span class="sxs-lookup"><span data-stu-id="190cd-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="190cd-116">É exibida uma lista de visualizadores disponíveis.:</span><span class="sxs-lookup"><span data-stu-id="190cd-116">A list of available visualizers is displayed.:</span></span> 

      ![Visualizadores de abertura do Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="190cd-118">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="190cd-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="190cd-119">`DebugView` Sintaxe</span><span class="sxs-lookup"><span data-stu-id="190cd-119">`DebugView` syntax</span></span> 

<span data-ttu-id="190cd-120">Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="190cd-120">Each expression type is displayed in the visualizer as described in the following sections.</span></span>

## <a name="parameterexpressions"></a><span data-ttu-id="190cd-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="190cd-121">ParameterExpressions</span></span>

<span data-ttu-id="190cd-122">Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com o símbolo "$" no início.</span><span class="sxs-lookup"><span data-stu-id="190cd-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="190cd-123">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="190cd-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-124">Examples</span></span>

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    <span data-ttu-id="190cd-125">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-125">`DebugView` property</span></span>

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    <span data-ttu-id="190cd-126">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-126">`DebugView` property</span></span>

    `$var1`

## <a name="constantexpressions"></a><span data-ttu-id="190cd-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="190cd-127">ConstantExpressions</span></span>
 <span data-ttu-id="190cd-128">Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="190cd-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-129">Examples</span></span>

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="190cd-130">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-130">`DebugView` property</span></span>

    <span data-ttu-id="190cd-131">10</span><span class="sxs-lookup"><span data-stu-id="190cd-131">10</span></span>

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="190cd-132">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-132">`DebugView` property</span></span>

    <span data-ttu-id="190cd-133">10D</span><span class="sxs-lookup"><span data-stu-id="190cd-133">10D</span></span>

## <a name="blockexpression"></a><span data-ttu-id="190cd-134">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="190cd-134">BlockExpression</span></span>

<span data-ttu-id="190cd-135">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="190cd-135">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="190cd-136">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="190cd-136">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-137">Examples</span></span>

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    <span data-ttu-id="190cd-138">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-138">`DebugView` property</span></span>

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    <span data-ttu-id="190cd-139">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-139">`DebugView` property</span></span>

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a><span data-ttu-id="190cd-140">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="190cd-140">LambdaExpression</span></span>

<span data-ttu-id="190cd-141">Objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="190cd-141"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="190cd-142">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="190cd-142">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-143">Examples</span></span>

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    <span data-ttu-id="190cd-144">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-144">`DebugView` property</span></span>

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    <span data-ttu-id="190cd-145">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-145">`DebugView` property</span></span>

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a><span data-ttu-id="190cd-146">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="190cd-146">LabelExpression</span></span>

<span data-ttu-id="190cd-147">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="190cd-147">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="190cd-148">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="190cd-148">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="190cd-149">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="190cd-149">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="190cd-150">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="190cd-150">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-151">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-151">Examples</span></span>

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    <span data-ttu-id="190cd-152">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-152">`DebugView` property</span></span>

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

    <span data-ttu-id="190cd-153">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-153">`DebugView` property</span></span>

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a><span data-ttu-id="190cd-154">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="190cd-154">Checked Operators</span></span>

<span data-ttu-id="190cd-155">Os operadores verificados são exibidos com o símbolo "#" na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="190cd-155">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="190cd-156">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="190cd-156">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="190cd-157">Exemplos</span><span class="sxs-lookup"><span data-stu-id="190cd-157">Examples</span></span>

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    <span data-ttu-id="190cd-158">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-158">`DebugView` property</span></span>

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    <span data-ttu-id="190cd-159">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="190cd-159">`DebugView` property</span></span>

    `#(System.Int32)10D`

## <a name="see-also"></a><span data-ttu-id="190cd-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="190cd-160">See also</span></span>

- [<span data-ttu-id="190cd-161">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="190cd-161">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="190cd-162">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="190cd-162">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="190cd-163">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="190cd-163">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
