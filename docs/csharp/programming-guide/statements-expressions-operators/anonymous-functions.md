---
title: Funções anônimas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 4d266584e1867a512e4b61e8839fe948aafb007f
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363920"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="d2f66-102">Funções anônimas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d2f66-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="d2f66-103">Uma função anônima é uma instrução ou expressão "embutida" que pode ser usada em qualquer local em que um tipo delegado é esperado.</span><span class="sxs-lookup"><span data-stu-id="d2f66-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="d2f66-104">Você pode usá-la para inicializar um delegado nomeado ou passá-la em vez de um tipo delegado nomeado como um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="d2f66-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="d2f66-105">Você pode usar uma [expressão lambda](lambda-expressions.md) ou um [método anônimo](../../language-reference/operators/delegate-operator.md) para criar uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="d2f66-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="d2f66-106">Recomendamos o uso de expressões lambda já que elas fornecem uma maneira mais concisa e expressiva de gravar código embutido.</span><span class="sxs-lookup"><span data-stu-id="d2f66-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="d2f66-107">Ao contrário dos métodos anônimos, alguns tipos de expressões lambda podem ser convertidos nos tipos de árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="d2f66-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="d2f66-108">A evolução de delegados em C\#</span><span class="sxs-lookup"><span data-stu-id="d2f66-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="d2f66-109">No C# 1.0, você criava uma instância de um delegado, inicializando-a explicitamente com um método que era definido em outro local no código.</span><span class="sxs-lookup"><span data-stu-id="d2f66-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="d2f66-110">O C# 2.0 introduziu o conceito de métodos anônimos como uma maneira de escrever blocos de instrução sem nome embutidos, que podem ser executados em uma invocação de delegado.</span><span class="sxs-lookup"><span data-stu-id="d2f66-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="d2f66-111">O C# 3.0 introduziu as expressões lambda, que são semelhantes ao conceito dos métodos anônimos, mas mais expressivas e concisas.</span><span class="sxs-lookup"><span data-stu-id="d2f66-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="d2f66-112">Essas duas funcionalidades são conhecidas coletivamente como *funções anônimas*.</span><span class="sxs-lookup"><span data-stu-id="d2f66-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="d2f66-113">Em geral, aplicativos que se destinam à versão 3.5 e posteriores do .NET Framework devem usar as expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="d2f66-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="d2f66-114">O exemplo a seguir demonstra a evolução da criação de delegado, desde o C# 1.0 até o C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="d2f66-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2f66-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d2f66-115">C# language specification</span></span>

<span data-ttu-id="d2f66-116">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2f66-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d2f66-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2f66-117">See also</span></span>

- [<span data-ttu-id="d2f66-118">Instruções, expressões e operadores</span><span class="sxs-lookup"><span data-stu-id="d2f66-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="d2f66-119">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="d2f66-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="d2f66-120">Delegados</span><span class="sxs-lookup"><span data-stu-id="d2f66-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="d2f66-121">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="d2f66-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
