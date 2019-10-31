---
title: Expressões lambda em PLINQ e TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: d1b716e977702d03db176da70be00a1e5c789a4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129026"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="013ec-102">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="013ec-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="013ec-103">A TPL (Biblioteca de Paralelismo de Tarefas) contém vários métodos que usam uma das família de delegados <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="013ec-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="013ec-104">Você pode usar esses delegados para transmitir sua lógica de programa personalizada para o loop paralelo, tarefa ou consulta.</span><span class="sxs-lookup"><span data-stu-id="013ec-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="013ec-105">Os exemplos de código para TPL, bem como o PLINQ, usam expressões lambda para criar instâncias desses delegados como blocos de código embutido.</span><span class="sxs-lookup"><span data-stu-id="013ec-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="013ec-106">Este tópico fornece uma breve introdução a Func e Action, e mostra como usar expressões lambda no PLINQ e na Biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="013ec-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="013ec-107">Para obter mais informações sobre delegados em geral, consulte [delegados](../../csharp/programming-guide/delegates/index.md) e [delegados](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="013ec-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="013ec-108">Para saber mais sobre expressões lambda em C# e em Visual Basic, confira [Expressões lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) e [Expressões lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="013ec-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="013ec-109">Delegado Func</span><span class="sxs-lookup"><span data-stu-id="013ec-109">Func Delegate</span></span>

<span data-ttu-id="013ec-110">Um delegado `Func` encapsula um método que retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="013ec-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="013ec-111">Em uma assinatura Func, o último parâmetro de tipo, ou da extrema direita, sempre especifica o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="013ec-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="013ec-112">Uma causa comum de erros do compilador é tentar passar dois parâmetros de entrada para um <xref:System.Func%602?displayProperty=nameWithType>; na verdade, esse tipo usa somente um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="013ec-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="013ec-113">A Biblioteca de Classes do Framework define 17 versões do `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType> e assim por diante até <xref:System.Func%6017?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="013ec-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="013ec-114">Delegado Action</span><span class="sxs-lookup"><span data-stu-id="013ec-114">Action Delegate</span></span>

<span data-ttu-id="013ec-115">Um delegado <xref:System.Action?displayProperty=nameWithType> encapsula um método (Sub em Visual Basic) que não retorna um valor, ou que retorna [void](../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="013ec-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value, or returns [void](../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="013ec-116">Em uma assinatura de tipo Action, os parâmetros de tipo representam apenas os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="013ec-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="013ec-117">Assim como Func, a Biblioteca de Classes do Framework define 17 versões de Action, partindo de uma versão que não tem nenhum parâmetro de tipo até uma versão que tenha 16 parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="013ec-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="013ec-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="013ec-118">Example</span></span>

<span data-ttu-id="013ec-119">O exemplo a seguir para o método <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> mostra como expressar delegados Func e Action usando expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="013ec-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="013ec-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="013ec-120">See also</span></span>

- [<span data-ttu-id="013ec-121">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="013ec-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
