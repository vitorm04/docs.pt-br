---
title: "Função expressão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: c379ed1694f72243ccb8367d5b820803b4fcf190
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="7b125-102">Expressão de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b125-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="7b125-103">Declara os parâmetros e o código que define uma expressão lambda de função.</span><span class="sxs-lookup"><span data-stu-id="7b125-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b125-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b125-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="7b125-105">Partes</span><span class="sxs-lookup"><span data-stu-id="7b125-105">Parts</span></span>  
  
|<span data-ttu-id="7b125-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7b125-106">Term</span></span>|<span data-ttu-id="7b125-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7b125-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="7b125-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7b125-108">Optional.</span></span> <span data-ttu-id="7b125-109">Uma lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="7b125-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="7b125-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="7b125-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="7b125-111">Consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="7b125-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="7b125-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7b125-112">Required.</span></span> <span data-ttu-id="7b125-113">Uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="7b125-113">A single expression.</span></span> <span data-ttu-id="7b125-114">O tipo da expressão é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="7b125-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="7b125-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7b125-115">Required.</span></span> <span data-ttu-id="7b125-116">Uma lista de instruções que retorna um valor usando o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="7b125-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="7b125-117">(Consulte [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).) O tipo do valor retornado é o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="7b125-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b125-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b125-118">Remarks</span></span>  
 <span data-ttu-id="7b125-119">A *expressão lambda* é uma função sem um nome que calcula e retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="7b125-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="7b125-120">Você pode usar uma expressão lambda em qualquer lugar você pode usar um tipo delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="7b125-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="7b125-121">Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [instrução delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="7b125-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="7b125-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="7b125-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="7b125-123">A sintaxe de uma expressão lambda lembra de uma função padrão.</span><span class="sxs-lookup"><span data-stu-id="7b125-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="7b125-124">As diferenças são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="7b125-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="7b125-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="7b125-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="7b125-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="7b125-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="7b125-127">Expressões lambda não usam uma `As` cláusula para designar o tipo de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="7b125-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="7b125-128">Em vez disso, o tipo é inferido do valor que avalia o corpo de uma expressão lambda de linha única ou o valor de retorno de uma expressão lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="7b125-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="7b125-129">Por exemplo, se o corpo de uma expressão lambda de linha única é `Where cust.City = "London"`, seu tipo de retorno é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7b125-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="7b125-130">O corpo de uma expressão lambda de linha deve ser uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="7b125-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="7b125-131">O corpo pode consistir de uma chamada para um procedimento function, mas não é uma chamada para um procedimento de sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="7b125-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="7b125-132">Todos os parâmetros devem especificar todos ou tipos de dados devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="7b125-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="7b125-133">Parâmetros opcionais e Paramarray não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="7b125-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="7b125-134">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="7b125-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b125-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b125-135">Example</span></span>  
 <span data-ttu-id="7b125-136">Os exemplos a seguir mostram duas maneiras de criar expressões lambda simples.</span><span class="sxs-lookup"><span data-stu-id="7b125-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="7b125-137">O primeiro usa um `Dim` para fornecer um nome para a função.</span><span class="sxs-lookup"><span data-stu-id="7b125-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="7b125-138">Para chamar a função, você deve enviar um valor para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7b125-138">To call the function, you send in a value for the parameter.</span></span>  
  
 <span data-ttu-id="7b125-139">[!code-vb[VbVbalrLambdas n º&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b125-139">[!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span></span>  
  
 <span data-ttu-id="7b125-140">[!code-vb[VbVbalrLambdas n º&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b125-140">[!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b125-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b125-141">Example</span></span>  
 <span data-ttu-id="7b125-142">Como alternativa, você pode declarar e executar a função ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="7b125-142">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 <span data-ttu-id="7b125-143">[!code-vb[VbVbalrLambdas n º&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b125-143">[!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b125-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b125-144">Example</span></span>  
 <span data-ttu-id="7b125-145">A seguir está um exemplo de uma expressão lambda que aumenta seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="7b125-145">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="7b125-146">O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="7b125-146">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="7b125-147">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7b125-147">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="7b125-148">[!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b125-148">[!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b125-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b125-149">Example</span></span>  
 <span data-ttu-id="7b125-150">Expressões lambda são a base de muitos dos operadores de consulta em [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]e pode ser usado explicitamente em consultas com base em método.</span><span class="sxs-lookup"><span data-stu-id="7b125-150">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="7b125-151">O exemplo a seguir mostra um típico [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consulta, seguido pela tradução da consulta em formato de método.</span><span class="sxs-lookup"><span data-stu-id="7b125-151">The following example shows a typical [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="7b125-152">Para obter mais informações sobre métodos de consulta, consulte [consultas](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="7b125-152">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="7b125-153">Para obter mais informações sobre operadores de consulta padrão, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="7b125-153">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b125-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b125-154">See Also</span></span>  
 <span data-ttu-id="7b125-155">[Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-155">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="7b125-156"> [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-156"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="7b125-157"> [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="7b125-158"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-158"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="7b125-159"> [Comparações de valor](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-159"> [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="7b125-160"> [Expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-160"> [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="7b125-161"> [Se operador](../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b125-161"> [If Operator](../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="7b125-162"> [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="7b125-162"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

