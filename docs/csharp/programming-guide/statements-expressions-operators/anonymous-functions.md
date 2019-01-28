---
title: Funções anônimas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 05098d1f26526c60656cca2255a2f93922c025da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613721"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="f2b96-102">Funções anônimas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f2b96-102">Anonymous Functions (C# Programming Guide)</span></span>
<span data-ttu-id="f2b96-103">Uma função anônima é uma instrução ou expressão "embutida" que pode ser usada em qualquer local em que um tipo delegado é esperado.</span><span class="sxs-lookup"><span data-stu-id="f2b96-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="f2b96-104">Você pode usá-la para inicializar um delegado nomeado ou passá-la em vez de um tipo delegado nomeado como um parâmetro de método.</span><span class="sxs-lookup"><span data-stu-id="f2b96-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>  
  
 <span data-ttu-id="f2b96-105">Há dois tipos de funções anônimas que serão discutidas individualmente nos tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="f2b96-105">There are two kinds of anonymous functions, which are discussed individually in the following topics:</span></span>  
  
-   <span data-ttu-id="f2b96-106">[Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f2b96-106">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
-   [<span data-ttu-id="f2b96-107">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="f2b96-107">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  <span data-ttu-id="f2b96-108">As expressões lambda podem ser vinculadas a árvores de expressão e também a delegados.</span><span class="sxs-lookup"><span data-stu-id="f2b96-108">Lambda expressions can be bound to expression trees and also to delegates.</span></span>  
  
## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="f2b96-109">A evolução de delegados em C#</span><span class="sxs-lookup"><span data-stu-id="f2b96-109">The Evolution of Delegates in C#</span></span>  
 <span data-ttu-id="f2b96-110">No C# 1.0, você criava uma instância de um delegado, inicializando-a explicitamente com um método que era definido em outro local no código.</span><span class="sxs-lookup"><span data-stu-id="f2b96-110">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="f2b96-111">O C# 2.0 introduziu o conceito de métodos anônimos como uma maneira de escrever blocos de instrução sem nome embutidos, que podem ser executados em uma invocação de delegado.</span><span class="sxs-lookup"><span data-stu-id="f2b96-111">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="f2b96-112">O C# 3.0 introduziu as expressões lambda, que são semelhantes ao conceito dos métodos anônimos, mas mais expressivas e concisas.</span><span class="sxs-lookup"><span data-stu-id="f2b96-112">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="f2b96-113">Essas duas funcionalidades são conhecidas coletivamente como *funções anônimas*.</span><span class="sxs-lookup"><span data-stu-id="f2b96-113">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="f2b96-114">Em geral, aplicativos que se destinam à versão 3.5 e posteriores do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] devem usar as expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="f2b96-114">In general, applications that target version 3.5 and later of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] should use lambda expressions.</span></span>  
  
 <span data-ttu-id="f2b96-115">O exemplo a seguir demonstra a evolução da criação de delegado, desde o C# 1.0 até o C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="f2b96-115">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f2b96-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f2b96-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2b96-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2b96-117">See also</span></span>

- [<span data-ttu-id="f2b96-118">Instruções, expressões e operadores</span><span class="sxs-lookup"><span data-stu-id="f2b96-118">Statements, Expressions, and Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/index.md)
- [<span data-ttu-id="f2b96-119">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="f2b96-119">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="f2b96-120">Delegados</span><span class="sxs-lookup"><span data-stu-id="f2b96-120">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="f2b96-121">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="f2b96-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
