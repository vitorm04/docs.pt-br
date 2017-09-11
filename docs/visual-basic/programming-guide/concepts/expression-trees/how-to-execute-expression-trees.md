---
title: "Como: executar árvores de expressão (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4cc2c9890c1f5efbc4036d94eef1adb05094ae40
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="326db-102">Como: executar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="326db-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="326db-103">Este tópico mostra como executar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="326db-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="326db-104">Executar uma árvore de expressão pode retornar um valor, ou ele pode executar apenas uma ação como chamar um método.</span><span class="sxs-lookup"><span data-stu-id="326db-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="326db-105">Somente as árvores de expressão que representam as expressões lambda podem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="326db-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="326db-106">Árvores de expressão que representam as expressões lambda são do tipo <xref:System.Linq.Expressions.LambdaExpression>ou <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="326db-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="326db-107">Para executar essas árvores de expressão, chame o <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>método para criar um delegado executável e, em seguida, chamar o delegado.</xref:System.Linq.Expressions.LambdaExpression.Compile%2A></span><span class="sxs-lookup"><span data-stu-id="326db-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="326db-108">Se o tipo do delegado não é conhecido, ou seja, a expressão lambda é do tipo <xref:System.Linq.Expressions.LambdaExpression>e não <xref:System.Linq.Expressions.Expression%601>, você deve chamar o <xref:System.Delegate.DynamicInvoke%2A>método no delegado em vez de chamá-lo diretamente.</xref:System.Delegate.DynamicInvoke%2A> </xref:System.Linq.Expressions.Expression%601> </xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="326db-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="326db-109">Se uma árvore de expressão não representa uma expressão lambda, você pode criar uma nova expressão lambda que tenha a árvore de expressão original como o corpo, chamando o <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>método.</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29></span><span class="sxs-lookup"><span data-stu-id="326db-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="326db-110">Em seguida, você pode executar a expressão lambda, conforme descrito anteriormente nesta seção.</span><span class="sxs-lookup"><span data-stu-id="326db-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="326db-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="326db-111">Example</span></span>  
 <span data-ttu-id="326db-112">O exemplo de código a seguir demonstra como executar uma árvore de expressão que representa a elevar um número a uma potência criando uma expressão lambda e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="326db-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="326db-113">O resultado, que representa o número elevado à potência, é exibido.</span><span class="sxs-lookup"><span data-stu-id="326db-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="326db-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="326db-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="326db-115">Adicione uma referência a System.Core.dll se ele já não foi referenciado.</span><span class="sxs-lookup"><span data-stu-id="326db-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="326db-116">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="326db-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="326db-117">See Also</span></span>  
 <span data-ttu-id="326db-118">[Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="326db-118">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="326db-119"> [Como: modificar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="326db-119"> [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span></span>
