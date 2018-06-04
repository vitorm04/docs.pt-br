---
title: ref (Referência de C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: a4d5719bccd240658880cc5c6e549e8c912ca1b9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696388"
---
# <a name="ref-c-reference"></a><span data-ttu-id="a0296-102">ref (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a0296-102">ref (C# Reference)</span></span>

<span data-ttu-id="a0296-103">A palavra-chave `ref` indica um valor que é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="a0296-104">Ele é usado em três contextos diferentes:</span><span class="sxs-lookup"><span data-stu-id="a0296-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="a0296-105">Em uma assinatura de método e em uma chamada de método, para passar um argumento a um método por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="a0296-106">Consulte [Passar um argumento por referência](#passing-an-argument-by-reference) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a0296-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="a0296-107">Em uma assinatura de método para retornar um valor para o chamador por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="a0296-108">Para obter mais informações, consulte [Valores retornados por referência](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="a0296-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="a0296-109">Em um corpo de membro, para indicar que um valor retornado por referência é armazenado localmente como uma referência que o chamador pretende modificar ou, em geral, uma variável local acessa outro valor por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="a0296-110">Consulte [Ref locals](#ref-locals) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a0296-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="a0296-111">Passando um argumento por referência</span><span class="sxs-lookup"><span data-stu-id="a0296-111">Passing an argument by reference</span></span>

<span data-ttu-id="a0296-112">Quando usado na lista de parâmetros do método, a palavra-chave `ref` indica que um argumento é passado por referência, não por valor.</span><span class="sxs-lookup"><span data-stu-id="a0296-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="a0296-113">O efeito de passar por referência é que qualquer alteração no argumento do método chamado será refletida no método chamado.</span><span class="sxs-lookup"><span data-stu-id="a0296-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="a0296-114">Por exemplo, se o chamador passa uma expressão variável local ou uma expressão de acesso do elemento de matriz e o método chamado substituir o objeto ao qual o parâmetro ref se refere, então a variável local do chamador ou o elemento da matriz fará agora referência ao novo objeto quando o método retornar.</span><span class="sxs-lookup"><span data-stu-id="a0296-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="a0296-115">Não confunda o conceito de passar por referência com o conceito de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="a0296-116">Os dois conceitos não são iguais.</span><span class="sxs-lookup"><span data-stu-id="a0296-116">The two concepts are not the same.</span></span> <span data-ttu-id="a0296-117">Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="a0296-118">Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="a0296-119">Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0296-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="a0296-120">Um argumento passado para um parâmetro `ref` ou `in` precisa ser inicializado antes de ser passado.</span><span class="sxs-lookup"><span data-stu-id="a0296-120">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="a0296-121">Isso é diferente dos parâmetros [out](out-parameter-modifier.md), cujos argumentos não precisam ser inicializados explicitamente antes de serem passados.</span><span class="sxs-lookup"><span data-stu-id="a0296-121">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="a0296-122">Os membros de uma classe não podem ter assinaturas que se diferem somente por `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="a0296-122">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="a0296-123">Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles tem um parâmetro `ref` e o outro tem um parâmetro `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="a0296-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="a0296-124">O código a seguir, por exemplo, não é compilado.</span><span class="sxs-lookup"><span data-stu-id="a0296-124">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
<span data-ttu-id="a0296-125">No entanto, os métodos podem ser sobrecarregados quando um método tem um parâmetro `ref`, `in` ou `out` e o outro tem um parâmetro de valor, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0296-125">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="a0296-126">Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `in`, `ref` e `out` fazem parte da assinatura e não são correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a0296-126">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="a0296-127">Propriedades não são variáveis.</span><span class="sxs-lookup"><span data-stu-id="a0296-127">Properties are not variables.</span></span> <span data-ttu-id="a0296-128">Elas são métodos e não podem ser passadas para parâmetros `ref`.</span><span class="sxs-lookup"><span data-stu-id="a0296-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="a0296-129">Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="a0296-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="a0296-130">Não é possível usar as palavras-chave `ref`, `in` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="a0296-130">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="a0296-131">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="a0296-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="a0296-132">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="a0296-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="a0296-133">Passando um argumento por referência: um exemplo</span><span class="sxs-lookup"><span data-stu-id="a0296-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="a0296-134">Os exemplos anteriores passam tipos de valor por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="a0296-135">Você também pode usar a palavra-chave `ref` para passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="a0296-136">Passar um tipo de referência por referência permite que o método chamado substitua o objeto ao qual se refere o parâmetro de referência no chamador.</span><span class="sxs-lookup"><span data-stu-id="a0296-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="a0296-137">O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="a0296-138">Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador.</span><span class="sxs-lookup"><span data-stu-id="a0296-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="a0296-139">O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="a0296-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="a0296-140">Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a0296-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="a0296-141">Valores retornados por referência</span><span class="sxs-lookup"><span data-stu-id="a0296-141">Reference return values</span></span>

<span data-ttu-id="a0296-142">Valores retornados por referência (ou ref returns) são valores que um método retorna por referência para o chamador.</span><span class="sxs-lookup"><span data-stu-id="a0296-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="a0296-143">Ou seja, o chamador pode modificar o valor retornado por um método e essa alteração será refletida no estado do objeto que contém o método.</span><span class="sxs-lookup"><span data-stu-id="a0296-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="a0296-144">Um valor retornado por referência é definido usando a palavra-chave `ref`:</span><span class="sxs-lookup"><span data-stu-id="a0296-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="a0296-145">Na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="a0296-145">In the method signature.</span></span> <span data-ttu-id="a0296-146">Por exemplo, a seguinte método assinatura indica por que o método `GetCurrentPrice` retorna um valor <xref:System.Decimal> por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="a0296-147">Entre o token `return` e a variável retornada em uma instrução `return` no método.</span><span class="sxs-lookup"><span data-stu-id="a0296-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="a0296-148">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0296-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="a0296-149">Para que o chamador modifique o estado do objeto, o valor retornado de referência deve ser armazenado em uma variável que é definida explicitamente como um [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="a0296-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="a0296-150">Para obter um exemplo, consulte [Um exemplo de ref returns e ref locals](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="a0296-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="a0296-151">Ref locals</span><span class="sxs-lookup"><span data-stu-id="a0296-151">Ref locals</span></span>

<span data-ttu-id="a0296-152">Uma variável de ref local é usada para fazer referência a valores retornados usando `return ref`.</span><span class="sxs-lookup"><span data-stu-id="a0296-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="a0296-153">Uma variável de ref local deve ser inicializada e atribuída a um valor retornado ref local.</span><span class="sxs-lookup"><span data-stu-id="a0296-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="a0296-154">Todas as modificações ao valor do ref local são refletidas no estado do objeto cujo método retornou o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="a0296-155">Você define um ref local usando a palavra-chave `ref` antes da declaração de variável, bem como imediatamente antes da chamada para o método que retorna o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="a0296-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="a0296-156">Por exemplo, a instrução a seguir define um valor de ref local que é retornado por um método chamado `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="a0296-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="a0296-157">Você pode acessar um valor por referência da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="a0296-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="a0296-158">Em alguns casos, acessar um valor por referência aumenta o desempenho, evitando uma operação de cópia potencialmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="a0296-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="a0296-159">Por exemplo, a instrução a seguir mostra como é possível definir um valor de local de ref que é usado para fazer referência a um valor.</span><span class="sxs-lookup"><span data-stu-id="a0296-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="a0296-160">Observe que, nos dois exemplos, a palavra-chave `ref` deve ser usada em ambos os locais ou o compilador gera o erro CS8172, "Não é possível inicializar uma variável por referência com um valor".</span><span class="sxs-lookup"><span data-stu-id="a0296-160">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="a0296-161">Um exemplo de ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="a0296-161">A ref returns and ref locals example</span></span>

<span data-ttu-id="a0296-162">O exemplo a seguir define uma classe `Book` que tem dois campos <xref:System.String>, `Title` e `Author`.</span><span class="sxs-lookup"><span data-stu-id="a0296-162">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="a0296-163">Ele também define uma classe `BookCollection` que inclui uma matriz privada de objetos `Book`.</span><span class="sxs-lookup"><span data-stu-id="a0296-163">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="a0296-164">Objetos de catálogo individuais são retornados por referência chamando o respectivo método `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="a0296-164">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="a0296-165">Quando o chamador armazena o valor retornado pelo método `GetBookByTitle` como um ref local, as alterações que o chamador faz ao valor retornado são refletidas no objeto `BookCollection`, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0296-165">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="a0296-166">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a0296-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0296-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0296-167">See also</span></span>  
 [<span data-ttu-id="a0296-168">Semântica de referência com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a0296-168">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
 [<span data-ttu-id="a0296-169">Passando parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0296-169">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="a0296-170">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="a0296-170">Method Parameters</span></span>](method-parameters.md)  
 [<span data-ttu-id="a0296-171">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a0296-171">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="a0296-172">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a0296-172">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="a0296-173">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a0296-173">C# Keywords</span></span>](index.md)
