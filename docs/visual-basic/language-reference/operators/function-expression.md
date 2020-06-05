---
title: Expressão de Função
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371175"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="83f19-102">Expressão de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83f19-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="83f19-103">Declara os parâmetros e o código que definem uma expressão lambda de função.</span><span class="sxs-lookup"><span data-stu-id="83f19-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83f19-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="83f19-105">Partes</span><span class="sxs-lookup"><span data-stu-id="83f19-105">Parts</span></span>  
  
|<span data-ttu-id="83f19-106">Termo</span><span class="sxs-lookup"><span data-stu-id="83f19-106">Term</span></span>|<span data-ttu-id="83f19-107">Definição</span><span class="sxs-lookup"><span data-stu-id="83f19-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="83f19-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="83f19-108">Optional.</span></span> <span data-ttu-id="83f19-109">Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="83f19-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="83f19-110">Os parênteses devem estar presentes mesmo quando a lista estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="83f19-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="83f19-111">Consulte a [lista de parâmetros](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="83f19-111">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="83f19-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="83f19-112">Required.</span></span> <span data-ttu-id="83f19-113">Uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="83f19-113">A single expression.</span></span> <span data-ttu-id="83f19-114">O tipo da expressão é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="83f19-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="83f19-115">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="83f19-115">Required.</span></span> <span data-ttu-id="83f19-116">Uma lista de instruções que retorna um valor usando a `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="83f19-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="83f19-117">(Consulte a [instrução return](../statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="83f19-117">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f19-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="83f19-118">Remarks</span></span>  
 <span data-ttu-id="83f19-119">Uma *expressão lambda* é uma função sem um nome que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="83f19-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="83f19-120">Você pode usar uma expressão lambda em qualquer lugar em que possa usar um tipo delegado, exceto como um argumento para `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="83f19-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="83f19-121">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [instrução delegate](../statements/delegate-statement.md) e [conversão de delegado reduzida](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="83f19-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="83f19-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="83f19-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="83f19-123">A sintaxe de uma expressão lambda é semelhante à de uma função padrão.</span><span class="sxs-lookup"><span data-stu-id="83f19-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="83f19-124">As diferenças são:</span><span class="sxs-lookup"><span data-stu-id="83f19-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="83f19-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="83f19-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="83f19-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="83f19-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="83f19-127">As expressões lambda não usam uma `As` cláusula para designar o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="83f19-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="83f19-128">Em vez disso, o tipo é inferido do valor que o corpo de uma expressão lambda de linha única avalia ou o valor de retorno de uma expressão lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="83f19-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="83f19-129">Por exemplo, se o corpo de uma expressão lambda de linha única for `Where cust.City = "London"` , seu tipo de retorno será `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="83f19-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="83f19-130">O corpo de uma expressão lambda de linha única deve ser uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="83f19-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="83f19-131">O corpo pode consistir em uma chamada para um procedimento Function, mas não uma chamada para um procedimento Sub.</span><span class="sxs-lookup"><span data-stu-id="83f19-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="83f19-132">Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="83f19-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="83f19-133">Parâmetros optional e ParamArray não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="83f19-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="83f19-134">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="83f19-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f19-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f19-135">Example</span></span>  
 <span data-ttu-id="83f19-136">Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples.</span><span class="sxs-lookup"><span data-stu-id="83f19-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="83f19-137">O primeiro usa um `Dim` para fornecer um nome para a função.</span><span class="sxs-lookup"><span data-stu-id="83f19-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="83f19-138">Para chamar a função, você envia em um valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="83f19-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="83f19-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f19-139">Example</span></span>  
 <span data-ttu-id="83f19-140">Como alternativa, você pode declarar e executar a função ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="83f19-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="83f19-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f19-141">Example</span></span>  
 <span data-ttu-id="83f19-142">Veja a seguir um exemplo de uma expressão lambda que incrementa seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="83f19-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="83f19-143">O exemplo mostra a sintaxe da expressão lambda de linha única e de várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="83f19-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="83f19-144">Para obter mais exemplos, consulte [expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="83f19-144">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="83f19-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f19-145">Example</span></span>  
 <span data-ttu-id="83f19-146">As expressões lambda são a base de muitos dos operadores de consulta em LINQ (consulta integrada à linguagem) e podem ser usadas explicitamente em consultas baseadas em método.</span><span class="sxs-lookup"><span data-stu-id="83f19-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="83f19-147">O exemplo a seguir mostra uma consulta LINQ típica, seguida pela conversão da consulta em formato de método.</span><span class="sxs-lookup"><span data-stu-id="83f19-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="83f19-148">Para obter mais informações sobre métodos de consulta, consulte [consultas](../queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="83f19-148">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="83f19-149">Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83f19-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f19-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="83f19-150">See also</span></span>

- [<span data-ttu-id="83f19-151">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="83f19-151">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="83f19-152">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="83f19-152">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="83f19-153">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="83f19-153">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="83f19-154">Instruções</span><span class="sxs-lookup"><span data-stu-id="83f19-154">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="83f19-155">Comparações de valor</span><span class="sxs-lookup"><span data-stu-id="83f19-155">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="83f19-156">Expressões booleanas</span><span class="sxs-lookup"><span data-stu-id="83f19-156">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="83f19-157">Operador If</span><span class="sxs-lookup"><span data-stu-id="83f19-157">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="83f19-158">Conversão de delegado reduzida</span><span class="sxs-lookup"><span data-stu-id="83f19-158">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
