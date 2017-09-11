---
title: "Depurando árvores de expressão no Visual Studio (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84de749afad6abb748d0622561f8ee7cd399ed54
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="91daf-102">Depurando árvores de expressão no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91daf-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="91daf-103">Quando você depurar seus aplicativos, você pode analisar a estrutura e o conteúdo das árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="91daf-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="91daf-104">Para obter uma visão geral da estrutura de árvore de expressão, você pode usar o `DebugView` propriedade, que está disponível apenas no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="91daf-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="91daf-105">Para obter mais informações sobre depuração, consulte [depuração no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="91daf-105">For more information about debugging, see [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="91daf-106">Para melhor representar o conteúdo das árvores de expressão, o `DebugView` propriedade usa os visualizadores do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91daf-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="91daf-107">Para obter mais informações, consulte [criar os visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="91daf-107">For more information, see [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="91daf-108">Para abrir um visualizador para uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="91daf-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="91daf-109">Clique no ícone de lupa que aparece ao lado de `DebugView` propriedade de uma árvore de expressão em **DataTips**, um **inspeção** janela, o **Autos** janela, ou o **locais** janela.</span><span class="sxs-lookup"><span data-stu-id="91daf-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="91daf-110">Uma lista de visualizadores é exibida.</span><span class="sxs-lookup"><span data-stu-id="91daf-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="91daf-111">Clique no visualizador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="91daf-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="91daf-112">Cada tipo de expressão é exibido no visualizador, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="91daf-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="91daf-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="91daf-113">ParameterExpressions</span></span>  
 <span data-ttu-id="91daf-114"><xref:System.Linq.Expressions.ParameterExpression>nomes de variáveis são exibidos com um símbolo "$" no início.</xref:System.Linq.Expressions.ParameterExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="91daf-115">Se um parâmetro não tem um nome, ele é atribuído um nome gerado automaticamente, como `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="91daf-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="91daf-117">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="91daf-118">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="91daf-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="91daf-119">ConstantExpressions</span></span>  
 <span data-ttu-id="91daf-120">Para <xref:System.Linq.Expressions.ConstantExpression>objetos que representam valores inteiros, cadeias de caracteres, e `null`, o valor da constante é exibido.</xref:System.Linq.Expressions.ConstantExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="91daf-122">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="91daf-123">10</span><span class="sxs-lookup"><span data-stu-id="91daf-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="91daf-124">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="91daf-125">10D</span><span class="sxs-lookup"><span data-stu-id="91daf-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="91daf-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="91daf-126">BlockExpression</span></span>  
 <span data-ttu-id="91daf-127">Se o tipo de uma <xref:System.Linq.Expressions.BlockExpression>objeto difere do tipo da última expressão no bloco, o tipo é exibido no `DebugInfo` propriedade entre colchetes angulares (\< e >).</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="91daf-128">Caso contrário, o tipo do <xref:System.Linq.Expressions.BlockExpression>objeto não é exibido.</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="91daf-130">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="91daf-131">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="91daf-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="91daf-132">LambdaExpression</span></span>  
 <span data-ttu-id="91daf-133"><xref:System.Linq.Expressions.LambdaExpression>objetos são exibidos junto com os tipos de delegado.</xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="91daf-134">Se uma expressão lambda não tem um nome, ele é atribuído um nome gerado automaticamente, como `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="91daf-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-135">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="91daf-136">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="91daf-137">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="91daf-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="91daf-138">LabelExpression</span></span>  
 <span data-ttu-id="91daf-139">Se você especificar um valor padrão para o <xref:System.Linq.Expressions.LabelExpression>do objeto, esse valor é exibido antes do <xref:System.Linq.Expressions.LabelTarget>objeto.</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression></span><span class="sxs-lookup"><span data-stu-id="91daf-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="91daf-140">O `.Label` token indica o início do rótulo.</span><span class="sxs-lookup"><span data-stu-id="91daf-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="91daf-141">O `.LabelTarget` token indica o destino de saltar para o destino.</span><span class="sxs-lookup"><span data-stu-id="91daf-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="91daf-142">Se um rótulo não tem um nome, ele é atribuído um nome gerado automaticamente, como `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="91daf-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="91daf-144">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-144">`DebugView` property</span></span>  
  
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
  
     <span data-ttu-id="91daf-145">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="91daf-146">Operadores de verificação</span><span class="sxs-lookup"><span data-stu-id="91daf-146">Checked Operators</span></span>  
 <span data-ttu-id="91daf-147">Operadores de verificação é exibido com o símbolo "#" na frente do operador.</span><span class="sxs-lookup"><span data-stu-id="91daf-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="91daf-148">Por exemplo, o operador de adição verificado é exibido como `#+`.</span><span class="sxs-lookup"><span data-stu-id="91daf-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="91daf-149">Exemplos</span><span class="sxs-lookup"><span data-stu-id="91daf-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="91daf-150">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="91daf-151">Propriedade `DebugView`</span><span class="sxs-lookup"><span data-stu-id="91daf-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="91daf-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91daf-152">See Also</span></span>  
 <span data-ttu-id="91daf-153">[Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="91daf-153">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="91daf-154"> [Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="91daf-154"> [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="91daf-155"> [Criar visualizadores personalizados](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span><span class="sxs-lookup"><span data-stu-id="91daf-155"> [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span></span>
