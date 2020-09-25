---
description: Modificador de parâmetro out – Referência de C#
title: Modificador de parâmetro out – Referência de C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 6addfa3a654c0bb4e10213a3fb4fc0368f2570b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200180"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="09a06-103">Modificador de parâmetro out (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="09a06-103">out parameter modifier (C# Reference)</span></span>

<span data-ttu-id="09a06-104">A palavra-chave `out` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="09a06-104">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="09a06-105">Ela torna o parâmetro formal um alias para o argumento, que deve ser uma variável.</span><span class="sxs-lookup"><span data-stu-id="09a06-105">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="09a06-106">Em outras palavras, qualquer operação no parâmetro é feita no argumento.</span><span class="sxs-lookup"><span data-stu-id="09a06-106">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="09a06-107">É como a palavra-chave [ref](ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada.</span><span class="sxs-lookup"><span data-stu-id="09a06-107">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="09a06-108">Também é como a palavra-chave [in](in-parameter-modifier.md), exceto que `in` não permite que o método chamado modifique o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="09a06-108">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="09a06-109">Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="09a06-109">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="09a06-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="09a06-110">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> <span data-ttu-id="09a06-111">A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="09a06-111">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="09a06-112">Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="09a06-112">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="09a06-113">Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="09a06-113">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="09a06-114">No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.</span><span class="sxs-lookup"><span data-stu-id="09a06-114">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="09a06-115">As palavras-chave `in`, `ref` e `out` não são consideradas parte da assinatura do método para fins de resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="09a06-115">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="09a06-116">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="09a06-116">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="09a06-117">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="09a06-117">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="09a06-118">A sobrecarga será válida, no entanto, se um método usar um argumento `ref`, `in` ou `out` e o outro não tiver nenhum desses modificadores, desta forma:</span><span class="sxs-lookup"><span data-stu-id="09a06-118">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="09a06-119">O compilador escolherá a melhor sobrecarga correspondendo os modificadores de parâmetro no site de chamada aos modificadores de parâmetro usados na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="09a06-119">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>

<span data-ttu-id="09a06-120">Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.</span><span class="sxs-lookup"><span data-stu-id="09a06-120">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="09a06-121">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="09a06-121">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="09a06-122">Métodos assíncronos, que você define usando o modificador [async](./async.md).</span><span class="sxs-lookup"><span data-stu-id="09a06-122">Async methods, which you define by using the [async](./async.md) modifier.</span></span>  
  
- <span data-ttu-id="09a06-123">Métodos de iterador, que incluem uma instrução [yield return](./yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="09a06-123">Iterator methods, which include a [yield return](./yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="09a06-124">Além disso, os [métodos de extensão](../../programming-guide/classes-and-structs/extension-methods.md) têm as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="09a06-124">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="09a06-125">A `out` palavra-chave não pode ser usada no primeiro argumento de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="09a06-125">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="09a06-126">A `ref` palavra-chave não pode ser usada no primeiro argumento de um método de extensão quando o argumento não é um struct ou um tipo genérico não restrito a ser um struct.</span><span class="sxs-lookup"><span data-stu-id="09a06-126">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="09a06-127">A `in` palavra-chave não pode ser usada, a menos que o primeiro argumento seja um struct.</span><span class="sxs-lookup"><span data-stu-id="09a06-127">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="09a06-128">A `in` palavra-chave não pode ser usada em nenhum tipo genérico, mesmo quando restrita a um struct.</span><span class="sxs-lookup"><span data-stu-id="09a06-128">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="declaring-out-parameters"></a><span data-ttu-id="09a06-129">Declarando parâmetros `out`</span><span class="sxs-lookup"><span data-stu-id="09a06-129">Declaring `out` parameters</span></span>

<span data-ttu-id="09a06-130">Declarar um método com argumentos `out` é uma solução clássica para retornar vários valores.</span><span class="sxs-lookup"><span data-stu-id="09a06-130">Declaring a method with `out` arguments is a classic workaround to return multiple values.</span></span> <span data-ttu-id="09a06-131">A partir do C# 7,0, considere as [tuplas de valor](../builtin-types/value-tuples.md) para cenários semelhantes.</span><span class="sxs-lookup"><span data-stu-id="09a06-131">Beginning with C# 7.0, consider [value tuples](../builtin-types/value-tuples.md) for similar scenarios.</span></span> <span data-ttu-id="09a06-132">O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="09a06-132">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="09a06-133">O terceiro argumento é atribuído a NULL.</span><span class="sxs-lookup"><span data-stu-id="09a06-133">The third argument is assigned to null.</span></span> <span data-ttu-id="09a06-134">Isso permite que os métodos retornem valores opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="09a06-134">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="09a06-135">Chamando um método com um argumento `out`</span><span class="sxs-lookup"><span data-stu-id="09a06-135">Calling a method with an `out` argument</span></span>

<span data-ttu-id="09a06-136">No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="09a06-136">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="09a06-137">O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="09a06-137">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="09a06-138">Começando com o C#7.0, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada.</span><span class="sxs-lookup"><span data-stu-id="09a06-138">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="09a06-139">Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="09a06-139">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="09a06-140">O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="09a06-140">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

<span data-ttu-id="09a06-141">No exemplo anterior, a variável `number` é fortemente tipada como um `int`.</span><span class="sxs-lookup"><span data-stu-id="09a06-141">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="09a06-142">Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="09a06-142">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="09a06-143">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="09a06-143">C# Language Specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09a06-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="09a06-144">See also</span></span>

- [<span data-ttu-id="09a06-145">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="09a06-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="09a06-146">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="09a06-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="09a06-147">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="09a06-147">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="09a06-148">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="09a06-148">Method Parameters</span></span>](./method-parameters.md)
