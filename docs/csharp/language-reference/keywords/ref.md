---
title: "ref (Referência de C#)"
ms.date: 2017-05-30
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 003125ca6218d42a919d8bb592b5454a7cb387c7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ref-c-reference"></a><span data-ttu-id="334d5-102">ref (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="334d5-102">ref (C# Reference)</span></span>

<span data-ttu-id="334d5-103">A palavra-chave `ref` indica um valor que é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="334d5-104">Ele é usado em três contextos diferentes:</span><span class="sxs-lookup"><span data-stu-id="334d5-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="334d5-105">Em uma assinatura de método e em uma chamada de método, para passar um argumento a um método por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="334d5-106">Consulte [Passar um argumento por referência](#passing-an-argument-by-reference) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="334d5-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="334d5-107">Em uma assinatura de método para retornar um valor para o chamador por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="334d5-108">Para obter mais informações, consulte [Valores retornados por referência](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="334d5-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="334d5-109">Em um corpo de membro, para indicar que um valor retornado por referência é armazenado localmente como uma referência que o chamador pretende modificar.</span><span class="sxs-lookup"><span data-stu-id="334d5-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="334d5-110">Consulte [Ref locals](#ref-locals) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="334d5-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="334d5-111">Passando um argumento por referência</span><span class="sxs-lookup"><span data-stu-id="334d5-111">Passing an argument by reference</span></span>

<span data-ttu-id="334d5-112">Quando usado na lista de parâmetros do método, a palavra-chave `ref` indica que um argumento é passado por referência, não por valor.</span><span class="sxs-lookup"><span data-stu-id="334d5-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="334d5-113">O efeito de passar por referência é que qualquer alteração no argumento do método chamado será refletida no método chamado.</span><span class="sxs-lookup"><span data-stu-id="334d5-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="334d5-114">Por exemplo, se o chamador passa uma expressão variável local ou uma expressão de acesso do elemento de matriz e o método chamado substituir o objeto ao qual o parâmetro ref se refere, então a variável local do chamador ou o elemento da matriz fará agora referência ao novo objeto quando o método retornar.</span><span class="sxs-lookup"><span data-stu-id="334d5-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="334d5-115">Não confunda o conceito de passar por referência com o conceito de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="334d5-116">Os dois conceitos não são iguais.</span><span class="sxs-lookup"><span data-stu-id="334d5-116">The two concepts are not the same.</span></span> <span data-ttu-id="334d5-117">Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="334d5-118">Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="334d5-119">Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="334d5-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

<span data-ttu-id="334d5-120">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="334d5-120">[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]</span></span>

<span data-ttu-id="334d5-121">Um argumento que é passado para um parâmetro `ref` deve ser inicializado antes de ser passado.</span><span class="sxs-lookup"><span data-stu-id="334d5-121">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="334d5-122">Isso é diferente dos parâmetros [out](out.md), cujos argumentos não precisam ser inicializados explicitamente antes de serem passados.</span><span class="sxs-lookup"><span data-stu-id="334d5-122">This differs from [out](out.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="334d5-123">Os membros de uma classe não podem ter assinaturas que diferem somente por `ref` e `out`.</span><span class="sxs-lookup"><span data-stu-id="334d5-123">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="334d5-124">Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles possui um parâmetro `ref` e o outro possui um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="334d5-124">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="334d5-125">O código a seguir, por exemplo, não é compilado.</span><span class="sxs-lookup"><span data-stu-id="334d5-125">The following code, for example, doesn't compile.</span></span>  
  
 <span data-ttu-id="334d5-126">[!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="334d5-126">[!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]</span></span>
  
 <span data-ttu-id="334d5-127">No entanto, pode haver sobrecarga quando um método tiver um parâmetro `ref` ou `out` e o outro tiver um parâmetro de valor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="334d5-127">However, methods can be overloaded when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
 <span data-ttu-id="334d5-128">[!code-cs[ref e sobrecargas](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="334d5-128">[!code-cs[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]</span></span>
  
 <span data-ttu-id="334d5-129">Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `ref` e `out` fazem parte da assinatura e não são correspondentes.</span><span class="sxs-lookup"><span data-stu-id="334d5-129">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="334d5-130">Propriedades não são variáveis.</span><span class="sxs-lookup"><span data-stu-id="334d5-130">Properties are not variables.</span></span> <span data-ttu-id="334d5-131">Elas são métodos e não podem ser passadas para parâmetros `ref`.</span><span class="sxs-lookup"><span data-stu-id="334d5-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="334d5-132">Para obter informações sobre como passar matrizes, consulte [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="334d5-132">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="334d5-133">Não é possível usar as palavras-chave `ref` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="334d5-133">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="334d5-134">Métodos assíncronos, que você define usando o modificador [async](../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="334d5-134">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="334d5-135">Métodos de iterador, que incluem uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="334d5-135">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="334d5-136">Passando um argumento por referência: um exemplo</span><span class="sxs-lookup"><span data-stu-id="334d5-136">Passing an argument by reference: An example</span></span>

<span data-ttu-id="334d5-137">Os exemplos anteriores passam tipos de valor por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-137">The previous examples pass value types by reference.</span></span> <span data-ttu-id="334d5-138">Você também pode usar a palavra-chave `ref` para passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-138">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="334d5-139">Passar um tipo de referência por referência permite que o método chamado substitua o objeto ao qual se refere o parâmetro de referência no chamador.</span><span class="sxs-lookup"><span data-stu-id="334d5-139">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="334d5-140">O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-140">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="334d5-141">Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador.</span><span class="sxs-lookup"><span data-stu-id="334d5-141">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="334d5-142">O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="334d5-142">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
 <span data-ttu-id="334d5-143">[!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]</span><span class="sxs-lookup"><span data-stu-id="334d5-143">[!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]</span></span>  

<span data-ttu-id="334d5-144">Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="334d5-144">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="334d5-145">Valores retornados por referência</span><span class="sxs-lookup"><span data-stu-id="334d5-145">Reference return values</span></span>

<span data-ttu-id="334d5-146">Valores retornados por referência (ou ref returns) são valores que um método retorna por referência para o chamador.</span><span class="sxs-lookup"><span data-stu-id="334d5-146">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="334d5-147">Ou seja, o chamador pode modificar o valor retornado por um método e essa alteração será refletida no estado do objeto que contém o método.</span><span class="sxs-lookup"><span data-stu-id="334d5-147">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="334d5-148">Um valor retornado por referência é definido usando a palavra-chave `ref`:</span><span class="sxs-lookup"><span data-stu-id="334d5-148">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="334d5-149">Na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="334d5-149">In the method signature.</span></span> <span data-ttu-id="334d5-150">Por exemplo, a seguinte método assinatura indica por que o método `GetCurrentPrice` retorna um valor <xref:System.Decimal> por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-150">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="334d5-151">Antes de cada instrução `return` no método.</span><span class="sxs-lookup"><span data-stu-id="334d5-151">Before each `return` statement in the method.</span></span> <span data-ttu-id="334d5-152">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="334d5-152">For example:</span></span>
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

<span data-ttu-id="334d5-153">Para que o chamador modifique o estado de um objeto, o valor retornado de referência deve ser armazenado em uma variável que é definida explicitamente como um [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="334d5-153">In order for the caller to modify the an object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="334d5-154">Para obter um exemplo, consulte [Um exemplo de ref returns e ref locals](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="334d5-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="334d5-155">Ref locals</span><span class="sxs-lookup"><span data-stu-id="334d5-155">Ref locals</span></span>

<span data-ttu-id="334d5-156">Uma variável de ref local é usada para fazer referência a valores retornados usando `ref return`.</span><span class="sxs-lookup"><span data-stu-id="334d5-156">A ref local variable is used to refer to values returned using `ref return`.</span></span>  <span data-ttu-id="334d5-157">Uma variável de ref local deve ser inicializada e atribuída a um valor retornado ref local.</span><span class="sxs-lookup"><span data-stu-id="334d5-157">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="334d5-158">Todas as modificações ao valor do ref local são refletidas no estado do objeto cujo método retornou o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-158">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="334d5-159">Você define um ref local usando a palavra-chave `ref` antes da declaração de variável, bem como imediatamente antes da chamada para o método que retorna o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="334d5-159">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="334d5-160">Por exemplo, a instrução a seguir define um valor de ref local que é retornado por um método chamado `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="334d5-160">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="334d5-161">Observe que a palavra-chave `ref` deve ser usada em ambos os locais ou o compilador gera o erro CS8172, "Não é possível inicializar uma variável por referência com um valor".</span><span class="sxs-lookup"><span data-stu-id="334d5-161">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="334d5-162">Um exemplo de ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="334d5-162">A ref returns and ref locals example</span></span>

<span data-ttu-id="334d5-163">O exemplo a seguir define uma classe `Book` que tem dois campos <xref:System.String>, `Title` e `Author`.</span><span class="sxs-lookup"><span data-stu-id="334d5-163">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="334d5-164">Ele também define uma classe `BookCollection` que inclui uma matriz privada de objetos `Book`.</span><span class="sxs-lookup"><span data-stu-id="334d5-164">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="334d5-165">Objetos de catálogo individuais são retornados por referência chamando o respectivo método `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="334d5-165">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

<span data-ttu-id="334d5-166">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="334d5-166">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]</span></span>  

<span data-ttu-id="334d5-167">Quando o chamador armazena o valor retornado pelo método `GetBookByTitle` como um ref local, as alterações que o chamador faz ao valor retornado são refletidas no objeto `BookCollection`, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="334d5-167">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

<span data-ttu-id="334d5-168">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="334d5-168">[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="334d5-169">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="334d5-169">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="334d5-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="334d5-170">See Also</span></span>  
 <span data-ttu-id="334d5-171">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="334d5-171">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="334d5-172">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="334d5-172">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="334d5-173">[Passando Parâmetros](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="334d5-173">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 <span data-ttu-id="334d5-174">[Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="334d5-174">[Method Parameters](../../../csharp/language-reference/keywords/method-parameters.md) </span></span>  
 [<span data-ttu-id="334d5-175">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="334d5-175">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

