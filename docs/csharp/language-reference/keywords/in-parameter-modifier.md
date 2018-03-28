---
title: Modificador de parâmetro in (referência do C#)
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
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="056f9-102">Modificador de parâmetro in (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="056f9-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="056f9-103">A palavra-chave `in` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="056f9-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="056f9-104">É como as palavras-chave [ref](ref.md) ou [out](out-parameter-modifier.md), exceto que os argumentos `in` não podem ser modificados pelo método chamado. Os argumentos `ref` podem ser modificados e os argumentos `out` precisam ser modificados pelo chamador, e essas modificações poderão ser observadas no contexto da chamada.</span><span class="sxs-lookup"><span data-stu-id="056f9-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="056f9-105">O exemplo anterior demonstra que o modificador `in` é desnecessário no site da chamada.</span><span class="sxs-lookup"><span data-stu-id="056f9-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="056f9-106">Ele apenas é necessário na declaração do método.</span><span class="sxs-lookup"><span data-stu-id="056f9-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="056f9-107">A palavra-chave `in` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é contravariante, como parte de uma instrução `foreach` ou como parte de uma cláusula `join` em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="056f9-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="056f9-108">Para obter mais informações sobre o uso da palavra-chave `in` nesses contextos, confira [in](in.md) que fornece links para todos os tipos de uso.</span><span class="sxs-lookup"><span data-stu-id="056f9-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="056f9-109">As variáveis passadas como argumentos `in` precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="056f9-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="056f9-110">No entanto, o método chamado não pode atribuir um valor nem modificar o argumento.</span><span class="sxs-lookup"><span data-stu-id="056f9-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="056f9-111">Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="056f9-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="056f9-112">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="056f9-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="056f9-113">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="056f9-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="056f9-114">A sobrecarga baseada na presença de `in` é permitida, mas gera um aviso do compilador:</span><span class="sxs-lookup"><span data-stu-id="056f9-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="056f9-115">As propriedades ou constantes podem ser passadas como parâmetros `in`, porque o método de chamada não pode modificar seus valores.</span><span class="sxs-lookup"><span data-stu-id="056f9-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="056f9-116">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="056f9-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="056f9-117">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="056f9-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="056f9-118">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="056f9-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="056f9-119">Normalmente, os argumentos `in` são declarados para evitar as operações de cópia necessárias para passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="056f9-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="056f9-120">Isso é mais útil quando os argumentos são tipos de valor, como estruturas, em que as operações de cópia são mais dispendiosas do que a passagem por referência.</span><span class="sxs-lookup"><span data-stu-id="056f9-120">This is most useful when arguments are value types such as structures where copy operations are more expensive than passing by reference.</span></span>

> [!WARNING]
>  <span data-ttu-id="056f9-121">Os parâmetros `in` podem ser ainda mais dispendiosos se usados de forma incorreta.</span><span class="sxs-lookup"><span data-stu-id="056f9-121">`in` parameters can be even more expensive if misused.</span></span> <span data-ttu-id="056f9-122">O compilador pode não saber se os métodos do membro modificam o estado do struct.</span><span class="sxs-lookup"><span data-stu-id="056f9-122">The compiler may not know if member methods modify the state of the struct.</span></span> <span data-ttu-id="056f9-123">Quando o compilador não pode garantir que o objeto não será modificado, ele cria uma cópia defensivamente e chama as referências de membro usando essa cópia.</span><span class="sxs-lookup"><span data-stu-id="056f9-123">Whenever the compiler cannot ensure that the object is not modified, it defensively creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="056f9-124">Todas as modificações possíveis são feitas nessa cópia de defesa.</span><span class="sxs-lookup"><span data-stu-id="056f9-124">Any possible modifications are to that defensive copy.</span></span> <span data-ttu-id="056f9-125">As duas maneiras de evitar essas cópias são passar parâmetros `in` como argumentos `in` ou definir estruturas como `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="056f9-125">The two ways to avoid these copies are to pass `in` parameters as `in` arguments or to define structures as `readonly struct`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="056f9-126">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="056f9-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="056f9-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="056f9-127">See Also</span></span>  
 [<span data-ttu-id="056f9-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="056f9-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="056f9-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="056f9-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="056f9-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="056f9-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="056f9-131">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="056f9-131">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="056f9-132">Semântica de referência com Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="056f9-132">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
