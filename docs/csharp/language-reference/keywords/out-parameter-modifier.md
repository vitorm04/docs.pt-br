---
title: Modificador de parâmetro out (Referência de C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc31ae202ccbfee467dc0f6fa2cf515c751825ed
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47202585"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="e56cd-102">Modificador de parâmetro out (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e56cd-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="e56cd-103">A palavra-chave `out` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="e56cd-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="e56cd-104">É como a palavra-chave [ref](ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada.</span><span class="sxs-lookup"><span data-stu-id="e56cd-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="e56cd-105">Também é como a palavra-chave [in](in-parameter-modifier.md), exceto que `in` não permite que o método chamado modifique o valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="e56cd-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="e56cd-106">Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="e56cd-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e56cd-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="e56cd-108">A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="e56cd-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="e56cd-109">Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="e56cd-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="e56cd-110">Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e56cd-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="e56cd-111">No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.</span><span class="sxs-lookup"><span data-stu-id="e56cd-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="e56cd-112">Embora as palavras-chave `in`, `ref` e `out` causem um comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="e56cd-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="e56cd-113">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método usa um argumento `ref` ou `in` e o outro usa um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="e56cd-114">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="e56cd-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="e56cd-115">A sobrecarga será válida, no entanto, se um método usar um argumento `ref`, `in` ou `out` e o outro não tiver nenhum desses modificadores, desta forma:</span><span class="sxs-lookup"><span data-stu-id="e56cd-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="e56cd-116">O compilador escolherá a melhor sobrecarga correspondendo os modificadores de parâmetro no site de chamada aos modificadores de parâmetro usados na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="e56cd-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="e56cd-117">Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
<span data-ttu-id="e56cd-118">Não é possível usar as palavras-chave `in`, `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="e56cd-118">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="e56cd-119">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="e56cd-119">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="e56cd-120">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-120">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="e56cd-121">Declarando argumentos `out`</span><span class="sxs-lookup"><span data-stu-id="e56cd-121">Declaring `out` arguments</span></span>   

 <span data-ttu-id="e56cd-122">Declarar um método com argumentos `out` é útil quando você deseja que um método retorne vários valores.</span><span class="sxs-lookup"><span data-stu-id="e56cd-122">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="e56cd-123">O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e56cd-123">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="e56cd-124">Observe que o terceiro argumento é atribuído a null.</span><span class="sxs-lookup"><span data-stu-id="e56cd-124">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="e56cd-125">Isso permite que os métodos retornem valores opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="e56cd-125">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="e56cd-126">O [padrão Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) envolve retornar um `bool` para indicar se uma operação teve êxito ou falhou, bem como retornar o valor produzido pela operação em um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-126">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded or failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="e56cd-127">Diversos métodos de análise, como o método [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="e56cd-127">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="e56cd-128">Chamando um método com um argumento `out`</span><span class="sxs-lookup"><span data-stu-id="e56cd-128">Calling a method with an `out` argument</span></span>

<span data-ttu-id="e56cd-129">No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-129">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="e56cd-130">O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="e56cd-130">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="e56cd-131">Começando com o C#7.0, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada.</span><span class="sxs-lookup"><span data-stu-id="e56cd-131">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="e56cd-132">Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e56cd-132">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="e56cd-133">O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="e56cd-133">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="e56cd-134">No exemplo anterior, a variável `number` é fortemente tipada como um `int`.</span><span class="sxs-lookup"><span data-stu-id="e56cd-134">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="e56cd-135">Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e56cd-135">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="e56cd-136">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e56cd-136">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e56cd-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e56cd-137">See Also</span></span>

- [<span data-ttu-id="e56cd-138">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e56cd-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e56cd-139">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e56cd-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e56cd-140">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e56cd-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="e56cd-141">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="e56cd-141">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
