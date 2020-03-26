---
title: Modificador de parâmetro out – Referência de C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: c713aa929673e51e8e9986c536bae782121c7756
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249338"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="14d72-102">Modificador de parâmetro out (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="14d72-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="14d72-103">A palavra-chave `out` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="14d72-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="14d72-104">Ela torna o parâmetro formal um alias para o argumento, que deve ser uma variável.</span><span class="sxs-lookup"><span data-stu-id="14d72-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="14d72-105">Em outras palavras, qualquer operação no parâmetro é feita no argumento.</span><span class="sxs-lookup"><span data-stu-id="14d72-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="14d72-106">É como a palavra-chave [ref](ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada.</span><span class="sxs-lookup"><span data-stu-id="14d72-106">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="14d72-107">Também é como a palavra-chave [in](in-parameter-modifier.md), exceto que `in` não permite que o método chamado modifique o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="14d72-107">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="14d72-108">Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="14d72-108">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="14d72-109">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="14d72-109">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="14d72-110">A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="14d72-110">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="14d72-111">Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="14d72-111">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="14d72-112">Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="14d72-112">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="14d72-113">No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.</span><span class="sxs-lookup"><span data-stu-id="14d72-113">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="14d72-114">As palavras-chave `in`, `ref` e `out` não são consideradas parte da assinatura do método para fins de resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="14d72-114">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="14d72-115">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="14d72-115">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="14d72-116">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="14d72-116">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="14d72-117">A sobrecarga será válida, no entanto, se um método usar um argumento `ref`, `in` ou `out` e o outro não tiver nenhum desses modificadores, desta forma:</span><span class="sxs-lookup"><span data-stu-id="14d72-117">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="14d72-118">O compilador escolherá a melhor sobrecarga correspondendo os modificadores de parâmetro no site de chamada aos modificadores de parâmetro usados na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="14d72-118">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="14d72-119">Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.</span><span class="sxs-lookup"><span data-stu-id="14d72-119">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="14d72-120">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="14d72-120">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="14d72-121">Métodos assíncronos, que você define usando o modificador [async](./async.md).</span><span class="sxs-lookup"><span data-stu-id="14d72-121">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="14d72-122">Métodos de iterador, que incluem uma instrução [yield return](./yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="14d72-122">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="14d72-123">Além disso, [os métodos de extensão](../../programming-guide/classes-and-structs/extension-methods.md) têm as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="14d72-123">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="14d72-124">O `out` keywoard não pode ser usado no primeiro argumento de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="14d72-124">The `out` keywoard cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="14d72-125">A `ref` palavra-chave não pode ser usada no primeiro argumento de um método de extensão quando o argumento não é uma estrutura, ou um tipo genérico não constrangido a ser uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="14d72-125">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="14d72-126">A `in` palavra-chave não pode ser usada a menos que o primeiro argumento seja uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="14d72-126">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="14d72-127">A `in` palavra-chave não pode ser usada em qualquer tipo genérico, mesmo quando constrangida a ser uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="14d72-127">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="14d72-128">Declarando parâmetros `out`</span><span class="sxs-lookup"><span data-stu-id="14d72-128">Declaring `out` parameters</span></span>

<span data-ttu-id="14d72-129">Declarar um método com argumentos `out` é uma solução clássica para retornar vários valores.</span><span class="sxs-lookup"><span data-stu-id="14d72-129">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="14d72-130">Começando com o C# 7.0, considere [tuplas](../../tuples.md) para cenários semelhantes.</span><span class="sxs-lookup"><span data-stu-id="14d72-130">Beginning with C# 7.0, consider [tuples](../../tuples.md) for similar scenarios.</span></span> <span data-ttu-id="14d72-131">O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="14d72-131">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="14d72-132">Observe que o terceiro argumento é atribuído a null.</span><span class="sxs-lookup"><span data-stu-id="14d72-132">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="14d72-133">Isso permite que os métodos retornem valores opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="14d72-133">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="14d72-134">Chamando um método com um argumento `out`</span><span class="sxs-lookup"><span data-stu-id="14d72-134">Calling a method with an `out` argument</span></span>

<span data-ttu-id="14d72-135">No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="14d72-135">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="14d72-136">O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="14d72-136">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="14d72-137">Começando com o C#7.0, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada.</span><span class="sxs-lookup"><span data-stu-id="14d72-137">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="14d72-138">Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="14d72-138">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="14d72-139">O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="14d72-139">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="14d72-140">No exemplo anterior, a variável `number` é fortemente tipada como um `int`.</span><span class="sxs-lookup"><span data-stu-id="14d72-140">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="14d72-141">Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="14d72-141">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="14d72-142">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="14d72-142">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14d72-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="14d72-143">See also</span></span>

- [<span data-ttu-id="14d72-144">C# Referência</span><span class="sxs-lookup"><span data-stu-id="14d72-144">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="14d72-145">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="14d72-145">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="14d72-146">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="14d72-146">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="14d72-147">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="14d72-147">Method Parameters</span></span>](./method-parameters.md)
