---
title: Expressão de função (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183087"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="a405f-102">Expressão de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a405f-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="a405f-103">Declara os parâmetros e o código que define uma expressão lambda de função.</span><span class="sxs-lookup"><span data-stu-id="a405f-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a405f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a405f-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="a405f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a405f-105">Parts</span></span>  
  
|<span data-ttu-id="a405f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a405f-106">Term</span></span>|<span data-ttu-id="a405f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a405f-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="a405f-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a405f-108">Optional.</span></span> <span data-ttu-id="a405f-109">Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="a405f-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="a405f-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="a405f-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="a405f-111">Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="a405f-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="a405f-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a405f-112">Required.</span></span> <span data-ttu-id="a405f-113">Uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="a405f-113">A single expression.</span></span> <span data-ttu-id="a405f-114">O tipo da expressão é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="a405f-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="a405f-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a405f-115">Required.</span></span> <span data-ttu-id="a405f-116">Uma lista de instruções que retorna um valor usando o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="a405f-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="a405f-117">(Consulte [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="a405f-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a405f-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a405f-118">Remarks</span></span>  
 <span data-ttu-id="a405f-119">Um *expressão lambda* é uma função sem um nome que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="a405f-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="a405f-120">Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="a405f-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="a405f-121">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="a405f-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="a405f-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="a405f-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="a405f-123">A sintaxe de uma expressão lambda lembra a de uma função padrão.</span><span class="sxs-lookup"><span data-stu-id="a405f-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="a405f-124">As diferenças são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a405f-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="a405f-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="a405f-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="a405f-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a405f-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="a405f-127">Expressões lambda não usam um `As` cláusula para designar o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="a405f-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="a405f-128">Em vez disso, o tipo é inferido do valor que avalia o corpo de uma expressão lambda de linha única, ou o valor retornado de uma expressão lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="a405f-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="a405f-129">Por exemplo, se o corpo de uma expressão lambda de linha única estiver `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a405f-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="a405f-130">O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="a405f-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="a405f-131">O corpo pode consistir de uma chamada para um procedimento function, mas não uma chamada para um procedimento sub.</span><span class="sxs-lookup"><span data-stu-id="a405f-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="a405f-132">Ou todos os parâmetros devem ter especificado devem ser deduzidos a tipos de dados ou todos.</span><span class="sxs-lookup"><span data-stu-id="a405f-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="a405f-133">Parâmetros opcionais e Paramarray não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="a405f-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="a405f-134">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="a405f-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a405f-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a405f-135">Example</span></span>  
 <span data-ttu-id="a405f-136">Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples.</span><span class="sxs-lookup"><span data-stu-id="a405f-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="a405f-137">O primeiro usa um `Dim` para fornecer um nome para a função.</span><span class="sxs-lookup"><span data-stu-id="a405f-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="a405f-138">Para chamar a função, você envia um valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a405f-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a405f-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a405f-139">Example</span></span>  
 <span data-ttu-id="a405f-140">Como alternativa, você pode declarar e executar a função ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a405f-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="a405f-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a405f-141">Example</span></span>  
 <span data-ttu-id="a405f-142">A seguir está um exemplo de uma expressão lambda que aumenta seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="a405f-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="a405f-143">O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="a405f-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="a405f-144">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a405f-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="a405f-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a405f-145">Example</span></span>  
 <span data-ttu-id="a405f-146">Expressões lambda são a base de muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]e pode ser usada explicitamente em consultas com base em método.</span><span class="sxs-lookup"><span data-stu-id="a405f-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="a405f-147">O exemplo a seguir mostra um típico [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta, seguido pela tradução da consulta em formato de método.</span><span class="sxs-lookup"><span data-stu-id="a405f-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="a405f-148">Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="a405f-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="a405f-149">Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a405f-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a405f-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a405f-150">See Also</span></span>  
 [<span data-ttu-id="a405f-151">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a405f-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="a405f-152">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="a405f-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="a405f-153">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="a405f-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="a405f-154">Instruções</span><span class="sxs-lookup"><span data-stu-id="a405f-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="a405f-155">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="a405f-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="a405f-156">Expressões Boolianas</span><span class="sxs-lookup"><span data-stu-id="a405f-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="a405f-157">Operador If</span><span class="sxs-lookup"><span data-stu-id="a405f-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="a405f-158">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="a405f-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
