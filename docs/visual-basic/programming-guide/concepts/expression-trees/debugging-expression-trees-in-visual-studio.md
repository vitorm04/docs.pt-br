---
title: Depurando árvores de expressão no Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2addba2654067eaaf6c621c927e0992308879ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="0bced-102">Depurando árvores de expressão no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bced-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="0bced-103">Ao depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="0bced-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="0bced-104">Para obter uma rápida visão geral da estrutura da árvore de expressão, você pode usar a propriedade `DebugView`, que está disponível apenas no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="0bced-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="0bced-105">Para obter mais informações sobre depuração, consulte [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="0bced-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="0bced-106">Para melhor representar o conteúdo das árvores de expressão, a propriedade `DebugView` usa os visualizadores do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0bced-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="0bced-107">Para obter mais informações, consulte [Criar visualizadores personalizados](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="0bced-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="0bced-108">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="0bced-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="0bced-109">Clique no ícone de lupa que aparece ao lado da propriedade `DebugView` de uma árvore de expressão em **DataTips**, uma janela **Inspeção**, a janela **Autos** ou a janela **Locais**.</span><span class="sxs-lookup"><span data-stu-id="0bced-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="0bced-110">Uma lista de visualizadores é exibida.</span><span class="sxs-lookup"><span data-stu-id="0bced-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="0bced-111">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="0bced-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="0bced-112">Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="0bced-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="0bced-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="0bced-113">ParameterExpressions</span></span>  
 <span data-ttu-id="0bced-114">Os nomes de variáveis <xref:System.Linq.Expressions.ParameterExpression> são exibidos com o símbolo "$" no início.</span><span class="sxs-lookup"><span data-stu-id="0bced-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="0bced-115">Se um parâmetro não tiver um nome, será atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="0bced-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="0bced-117">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="0bced-118">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="0bced-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="0bced-119">ConstantExpressions</span></span>  
 <span data-ttu-id="0bced-120">Para objetos <xref:System.Linq.Expressions.ConstantExpression> que representam valores inteiros, cadeias de caracteres e `null`, o valor da constante é exibido.</span><span class="sxs-lookup"><span data-stu-id="0bced-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="0bced-122">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="0bced-123">10</span><span class="sxs-lookup"><span data-stu-id="0bced-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="0bced-124">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="0bced-125">10D</span><span class="sxs-lookup"><span data-stu-id="0bced-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="0bced-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="0bced-126">BlockExpression</span></span>  
 <span data-ttu-id="0bced-127">Se o tipo de um objeto <xref:System.Linq.Expressions.BlockExpression> difere do tipo da última expressão no bloco, o tipo é exibido na propriedade `DebugInfo` entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="0bced-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="0bced-128">Caso contrário, o tipo do objeto <xref:System.Linq.Expressions.BlockExpression> não é exibido.</span><span class="sxs-lookup"><span data-stu-id="0bced-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="0bced-130">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="0bced-131">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="0bced-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="0bced-132">LambdaExpression</span></span>  
 <span data-ttu-id="0bced-133">Objetos <xref:System.Linq.Expressions.LambdaExpression> são exibidos junto com seus tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="0bced-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="0bced-134">Se uma expressão lambda não tiver um nome, será atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="0bced-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-135">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="0bced-136">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="0bced-137">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="0bced-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="0bced-138">LabelExpression</span></span>  
 <span data-ttu-id="0bced-139">Se você especificar um valor padrão para o objeto <xref:System.Linq.Expressions.LabelExpression>, esse valor será exibido antes do objeto <xref:System.Linq.Expressions.LabelTarget>.</span><span class="sxs-lookup"><span data-stu-id="0bced-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="0bced-140">O token `.Label` indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="0bced-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="0bced-141">O token `.LabelTarget` indica o local para o qual o destino deve saltar.</span><span class="sxs-lookup"><span data-stu-id="0bced-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="0bced-142">Se um rótulo não tiver um nome, será atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="0bced-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="0bced-144">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="0bced-145">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="0bced-146">Operadores verificados</span><span class="sxs-lookup"><span data-stu-id="0bced-146">Checked Operators</span></span>  
 <span data-ttu-id="0bced-147">Os operadores verificados são exibidos com o símbolo "#" na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="0bced-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="0bced-148">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="0bced-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="0bced-149">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0bced-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="0bced-150">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="0bced-151">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0bced-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="0bced-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bced-152">See Also</span></span>  
 [<span data-ttu-id="0bced-153">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bced-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="0bced-154">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0bced-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="0bced-155">Criar visualizadores personalizados</span><span class="sxs-lookup"><span data-stu-id="0bced-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
