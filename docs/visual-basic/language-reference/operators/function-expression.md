---
title: Expressão de função
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: d14d7c9bc701b5e06c51202c07c3b79832aba7cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331075"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="b98d9-102">Expressão de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b98d9-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="b98d9-103">Declara os parâmetros e o código que definem uma expressão lambda de função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b98d9-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="b98d9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b98d9-105">Parts</span></span>  
  
|<span data-ttu-id="b98d9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b98d9-106">Term</span></span>|<span data-ttu-id="b98d9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b98d9-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="b98d9-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b98d9-108">Optional.</span></span> <span data-ttu-id="b98d9-109">Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="b98d9-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="b98d9-110">Os parênteses devem estar presentes mesmo quando a lista estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="b98d9-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="b98d9-111">Consulte a [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b98d9-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="b98d9-112">Necessária.</span><span class="sxs-lookup"><span data-stu-id="b98d9-112">Required.</span></span> <span data-ttu-id="b98d9-113">Uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="b98d9-113">A single expression.</span></span> <span data-ttu-id="b98d9-114">O tipo da expressão é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="b98d9-115">Necessária.</span><span class="sxs-lookup"><span data-stu-id="b98d9-115">Required.</span></span> <span data-ttu-id="b98d9-116">Uma lista de instruções que retorna um valor usando a instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="b98d9-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="b98d9-117">(Consulte a [instrução return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b98d9-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b98d9-118">Remarks</span></span>  
 <span data-ttu-id="b98d9-119">Uma *expressão lambda* é uma função sem um nome que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="b98d9-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="b98d9-120">Você pode usar uma expressão lambda em qualquer lugar em que possa usar um tipo delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="b98d9-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="b98d9-121">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="b98d9-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="b98d9-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="b98d9-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="b98d9-123">A sintaxe de uma expressão lambda é semelhante à de uma função padrão.</span><span class="sxs-lookup"><span data-stu-id="b98d9-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="b98d9-124">As diferenças são:</span><span class="sxs-lookup"><span data-stu-id="b98d9-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="b98d9-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="b98d9-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="b98d9-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="b98d9-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="b98d9-127">As expressões lambda não usam uma cláusula `As` para designar o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="b98d9-128">Em vez disso, o tipo é inferido do valor que o corpo de uma expressão lambda de linha única avalia ou o valor de retorno de uma expressão lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="b98d9-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="b98d9-129">Por exemplo, se o corpo de uma expressão lambda de linha única for `Where cust.City = "London"`, seu tipo de retorno será `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b98d9-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="b98d9-130">O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="b98d9-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="b98d9-131">O corpo pode consistir em uma chamada para um procedimento Function, mas não uma chamada para um procedimento Sub.</span><span class="sxs-lookup"><span data-stu-id="b98d9-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="b98d9-132">Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="b98d9-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="b98d9-133">Parâmetros optional e ParamArray não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="b98d9-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="b98d9-134">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="b98d9-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b98d9-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b98d9-135">Example</span></span>  
 <span data-ttu-id="b98d9-136">Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples.</span><span class="sxs-lookup"><span data-stu-id="b98d9-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="b98d9-137">O primeiro usa um `Dim` para fornecer um nome para a função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="b98d9-138">Para chamar a função, você envia em um valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b98d9-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b98d9-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b98d9-139">Example</span></span>  
 <span data-ttu-id="b98d9-140">Como alternativa, você pode declarar e executar a função ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b98d9-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b98d9-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b98d9-141">Example</span></span>  
 <span data-ttu-id="b98d9-142">Veja a seguir um exemplo de uma expressão lambda que incrementa seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="b98d9-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="b98d9-143">O exemplo mostra a sintaxe da expressão lambda de linha única e de várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="b98d9-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="b98d9-144">Para obter mais exemplos, consulte [expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b98d9-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b98d9-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b98d9-145">Example</span></span>  
 <span data-ttu-id="b98d9-146">As expressões lambda são a base de muitos dos operadores de consulta no [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]e podem ser usadas explicitamente em consultas baseadas em método.</span><span class="sxs-lookup"><span data-stu-id="b98d9-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="b98d9-147">O exemplo a seguir mostra uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] típica, seguida pela conversão da consulta em formato de método.</span><span class="sxs-lookup"><span data-stu-id="b98d9-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="b98d9-148">Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="b98d9-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="b98d9-149">Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b98d9-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98d9-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b98d9-150">See also</span></span>

- [<span data-ttu-id="b98d9-151">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="b98d9-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b98d9-152">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="b98d9-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="b98d9-153">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="b98d9-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="b98d9-154">Instruções</span><span class="sxs-lookup"><span data-stu-id="b98d9-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="b98d9-155">Comparações de Valor</span><span class="sxs-lookup"><span data-stu-id="b98d9-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="b98d9-156">Expressões Boolianas</span><span class="sxs-lookup"><span data-stu-id="b98d9-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="b98d9-157">Operador If</span><span class="sxs-lookup"><span data-stu-id="b98d9-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="b98d9-158">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="b98d9-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
