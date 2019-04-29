---
title: 'Como: Executar árvores de expressão (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: cccb0b301e1da6d82c616d56604ad46dfde83e2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787173"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="772f7-102">Como: Executar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="772f7-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="772f7-103">Este tópico mostra como executar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="772f7-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="772f7-104">Executar uma árvore de expressão pode retornar um valor ou apenas realizar uma ação, como chamar um método.</span><span class="sxs-lookup"><span data-stu-id="772f7-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="772f7-105">Somente árvores de expressão que representam expressões lambda podem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="772f7-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="772f7-106">Árvores de expressão que representam expressões lambda são do tipo <xref:System.Linq.Expressions.LambdaExpression> ou <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="772f7-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="772f7-107">Para executar essas árvores de expressão, chame o método <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> para criar um delegado executável e, em seguida, invoque o delegado.</span><span class="sxs-lookup"><span data-stu-id="772f7-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="772f7-108">Se o tipo de delegado não for conhecido, ou seja, a expressão lambda for do tipo <xref:System.Linq.Expressions.LambdaExpression> e não <xref:System.Linq.Expressions.Expression%601>, você deverá chamar o método <xref:System.Delegate.DynamicInvoke%2A> sobre o delegado em vez de invocá-la diretamente.</span><span class="sxs-lookup"><span data-stu-id="772f7-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="772f7-109">Se uma árvore de expressão não representa uma expressão lambda, você pode criar uma nova expressão lambda que tenha a árvore de expressão original como corpo, chamando o método <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="772f7-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="772f7-110">Em seguida, você pode executar a expressão lambda como descrito anteriormente nesta seção.</span><span class="sxs-lookup"><span data-stu-id="772f7-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="772f7-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="772f7-111">Example</span></span>  
 <span data-ttu-id="772f7-112">O exemplo de código a seguir demonstra como executar uma árvore de expressão que representa a elevação de um número a uma potência, criando uma expressão lambda e executando-a.</span><span class="sxs-lookup"><span data-stu-id="772f7-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="772f7-113">O resultado, representado pelo número elevado à potência, é exibido.</span><span class="sxs-lookup"><span data-stu-id="772f7-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="772f7-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="772f7-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="772f7-115">Adicione uma referência de projeto à System.Core.dll, se ainda não foi referenciada.</span><span class="sxs-lookup"><span data-stu-id="772f7-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="772f7-116">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="772f7-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772f7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="772f7-117">See also</span></span>

- [<span data-ttu-id="772f7-118">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="772f7-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="772f7-119">Como: Modificar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="772f7-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
