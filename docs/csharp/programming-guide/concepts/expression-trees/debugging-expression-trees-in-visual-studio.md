---
title: Depurando árvores de expressão no Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877122"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="9e8b2-102">Depurando árvores de expressão no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="9e8b2-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="9e8b2-103">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="9e8b2-104">Para obter uma visão geral da estrutura de árvore de expressão, você pode usar a propriedade `DebugView`, que representa as árvores de expressão usando uma sintaxe especial descrita [abaixo](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="9e8b2-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="9e8b2-105">(Observe que `DebugView` está disponível apenas no modo de depuração.)</span><span class="sxs-lookup"><span data-stu-id="9e8b2-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView da árvore de expressão no depurador do Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="9e8b2-107">Uma vez que `DebugView` é uma cadeia de caracteres, você pode usar o [Visualizador de Texto interno](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) para exibi-lo em várias linhas, selecionando **Visualizador de Texto** do ícone de lupa ao lado do rótulo `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Visualizador de Texto aplicado aos resultados de 'DebugView'](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="9e8b2-109">Como alternativa, você pode instalar e usar [um visualizador personalizado](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) para árvores de expressão:</span><span class="sxs-lookup"><span data-stu-id="9e8b2-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="9e8b2-110">As [Expressões Legíveis](https://github.com/agileobjects/ReadableExpressions) ([licença do MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) renderizam a árvore de expressão com código em C#:</span><span class="sxs-lookup"><span data-stu-id="9e8b2-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Visualizador de Expressões Legíveis](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="9e8b2-112">O [Visualizador de Árvore de Expressão](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licença do MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) fornece uma exibição gráfica da árvore de expressão, suas propriedades e os objetos relacionados:</span><span class="sxs-lookup"><span data-stu-id="9e8b2-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Visualizador de ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="9e8b2-114">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="9e8b2-115">Clique no ícone de lupa que aparece ao lado da árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="9e8b2-116">É exibida uma lista de visualizadores disponíveis:</span><span class="sxs-lookup"><span data-stu-id="9e8b2-116">A list of available visualizers is displayed.:</span></span> 

      ![Abrindo visualizadores do Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="9e8b2-118">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="9e8b2-119">Sintaxe de `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-119">`DebugView` syntax</span></span> 

<span data-ttu-id="9e8b2-120">Cada tipo de expressão é exibido pela propriedade `DebugView` conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="9e8b2-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="9e8b2-121">ParameterExpressions</span></span>  
 <span data-ttu-id="9e8b2-122">Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com o símbolo "$" no início.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="9e8b2-123">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-124">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-125">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-125">Expression</span></span>|<span data-ttu-id="9e8b2-126">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="9e8b2-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="9e8b2-127">ConstantExpressions</span></span>  
 <span data-ttu-id="9e8b2-128">Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="9e8b2-129">Para tipos numéricos que têm sufixos padrão como literais de C#, o sufixo é adicionado ao valor.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="9e8b2-130">A tabela a seguir mostra os sufixos associados com vários tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="9e8b2-131">Tipo</span><span class="sxs-lookup"><span data-stu-id="9e8b2-131">Type</span></span>|<span data-ttu-id="9e8b2-132">Sufixo</span><span class="sxs-lookup"><span data-stu-id="9e8b2-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="9e8b2-133">U</span><span class="sxs-lookup"><span data-stu-id="9e8b2-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="9e8b2-134">L</span><span class="sxs-lookup"><span data-stu-id="9e8b2-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="9e8b2-135">UL</span><span class="sxs-lookup"><span data-stu-id="9e8b2-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="9e8b2-136">D</span><span class="sxs-lookup"><span data-stu-id="9e8b2-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="9e8b2-137">F</span><span class="sxs-lookup"><span data-stu-id="9e8b2-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="9e8b2-138">M</span><span class="sxs-lookup"><span data-stu-id="9e8b2-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-139">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-139">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-140">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-140">Expression</span></span>|<span data-ttu-id="9e8b2-141">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="9e8b2-142">10</span><span class="sxs-lookup"><span data-stu-id="9e8b2-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="9e8b2-143">10D</span><span class="sxs-lookup"><span data-stu-id="9e8b2-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="9e8b2-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="9e8b2-144">BlockExpression</span></span>  
 <span data-ttu-id="9e8b2-145">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="9e8b2-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="9e8b2-146">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-147">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-147">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-148">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-148">Expression</span></span>|<span data-ttu-id="9e8b2-149">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="9e8b2-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="9e8b2-150">LambdaExpression</span></span>  
 <span data-ttu-id="9e8b2-151">Objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="9e8b2-152">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-153">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-153">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-154">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-154">Expression</span></span>|<span data-ttu-id="9e8b2-155">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="9e8b2-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="9e8b2-156">LabelExpression</span></span>  
 <span data-ttu-id="9e8b2-157">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="9e8b2-158">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="9e8b2-159">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="9e8b2-160">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-161">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-161">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-162">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-162">Expression</span></span>|<span data-ttu-id="9e8b2-163">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="9e8b2-164">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="9e8b2-164">Checked Operators</span></span>  
 <span data-ttu-id="9e8b2-165">Os operadores verificados são exibidos com o símbolo "#" na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="9e8b2-166">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="9e8b2-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9e8b2-167">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e8b2-167">Examples</span></span>  
  
|<span data-ttu-id="9e8b2-168">Expressão</span><span class="sxs-lookup"><span data-stu-id="9e8b2-168">Expression</span></span>|<span data-ttu-id="9e8b2-169">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="9e8b2-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="9e8b2-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e8b2-170">See also</span></span>

- [<span data-ttu-id="9e8b2-171">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="9e8b2-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="9e8b2-172">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e8b2-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="9e8b2-173">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="9e8b2-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
