---
title: Depurando árvores de expressão no Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330396"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="cbfdd-102">Depurando árvores de expressão no Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="cbfdd-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="cbfdd-103">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="cbfdd-104">Para obter uma rápida visão geral da estrutura da árvore de expressão, você pode usar a propriedade `DebugView`, que está disponível apenas no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="cbfdd-105">Para obter mais informações sobre depuração, consulte [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cbfdd-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="cbfdd-106">Para melhor representar o conteúdo das árvores de expressão, a propriedade `DebugView` usa os visualizadores do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="cbfdd-107">Para obter mais informações, consulte [Criar visualizadores personalizados](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="cbfdd-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="cbfdd-108">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-108">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="cbfdd-109">Clique no ícone de lupa que aparece ao lado da propriedade `DebugView` de uma árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="cbfdd-110">Uma lista de visualizadores é exibida.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-110">A list of visualizers is displayed.</span></span>  
  
2. <span data-ttu-id="cbfdd-111">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="cbfdd-112">Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="cbfdd-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="cbfdd-113">ParameterExpressions</span></span>  
 <span data-ttu-id="cbfdd-114">Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com o símbolo "$" no início.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="cbfdd-115">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-116">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-117">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-117">Expression</span></span>|<span data-ttu-id="cbfdd-118">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="cbfdd-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="cbfdd-119">ConstantExpressions</span></span>  
 <span data-ttu-id="cbfdd-120">Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="cbfdd-121">Para tipos numéricos que têm sufixos padrão como literais de C#, o sufixo é adicionado ao valor.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="cbfdd-122">A tabela a seguir mostra os sufixos associados com vários tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="cbfdd-123">Tipo</span><span class="sxs-lookup"><span data-stu-id="cbfdd-123">Type</span></span>|<span data-ttu-id="cbfdd-124">Sufixo</span><span class="sxs-lookup"><span data-stu-id="cbfdd-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="cbfdd-125">U</span><span class="sxs-lookup"><span data-stu-id="cbfdd-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="cbfdd-126">L</span><span class="sxs-lookup"><span data-stu-id="cbfdd-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="cbfdd-127">UL</span><span class="sxs-lookup"><span data-stu-id="cbfdd-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="cbfdd-128">D</span><span class="sxs-lookup"><span data-stu-id="cbfdd-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="cbfdd-129">F</span><span class="sxs-lookup"><span data-stu-id="cbfdd-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="cbfdd-130">M</span><span class="sxs-lookup"><span data-stu-id="cbfdd-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-131">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-131">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-132">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-132">Expression</span></span>|<span data-ttu-id="cbfdd-133">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="cbfdd-134">10</span><span class="sxs-lookup"><span data-stu-id="cbfdd-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="cbfdd-135">10D</span><span class="sxs-lookup"><span data-stu-id="cbfdd-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="cbfdd-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="cbfdd-136">BlockExpression</span></span>  
 <span data-ttu-id="cbfdd-137">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="cbfdd-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="cbfdd-138">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-139">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-139">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-140">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-140">Expression</span></span>|<span data-ttu-id="cbfdd-141">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="cbfdd-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="cbfdd-142">LambdaExpression</span></span>  
 <span data-ttu-id="cbfdd-143">Objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="cbfdd-144">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-145">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-146">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-146">Expression</span></span>|<span data-ttu-id="cbfdd-147">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="cbfdd-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="cbfdd-148">LabelExpression</span></span>  
 <span data-ttu-id="cbfdd-149">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="cbfdd-150">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="cbfdd-151">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="cbfdd-152">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-153">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-153">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-154">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-154">Expression</span></span>|<span data-ttu-id="cbfdd-155">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="cbfdd-156">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="cbfdd-156">Checked Operators</span></span>  
 <span data-ttu-id="cbfdd-157">Os operadores verificados são exibidos com o símbolo "#" na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="cbfdd-158">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="cbfdd-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="cbfdd-159">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cbfdd-159">Examples</span></span>  
  
|<span data-ttu-id="cbfdd-160">Expressão</span><span class="sxs-lookup"><span data-stu-id="cbfdd-160">Expression</span></span>|<span data-ttu-id="cbfdd-161">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="cbfdd-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="cbfdd-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbfdd-162">See also</span></span>

- [<span data-ttu-id="cbfdd-163">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="cbfdd-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="cbfdd-164">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cbfdd-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="cbfdd-165">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="cbfdd-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
