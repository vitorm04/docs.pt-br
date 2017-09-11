---
title: "Modificador de parâmetro out (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 59e445ac27f07c85d9e98c5f595cf5f935f75443
ms.openlocfilehash: 9a0a488c6f444608a335cd990847774fb6fe9e3f
ms.contentlocale: pt-br
ms.lasthandoff: 08/31/2017

---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="6ab2e-102">Modificador de parâmetro out (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6ab2e-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="6ab2e-103">A palavra-chave `out` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="6ab2e-104">É como a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="6ab2e-105">Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="6ab2e-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ab2e-106">For example:</span></span>  
  
 <span data-ttu-id="6ab2e-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-107">[!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="6ab2e-108">A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="6ab2e-109">Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="6ab2e-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="6ab2e-110">Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="6ab2e-111">No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="6ab2e-112">Embora as palavras-chave `ref` e `out` causem comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-112">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="6ab2e-113">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método terá um argumento `ref` e o outro utilizará um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="6ab2e-114">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="6ab2e-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="6ab2e-115">No entanto, a sobrecarga será válida se um método usar um argumento `ref` ou `out` e o outro não usar nenhum, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6ab2e-115">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 <span data-ttu-id="6ab2e-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-116">[!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]</span></span>  
  
 <span data-ttu-id="6ab2e-117">Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="6ab2e-118">Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="6ab2e-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="6ab2e-119">Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="6ab2e-119">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="6ab2e-120">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="6ab2e-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="6ab2e-121">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="6ab2e-122">Declarando argumentos `out`</span><span class="sxs-lookup"><span data-stu-id="6ab2e-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="6ab2e-123">Declarar um método com argumentos `out` é útil quando você deseja que um método retorne vários valores.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="6ab2e-124">O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="6ab2e-125">Observe que o terceiro argumento é atribuído a null.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="6ab2e-126">Isso permite que os métodos retornem valores opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-126">This enables methods to return values optionally.</span></span>  
  
 <span data-ttu-id="6ab2e-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-127">[!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]</span></span>  

 <span data-ttu-id="6ab2e-128">O [padrão Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) envolve retornar um `bool` para indicar se uma operação teve êxito ou falhou, bem como retornar o valor produzido pela operação em um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-128">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="6ab2e-129">Diversos métodos de análise, como o método [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-129">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="6ab2e-130">Chamando um método com um argumento `out`</span><span class="sxs-lookup"><span data-stu-id="6ab2e-130">Calling a method with an `out` argument</span></span>

<span data-ttu-id="6ab2e-131">No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-131">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="6ab2e-132">O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-132">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 <span data-ttu-id="6ab2e-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-133">[!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]</span></span>  

<span data-ttu-id="6ab2e-134">A partir do C#7, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-134">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="6ab2e-135">Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-135">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="6ab2e-136">O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="6ab2e-136">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 <span data-ttu-id="6ab2e-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-137">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]</span></span>  
   
<span data-ttu-id="6ab2e-138">No exemplo anterior, a variável `number` é fortemente tipada como um `int`.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-138">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="6ab2e-139">Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ab2e-139">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 <span data-ttu-id="6ab2e-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ab2e-140">[!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]</span></span>  
   
## <a name="c-language-specification"></a><span data-ttu-id="6ab2e-141">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6ab2e-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ab2e-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ab2e-142">See Also</span></span>  
 <span data-ttu-id="6ab2e-143">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ab2e-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6ab2e-144">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ab2e-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6ab2e-145">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ab2e-145">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="6ab2e-146">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="6ab2e-146">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

