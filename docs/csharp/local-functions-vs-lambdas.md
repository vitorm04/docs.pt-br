---
title: "Funções locais vs. expressões lambda"
description: "Saiba porque as funções locais podem ser uma escolha melhor que as expressões lambda."
keywords: "C#, .NET, .NET Core, Últimos Recursos, Novidades, funções locais, expressões lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 0730e7b7d6e3ef7b5c534d16baacde6a7dafacfc
ms.contentlocale: pt-br
ms.lasthandoff: 08/25/2017

---
# <a name="local-functions-compared-to-lambda-expressions"></a><span data-ttu-id="e3faf-104">Funções locais comparadas com expressões lambda</span><span class="sxs-lookup"><span data-stu-id="e3faf-104">Local functions compared to Lambda expressions</span></span>

<span data-ttu-id="e3faf-105">À primeira vista, [funções locais](programming-guide/classes-and-structs/local-functions.md) e [expressões lambda](lambda-expressions.md) são muito semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e3faf-105">At first glance, [local functions](programming-guide/classes-and-structs/local-functions.md) and [lambda expressions](lambda-expressions.md) are very similar.</span></span>
<span data-ttu-id="e3faf-106">Dependendo de suas necessidades, funções locais podem ser uma solução muito melhor e mais simples.</span><span class="sxs-lookup"><span data-stu-id="e3faf-106">Depending on your needs, local functions may be a much better and simpler solution.</span></span>

<span data-ttu-id="e3faf-107">Examinaremos as diferenças entre a função local e as implementações de expressão lambda do algoritmo fatorial.</span><span class="sxs-lookup"><span data-stu-id="e3faf-107">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="e3faf-108">Primeiro a versão usando uma função local:</span><span class="sxs-lookup"><span data-stu-id="e3faf-108">First the version using a local function:</span></span>

<span data-ttu-id="e3faf-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Fatorial recursiva usando a função local")]</span><span class="sxs-lookup"><span data-stu-id="e3faf-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]</span></span>

<span data-ttu-id="e3faf-110">Compare essa implementação com uma versão que usa expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="e3faf-110">Contrast that implementation with a version that uses lambda expressions:</span></span>

<span data-ttu-id="e3faf-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Fatorial recursiva usando expressões lambda")]</span><span class="sxs-lookup"><span data-stu-id="e3faf-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]</span></span>

<span data-ttu-id="e3faf-112">Primeiro, as expressões lambda são implementadas instanciando um delegado e invocando esse delegado.</span><span class="sxs-lookup"><span data-stu-id="e3faf-112">First, lambda expressions are implemented by instantiating a delegate and invoking that delegate.</span></span> <span data-ttu-id="e3faf-113">As funções locais são implementadas como chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="e3faf-113">Local functions are implemented as method calls.</span></span>
<span data-ttu-id="e3faf-114">A instanciação necessária para expressões lambda significa alocações de memória extra, o que podem ser um fator de desempenho em caminhos de código crítico de tempo.</span><span class="sxs-lookup"><span data-stu-id="e3faf-114">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time critical code paths.</span></span>
<span data-ttu-id="e3faf-115">As funções locais não incorrem nessa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="e3faf-115">Local functions do not incur this overhead.</span></span> <span data-ttu-id="e3faf-116">No exemplo acima, a versão das funções locais tem 2 alocações a menos que a versão da expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="e3faf-116">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="e3faf-117">Esse método recursivo é simples o suficiente para que a função local seja implementada como um método privado com um nome gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="e3faf-117">This recursive method is simple enough that the local function is implemented as a private method with a compiler generated name.</span></span> <span data-ttu-id="e3faf-118">A única diferença de outros métodos privados é que ele é semanticamente delimitado dentro da função externa.</span><span class="sxs-lookup"><span data-stu-id="e3faf-118">Its only difference from other private methods is that it is semantically scoped inside the outer function.</span></span>

<span data-ttu-id="e3faf-119">Segundo, as funções locais podem ser chamadas antes de serem definidas.</span><span class="sxs-lookup"><span data-stu-id="e3faf-119">Second, local functions can be called before they are defined.</span></span> <span data-ttu-id="e3faf-120">As expressões lambda devem ser declaradas antes de serem definidas.</span><span class="sxs-lookup"><span data-stu-id="e3faf-120">Lambda expressions must be declared before they are defined.</span></span> <span data-ttu-id="e3faf-121">Isso significa que funções locais são mais fáceis de usar em algoritmos recursivos, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="e3faf-121">This means local functions are easier to use in recursive algorithms, as shown above.</span></span>

<span data-ttu-id="e3faf-122">Observe que a versão usando a expressão lambda deve declarar e inicializar a expressão lambda, `nthFactorial` antes de defini-la.</span><span class="sxs-lookup"><span data-stu-id="e3faf-122">Notice that the version using the lambda expression must declare and initialize the lambda expression, `nthFactorial` before defining it.</span></span> <span data-ttu-id="e3faf-123">Não fazer isso resulta em um erro em tempo de compilação para referenciar `nthFactorial` antes de atribuí-lo.</span><span class="sxs-lookup"><span data-stu-id="e3faf-123">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>
<span data-ttu-id="e3faf-124">Os algoritmos recursivos são mais fáceis de criar usando funções locais.</span><span class="sxs-lookup"><span data-stu-id="e3faf-124">Recursive algorithms are easier to create using local functions.</span></span>

<span data-ttu-id="e3faf-125">Terceiro, para as expressões lambda, o compilador deve sempre criar uma classe anônima e uma instância dessa classe para armazenar todas as variáveis capturadas pelo fechamento.</span><span class="sxs-lookup"><span data-stu-id="e3faf-125">Third, for lambda expressions, the compiler must always create an anonymous class and an instance of that class to store any variables captured by the closure.</span></span> <span data-ttu-id="e3faf-126">Considere este exemplo assíncrono:</span><span class="sxs-lookup"><span data-stu-id="e3faf-126">Consider this async example:</span></span>

<span data-ttu-id="e3faf-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Método de retorno de tarefa com uma expressão lambda")]</span><span class="sxs-lookup"><span data-stu-id="e3faf-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]</span></span>

<span data-ttu-id="e3faf-128">O fechamento desta expressão lambda contém as variáveis `address`, `index` e `name`.</span><span class="sxs-lookup"><span data-stu-id="e3faf-128">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="e3faf-129">No caso de funções locais, o objeto que implementa o encerramento pode ser um tipo `struct`.</span><span class="sxs-lookup"><span data-stu-id="e3faf-129">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="e3faf-130">Isso poderia gerar economia em uma alocação.</span><span class="sxs-lookup"><span data-stu-id="e3faf-130">That would save on an allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="e3faf-131">A função local equivalente desse método também usa uma classe para o fechamento.</span><span class="sxs-lookup"><span data-stu-id="e3faf-131">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="e3faf-132">O fechamento de uma função local ser implementado como um `class` ou como um `struct`, trata-se de um detalhe de implementação.</span><span class="sxs-lookup"><span data-stu-id="e3faf-132">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="e3faf-133">Uma função local pode usar um `struct`, enquanto uma lambda sempre usará um `class`.</span><span class="sxs-lookup"><span data-stu-id="e3faf-133">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

<span data-ttu-id="e3faf-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Método de retorno de tarefa com função local")]</span><span class="sxs-lookup"><span data-stu-id="e3faf-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]</span></span>

<span data-ttu-id="e3faf-135">Uma vantagem final não demonstrada neste exemplo é que as funções locais podem ser implementadas como iteradores, usando a sintaxe `yield return` para produzir uma sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="e3faf-135">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

<span data-ttu-id="e3faf-136">Embora as funções locais possam parecer redundantes para expressões lambda, elas realmente têm finalidades e usos diferentes.</span><span class="sxs-lookup"><span data-stu-id="e3faf-136">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span>
<span data-ttu-id="e3faf-137">As funções locais são mais eficientes para quando você deseja escrever uma função que é chamada apenas do contexto de outro método.</span><span class="sxs-lookup"><span data-stu-id="e3faf-137">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

