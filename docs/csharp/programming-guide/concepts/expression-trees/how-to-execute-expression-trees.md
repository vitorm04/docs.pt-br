---
title: Como executar árvores de expressão (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 2aad970946e417d623907c9f832e2c6e29eef912
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44192516"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="0c3d6-102">Como executar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="0c3d6-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="0c3d6-103">Este tópico mostra como executar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="0c3d6-104">Executar uma árvore de expressão pode retornar um valor ou apenas realizar uma ação, como chamar um método.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="0c3d6-105">Somente árvores de expressão que representam expressões lambda podem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="0c3d6-106">Árvores de expressão que representam expressões lambda são do tipo <xref:System.Linq.Expressions.LambdaExpression> ou <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="0c3d6-107">Para executar essas árvores de expressão, chame o método <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> para criar um delegado executável e, em seguida, invoque o delegado.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c3d6-108">Se o tipo de delegado não for conhecido, ou seja, a expressão lambda for do tipo <xref:System.Linq.Expressions.LambdaExpression> e não <xref:System.Linq.Expressions.Expression%601>, você deverá chamar o método <xref:System.Delegate.DynamicInvoke%2A> sobre o delegado em vez de invocá-la diretamente.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="0c3d6-109">Se uma árvore de expressão não representa uma expressão lambda, você pode criar uma nova expressão lambda que tenha a árvore de expressão original como corpo, chamando o método <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="0c3d6-110">Em seguida, você pode executar a expressão lambda como descrito anteriormente nesta seção.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c3d6-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c3d6-111">Example</span></span>  
 <span data-ttu-id="0c3d6-112">O exemplo de código a seguir demonstra como executar uma árvore de expressão que representa a elevação de um número a uma potência, criando uma expressão lambda e executando-a.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="0c3d6-113">O resultado, representado pelo número elevado à potência, é exibido.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c3d6-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0c3d6-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0c3d6-115">Adicione uma referência de projeto à System.Core.dll, se ainda não foi referenciada.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="0c3d6-116">Inclua o namespace System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="0c3d6-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3d6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c3d6-117">See Also</span></span>

- [<span data-ttu-id="0c3d6-118">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="0c3d6-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [<span data-ttu-id="0c3d6-119">Como modificar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="0c3d6-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
