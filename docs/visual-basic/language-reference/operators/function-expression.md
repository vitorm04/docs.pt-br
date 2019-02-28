---
title: Expressão de função (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 6cecc7fc2356a265ca4a3d57c837298ec33efc60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965828"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="39c97-102">Expressão de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39c97-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="39c97-103">Declara os parâmetros e o código que define uma expressão lambda de função.</span><span class="sxs-lookup"><span data-stu-id="39c97-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39c97-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="39c97-105">Partes</span><span class="sxs-lookup"><span data-stu-id="39c97-105">Parts</span></span>  
  
|<span data-ttu-id="39c97-106">Termo</span><span class="sxs-lookup"><span data-stu-id="39c97-106">Term</span></span>|<span data-ttu-id="39c97-107">Definição</span><span class="sxs-lookup"><span data-stu-id="39c97-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="39c97-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39c97-108">Optional.</span></span> <span data-ttu-id="39c97-109">Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="39c97-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="39c97-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="39c97-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="39c97-111">Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="39c97-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="39c97-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="39c97-112">Required.</span></span> <span data-ttu-id="39c97-113">Uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="39c97-113">A single expression.</span></span> <span data-ttu-id="39c97-114">O tipo da expressão é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="39c97-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="39c97-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="39c97-115">Required.</span></span> <span data-ttu-id="39c97-116">Uma lista de instruções que retorna um valor usando o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="39c97-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="39c97-117">(Consulte [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="39c97-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c97-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="39c97-118">Remarks</span></span>  
 <span data-ttu-id="39c97-119">Um *expressão lambda* é uma função sem um nome que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="39c97-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="39c97-120">Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="39c97-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="39c97-121">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="39c97-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="39c97-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="39c97-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="39c97-123">A sintaxe de uma expressão lambda lembra a de uma função padrão.</span><span class="sxs-lookup"><span data-stu-id="39c97-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="39c97-124">As diferenças são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="39c97-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="39c97-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="39c97-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="39c97-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="39c97-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="39c97-127">Expressões lambda não usam um `As` cláusula para designar o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="39c97-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="39c97-128">Em vez disso, o tipo é inferido do valor que avalia o corpo de uma expressão lambda de linha única, ou o valor retornado de uma expressão lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="39c97-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="39c97-129">Por exemplo, se o corpo de uma expressão lambda de linha única estiver `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39c97-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="39c97-130">O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="39c97-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="39c97-131">O corpo pode consistir de uma chamada para um procedimento function, mas não uma chamada para um procedimento sub.</span><span class="sxs-lookup"><span data-stu-id="39c97-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="39c97-132">Ou todos os parâmetros devem ter especificado devem ser deduzidos a tipos de dados ou todos.</span><span class="sxs-lookup"><span data-stu-id="39c97-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="39c97-133">Parâmetros opcionais e Paramarray não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="39c97-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="39c97-134">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="39c97-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39c97-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39c97-135">Example</span></span>  
 <span data-ttu-id="39c97-136">Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples.</span><span class="sxs-lookup"><span data-stu-id="39c97-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="39c97-137">O primeiro usa um `Dim` para fornecer um nome para a função.</span><span class="sxs-lookup"><span data-stu-id="39c97-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="39c97-138">Para chamar a função, você envia um valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="39c97-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="39c97-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39c97-139">Example</span></span>  
 <span data-ttu-id="39c97-140">Como alternativa, você pode declarar e executar a função ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="39c97-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="39c97-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39c97-141">Example</span></span>  
 <span data-ttu-id="39c97-142">A seguir está um exemplo de uma expressão lambda que aumenta seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="39c97-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="39c97-143">O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="39c97-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="39c97-144">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="39c97-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="39c97-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39c97-145">Example</span></span>  
 <span data-ttu-id="39c97-146">Expressões lambda são a base de muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]e pode ser usada explicitamente em consultas com base em método.</span><span class="sxs-lookup"><span data-stu-id="39c97-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="39c97-147">O exemplo a seguir mostra um típico [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta, seguido pela tradução da consulta em formato de método.</span><span class="sxs-lookup"><span data-stu-id="39c97-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="39c97-148">Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="39c97-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="39c97-149">Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="39c97-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c97-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39c97-150">See also</span></span>
- [<span data-ttu-id="39c97-151">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="39c97-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="39c97-152">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="39c97-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="39c97-153">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="39c97-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="39c97-154">Instruções</span><span class="sxs-lookup"><span data-stu-id="39c97-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="39c97-155">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="39c97-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="39c97-156">Expressões Boolianas</span><span class="sxs-lookup"><span data-stu-id="39c97-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="39c97-157">Operador If</span><span class="sxs-lookup"><span data-stu-id="39c97-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="39c97-158">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="39c97-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
