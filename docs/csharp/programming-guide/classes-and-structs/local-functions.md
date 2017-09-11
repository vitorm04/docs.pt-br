---
title: "Funções locais (Guia de Programação em C#)"
ms.date: 2017-06-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: 069a6411e3d89fa1c2dba57f0b83badff1342763
ms.contentlocale: pt-br
ms.lasthandoff: 08/16/2017

---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="e2514-102">Funções locais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e2514-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="e2514-103">Do C# 7 em diante, o C# dá suporte a *funções locais*.</span><span class="sxs-lookup"><span data-stu-id="e2514-103">Starting with C# 7, C# supports *local functions*.</span></span> <span data-ttu-id="e2514-104">Funções locais são métodos privados de um tipo que estão aninhados em outro membro.</span><span class="sxs-lookup"><span data-stu-id="e2514-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="e2514-105">Eles só podem ser chamados do membro que os contém.</span><span class="sxs-lookup"><span data-stu-id="e2514-105">They can only be called from their containing member.</span></span> <span data-ttu-id="e2514-106">Funções locais podem ser declaradas em e chamadas de:</span><span class="sxs-lookup"><span data-stu-id="e2514-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="e2514-107">Métodos, especialmente os métodos iteradores e os métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="e2514-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="e2514-108">Construtores</span><span class="sxs-lookup"><span data-stu-id="e2514-108">Constructors</span></span>
- <span data-ttu-id="e2514-109">Acessadores de propriedade</span><span class="sxs-lookup"><span data-stu-id="e2514-109">Property accessors</span></span>
- <span data-ttu-id="e2514-110">Acessadores de eventos</span><span class="sxs-lookup"><span data-stu-id="e2514-110">Event accessors</span></span>
- <span data-ttu-id="e2514-111">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="e2514-111">Anonymous methods</span></span>
- <span data-ttu-id="e2514-112">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="e2514-112">Lambda expressions</span></span>
- <span data-ttu-id="e2514-113">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="e2514-113">Finalizers</span></span>
- <span data-ttu-id="e2514-114">Outras funções locais</span><span class="sxs-lookup"><span data-stu-id="e2514-114">Other local functions</span></span>

<span data-ttu-id="e2514-115">No entanto, as funções locais não podem ser declaradas dentro de um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="e2514-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="e2514-116">Em alguns casos, você pode usar uma expressão lambda para implementar uma funcionalidade que também tem suporte por uma função local.</span><span class="sxs-lookup"><span data-stu-id="e2514-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="e2514-117">Para obter uma comparação, consulte [Funções locais comparadas com expressões Lambda](../../local-functions-vs-lambdas.md).</span><span class="sxs-lookup"><span data-stu-id="e2514-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="e2514-118">Funções locais tornam a intenção do seu código clara.</span><span class="sxs-lookup"><span data-stu-id="e2514-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="e2514-119">Qualquer pessoa que leia o código poderá ver que o método não pode ser chamado, exceto pelo método que o contém.</span><span class="sxs-lookup"><span data-stu-id="e2514-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="e2514-120">Para projetos de equipe, elas também impossibilitam que outro desenvolvedor, por engano, chame o método diretamente de qualquer outro lugar na classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="e2514-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or stuct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="e2514-121">Sintaxe de função local</span><span class="sxs-lookup"><span data-stu-id="e2514-121">Local function syntax</span></span>

<span data-ttu-id="e2514-122">Uma função local é definida como um método aninhado dentro de um membro recipiente.</span><span class="sxs-lookup"><span data-stu-id="e2514-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="e2514-123">Sua definição tem a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e2514-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="e2514-124">Funções locais podem usar os modificadores [async](../../language-reference/keywords/async.md) e [unsafe](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="e2514-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="e2514-125">Observe que todas as variáveis locais que estão definidas no membro recipiente, incluindo seus parâmetros de método, são acessíveis na função local.</span><span class="sxs-lookup"><span data-stu-id="e2514-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="e2514-126">Ao contrário de uma definição de método, uma definição de função local não pode incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="e2514-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="e2514-127">O modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="e2514-127">The member access modifier.</span></span> <span data-ttu-id="e2514-128">Já que todas as funções locais são privadas, incluir um modificador de acesso como a palavra-chave `private` gera o erro do compilador CS0106, "O modificador 'private' não é válido para este item".</span><span class="sxs-lookup"><span data-stu-id="e2514-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="e2514-129">A palavra-chave [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="e2514-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="e2514-130">Incluir a palavra-chave `static` gera o erro do compilador CS0106, "O modificador 'static' não é válido para este item".</span><span class="sxs-lookup"><span data-stu-id="e2514-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="e2514-131">Além disso, os atributos não podem ser aplicados à função local ou aos respectivos parâmetros e parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="e2514-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="e2514-132">O exemplo a seguir define uma função local chamada `AppendPathSeparator` que é privada para um método chamado `GetText`:</span><span class="sxs-lookup"><span data-stu-id="e2514-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
<span data-ttu-id="e2514-133">[!code-cs[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2514-133">[!code-cs[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]</span></span>  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="e2514-134">Funções locais e exceções</span><span class="sxs-lookup"><span data-stu-id="e2514-134">Local functions and exceptions</span></span>

<span data-ttu-id="e2514-135">Um dos recursos úteis de funções locais é que elas podem permitir que exceções sejam apresentadas imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e2514-135">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="e2514-136">Para iteradores de método, as exceções são apresentadas somente quando a sequência retornada é enumerada e não quando o iterador é recuperado.</span><span class="sxs-lookup"><span data-stu-id="e2514-136">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="e2514-137">Para métodos assíncronos, as exceções geradas em um método assíncrono são observadas quando a tarefa retornada é esperada.</span><span class="sxs-lookup"><span data-stu-id="e2514-137">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="e2514-138">O exemplo a seguir define um método `OddSequence` que enumera números ímpares entre um intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="e2514-138">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="e2514-139">Já que ele passa um número maior que 100 para o método enumerador `OddSequence`, o método gera uma <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="e2514-139">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="e2514-140">Assim como demonstrado pela saída do exemplo, a exceção é apresentada somente quando você itera os números e não quando você recupera o enumerador.</span><span class="sxs-lookup"><span data-stu-id="e2514-140">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

<span data-ttu-id="e2514-141">[!code-cs[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2514-141">[!code-cs[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]</span></span> 

<span data-ttu-id="e2514-142">Em vez disso, você pode lançar uma exceção ao executar a validação e antes de recuperar o iterador, retornando o iterador de uma função local, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2514-142">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

<span data-ttu-id="e2514-143">[!code-cs[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2514-143">[!code-cs[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]</span></span>

<span data-ttu-id="e2514-144">Funções locais podem ser usadas de maneira semelhante para lidar com exceções fora da operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e2514-144">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="e2514-145">Em geral, exceções geradas no método assíncrono exigem que você examine as exceções internas de um <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e2514-145">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="e2514-146">Funções locais permitem que seu código falhe no modo rápido e permitem que a exceção seja gerada e observada de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="e2514-146">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="e2514-147">O exemplo a seguir usa um método assíncrono chamado `GetMultipleAsync` para pausar para um número especificado de segundos e retornar um valor que é um múltiplo aleatório desse número de segundos.</span><span class="sxs-lookup"><span data-stu-id="e2514-147">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="e2514-148">O atraso máximo é de 5 segundos; um <xref:System.ArgumentOutOfRangeException> resulta em se o valor for maior que 5.</span><span class="sxs-lookup"><span data-stu-id="e2514-148">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="e2514-149">Como mostra o exemplo a seguir, a exceção que é lançada quando um valor de 6 é passada para o método `GetMultipleAsync` é encapsulada em um <xref:System.AggregateException> depois que o método `GetMultipleAsync` inicia sua execução.</span><span class="sxs-lookup"><span data-stu-id="e2514-149">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

<span data-ttu-id="e2514-150">[!code-cs[LocalFunctionAsync\`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2514-150">[!code-cs[LocalFunctionAsync\`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]</span></span> 

<span data-ttu-id="e2514-151">Assim como foi feito com o método iterador, podemos refatorar o código deste exemplo para executar a validação antes de chamar o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e2514-151">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="e2514-152">Assim como demonstrado pela saída de exemplo a seguir, o <xref:System.ArgumentOutOfRangeException> não é empacotado em uma < x:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="e2514-152">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <x:System.AggregateException>.</span></span>

<span data-ttu-id="e2514-153">[!code-cs[LocalFunctionAsync\`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2514-153">[!code-cs[LocalFunctionAsync\`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="e2514-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2514-154">See also</span></span>
[<span data-ttu-id="e2514-155">Métodos</span><span class="sxs-lookup"><span data-stu-id="e2514-155">Methods</span></span>](methods.md)

