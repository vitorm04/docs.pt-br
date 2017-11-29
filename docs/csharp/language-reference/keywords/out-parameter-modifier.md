---
title: "Modificador de parâmetro out (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="bfc6a-102">Modificador de parâmetro out (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bfc6a-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="bfc6a-103">A palavra-chave `out` faz com que os argumentos sejam passados por referência.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="bfc6a-104">É como a palavra-chave [ref](../../../csharp/language-reference/keywords/ref.md), exceto pelo fato de que `ref` requer que a variável seja inicializada antes de ser passada.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-104">It is like the [ref](../../../csharp/language-reference/keywords/ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="bfc6a-105">Para usar um parâmetro `out`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `out`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-105">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="bfc6a-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfc6a-106">For example:</span></span>  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> <span data-ttu-id="bfc6a-107">A palavra-chave `out` também pode ser usada com um parâmetro de tipo genérico para especificar que o parâmetro de tipo é covariante.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-107">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="bfc6a-108">Para obter mais informações sobre o uso da palavra-chave `out` nesse contexto, consulte [out (modificador genérico)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="bfc6a-108">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](../../../csharp/language-reference/keywords/out-generic-modifier.md).</span></span>
  
 <span data-ttu-id="bfc6a-109">Variáveis passadas como argumentos `out` não precisam ser inicializadas antes de serem passadas em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-109">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="bfc6a-110">No entanto, o método chamado é necessário para atribuir um valor antes que o método seja retornado.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-110">However, the called method is required to assign a value before the method returns.</span></span>  
  
 <span data-ttu-id="bfc6a-111">Embora as palavras-chave `ref` e `out` causem comportamento de tempo de execução diferente, elas não são consideradas parte da assinatura do método no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-111">Although the `ref` and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="bfc6a-112">Portanto, os métodos não poderão ser sobrecarregados se a única diferença for que um método terá um argumento `ref` e o outro utilizará um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="bfc6a-113">Por exemplo, o código a seguir, não será compilado:</span><span class="sxs-lookup"><span data-stu-id="bfc6a-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="bfc6a-114">No entanto, a sobrecarga será válida se um método usar um argumento `ref` ou `out` e o outro não usar nenhum, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bfc6a-114">Overloading is legal, however, if one method takes a `ref` or `out` argument and the other uses neither, like this:</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 <span data-ttu-id="bfc6a-115">Propriedades não são variáveis e portanto não podem ser passadas como parâmetros `out`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-115">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>  
  
 <span data-ttu-id="bfc6a-116">Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="bfc6a-116">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="bfc6a-117">Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="bfc6a-117">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="bfc6a-118">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="bfc6a-118">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="bfc6a-119">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-119">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="bfc6a-120">Declarando argumentos `out`</span><span class="sxs-lookup"><span data-stu-id="bfc6a-120">Declaring `out` arguments</span></span>   

 <span data-ttu-id="bfc6a-121">Declarar um método com argumentos `out` é útil quando você deseja que um método retorne vários valores.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-121">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="bfc6a-122">O exemplo a seguir usa `out` para retornar três variáveis com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-122">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="bfc6a-123">Observe que o terceiro argumento é atribuído a null.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-123">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="bfc6a-124">Isso permite que os métodos retornem valores opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-124">This enables methods to return values optionally.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 <span data-ttu-id="bfc6a-125">O [padrão Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) envolve retornar um `bool` para indicar se uma operação teve êxito ou falhou, bem como retornar o valor produzido pela operação em um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-125">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="bfc6a-126">Diversos métodos de análise, como o método [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), usam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-126">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="bfc6a-127">Chamando um método com um argumento `out`</span><span class="sxs-lookup"><span data-stu-id="bfc6a-127">Calling a method with an `out` argument</span></span>

<span data-ttu-id="bfc6a-128">No C# 6 e em versões anteriores, você precisa declarar uma variável em uma instrução separada antes de passá-lo como um argumento `out`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-128">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="bfc6a-129">O exemplo a seguir declara uma variável chamada `number` antes de passá-la para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), que tenta converter uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-129">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

<span data-ttu-id="bfc6a-130">A partir do C#7, você pode declarar a variável `out` na lista de argumentos da chamada de método em vez de declará-la em uma declaração de variável separada.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-130">Starting with C# 7, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="bfc6a-131">Isso produz um código mais compacto e legível, além de impedir que você atribua acidentalmente um valor à variável antes da chamada de método.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-131">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="bfc6a-132">O exemplo a seguir é semelhante ao exemplo anterior, exceto por definir a variável `number` na chamada para o método [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).</span><span class="sxs-lookup"><span data-stu-id="bfc6a-132">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
<span data-ttu-id="bfc6a-133">No exemplo anterior, a variável `number` é fortemente tipada como um `int`.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-133">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="bfc6a-134">Você também pode declarar uma variável local de tipo implícito, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfc6a-134">You can also declare an implicitly typed local variable, as the following example does.</span></span>

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="bfc6a-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="bfc6a-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bfc6a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfc6a-136">See Also</span></span>  
 [<span data-ttu-id="bfc6a-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bfc6a-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bfc6a-138">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bfc6a-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bfc6a-139">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="bfc6a-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bfc6a-140">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="bfc6a-140">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
