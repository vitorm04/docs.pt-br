---
title: "Modificador de parâmetro in (referência do C#)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="fa338-102">Modificador de parâmetro in (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="fa338-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="fa338-103">A palavra-chave `in` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="fa338-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="fa338-104">É como as palavras-chave [ref](ref.md) ou [out](out-parameter-modifier.md), exceto que os argumentos `in` não podem ser modificados pelo método chamado. Os argumentos `ref` podem ser modificados e os argumentos `out` precisam ser modificados pelo chamador, e essas modificações poderão ser observadas no contexto da chamada.</span><span class="sxs-lookup"><span data-stu-id="fa338-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="fa338-105">O exemplo anterior demonstra que o modificador `in` é desnecessário no site da chamada.</span><span class="sxs-lookup"><span data-stu-id="fa338-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="fa338-106">Ele apenas é necessário na declaração do método.</span><span class="sxs-lookup"><span data-stu-id="fa338-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="fa338-107">A palavra-chave `in` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é contravariante, como parte de uma instrução `foreach` ou como parte de uma cláusula `join` em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="fa338-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="fa338-108">Para obter mais informações sobre o uso da palavra-chave `in` nesses contextos, confira [in](in.md) que fornece links para todos os tipos de uso.</span><span class="sxs-lookup"><span data-stu-id="fa338-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="fa338-109">As variáveis passadas como argumentos `in` precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="fa338-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="fa338-110">No entanto, o método chamado não pode atribuir um valor nem modificar o argumento.</span><span class="sxs-lookup"><span data-stu-id="fa338-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="fa338-111">Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="fa338-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="fa338-112">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="fa338-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="fa338-113">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="fa338-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="fa338-114">A sobrecarga baseada na presença de `in` é permitida, mas gera um aviso do compilador:</span><span class="sxs-lookup"><span data-stu-id="fa338-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="fa338-115">As propriedades ou constantes podem ser passadas como parâmetros `in`, porque o método de chamada não pode modificar seus valores.</span><span class="sxs-lookup"><span data-stu-id="fa338-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="fa338-116">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="fa338-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="fa338-117">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="fa338-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="fa338-118">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="fa338-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="fa338-119">Normalmente, os argumentos `in` são declarados para evitar as operações de cópia necessárias para passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="fa338-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="fa338-120">Isso é mais útil quando os argumentos são estruturas ou matrizes de estruturas.</span><span class="sxs-lookup"><span data-stu-id="fa338-120">This is most useful when arguments are structures or arrays of structures.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fa338-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fa338-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa338-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa338-122">See Also</span></span>  
 [<span data-ttu-id="fa338-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fa338-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fa338-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fa338-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa338-125">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fa338-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fa338-126">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="fa338-126">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
