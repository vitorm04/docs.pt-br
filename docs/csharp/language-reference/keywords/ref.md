---
title: Palavra-chave ref – Referência de C#
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 1faebe2ce1a59798621888e3a518900234720be5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116250"
---
# <a name="ref-c-reference"></a><span data-ttu-id="2b2d1-102">ref (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2b2d1-102">ref (C# Reference)</span></span>

<span data-ttu-id="2b2d1-103">A palavra-chave `ref` indica um valor que é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="2b2d1-104">Ela é usada em quatro contextos diferentes:</span><span class="sxs-lookup"><span data-stu-id="2b2d1-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="2b2d1-105">Em uma assinatura de método e em uma chamada de método, para passar um argumento a um método por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="2b2d1-106">Para obter mais informações, veja [Passar um argumento por referência](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="2b2d1-107">Em uma assinatura de método para retornar um valor para o chamador por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="2b2d1-108">Para obter mais informações, consulte [Reference return values](#reference-return-values) (Valores retornados de referência).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="2b2d1-109">Em um corpo de membro, para indicar que um valor retornado por referência é armazenado localmente como uma referência que o chamador pretende modificar ou, em geral, uma variável local acessa outro valor por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="2b2d1-110">Para obter mais informações, veja [Locais de referência](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="2b2d1-111">Em uma declaração `struct` para declarar um `ref struct` ou um `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="2b2d1-112">Para obter mais informações, veja [tipos ref struct](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="2b2d1-113">Passando um argumento por referência</span><span class="sxs-lookup"><span data-stu-id="2b2d1-113">Passing an argument by reference</span></span>

<span data-ttu-id="2b2d1-114">Quando usado na lista de parâmetros do método, a palavra-chave `ref` indica que um argumento é passado por referência, não por valor.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="2b2d1-115">A palavra-chave `ref` torna o parâmetro formal um alias para o argumento, que deve ser uma variável.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="2b2d1-116">Em outras palavras, qualquer operação no parâmetro é feita no argumento.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="2b2d1-117">Por exemplo, se o chamador passa uma expressão variável local ou uma expressão de acesso do elemento de matriz e o método chamado substituir o objeto ao qual o parâmetro ref se refere, então a variável local do chamador ou o elemento da matriz fará agora referência ao novo objeto quando o método retornar.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="2b2d1-118">Não confunda o conceito de passar por referência com o conceito de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="2b2d1-119">Os dois conceitos não são iguais.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-119">The two concepts are not the same.</span></span> <span data-ttu-id="2b2d1-120">Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="2b2d1-121">Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="2b2d1-122">Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="2b2d1-123">Um argumento passado para um parâmetro `ref` ou `in` precisa ser inicializado antes de ser passado.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="2b2d1-124">Isso é diferente dos parâmetros [out](out-parameter-modifier.md), cujos argumentos não precisam ser inicializados explicitamente antes de serem passados.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="2b2d1-125">Os membros de uma classe não podem ter assinaturas que se diferem somente por `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="2b2d1-126">Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles tem um parâmetro `ref` e o outro tem um parâmetro `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="2b2d1-127">O código a seguir, por exemplo, não é compilado.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="2b2d1-128">No entanto, os métodos podem ser sobrecarregados quando um método tem um parâmetro `ref`, `in` ou `out` e o outro tem um parâmetro de valor, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="2b2d1-129">Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `in`, `ref` e `out` fazem parte da assinatura e não são correspondentes.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="2b2d1-130">Propriedades não são variáveis.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-130">Properties are not variables.</span></span> <span data-ttu-id="2b2d1-131">Elas são métodos e não podem ser passadas para parâmetros `ref`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="2b2d1-132">Não é possível usar as palavras-chave `ref`, `in` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="2b2d1-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="2b2d1-133">Métodos assíncronos, que você define usando o modificador [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="2b2d1-134">Métodos de iterador, que incluem uma instrução [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="2b2d1-135">Passando um argumento por referência: Um exemplo</span><span class="sxs-lookup"><span data-stu-id="2b2d1-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="2b2d1-136">Os exemplos anteriores passam tipos de valor por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="2b2d1-137">Você também pode usar a palavra-chave `ref` para passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="2b2d1-138">Passar um tipo de referência por referência permite que o método chamado substitua o objeto ao qual se refere o parâmetro de referência no chamador.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="2b2d1-139">O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="2b2d1-140">Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="2b2d1-141">O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="2b2d1-142">Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="2b2d1-143">Valores retornados por referência</span><span class="sxs-lookup"><span data-stu-id="2b2d1-143">Reference return values</span></span>

<span data-ttu-id="2b2d1-144">Valores retornados por referência (ou ref returns) são valores que um método retorna por referência para o chamador.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="2b2d1-145">Ou seja, o chamador pode modificar o valor retornado por um método e essa alteração será refletida no estado do objeto que contém o método.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="2b2d1-146">Um valor retornado por referência é definido usando a palavra-chave `ref`:</span><span class="sxs-lookup"><span data-stu-id="2b2d1-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="2b2d1-147">Na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-147">In the method signature.</span></span> <span data-ttu-id="2b2d1-148">Por exemplo, a assinatura de método a seguir indica que o método `GetCurrentPrice` retorna um valor <xref:System.Decimal> por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="2b2d1-149">Entre o token `return` e a variável retornada em uma instrução `return` no método.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="2b2d1-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b2d1-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="2b2d1-151">Para que o chamador modifique o estado do objeto, o valor retornado de referência deve ser armazenado em uma variável que é definida explicitamente como um [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="2b2d1-152">O método chamado também poderá declarar o valor retornado como `ref readonly` para retornar o valor por referência e, em seguida, impor que o código de chamada não possa modificar o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="2b2d1-153">O método de chamada pode evitar a cópia retornada com um valor ao armazenar o valor em um local [ref readonly](#ref-readonly-locals) variável.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="2b2d1-154">Para obter um exemplo, consulte [Um exemplo de ref returns e ref locals](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="2b2d1-155">Ref locals</span><span class="sxs-lookup"><span data-stu-id="2b2d1-155">Ref locals</span></span>

<span data-ttu-id="2b2d1-156">Uma variável de ref local é usada para fazer referência a valores retornados usando `return ref`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="2b2d1-157">Uma variável local ref não pode ser inicializada para um valor retornado que não seja ref.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="2b2d1-158">Em outras palavras, o lado direito da inicialização deve ser uma referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="2b2d1-159">Todas as modificações ao valor do ref local são refletidas no estado do objeto cujo método retornou o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="2b2d1-160">Você define um ref local usando a palavra-chave `ref` antes da declaração de variável, bem como imediatamente antes da chamada para o método que retorna o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="2b2d1-161">Por exemplo, a instrução a seguir define um valor de ref local que é retornado por um método chamado `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="2b2d1-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="2b2d1-162">Você pode acessar um valor por referência da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="2b2d1-163">Em alguns casos, acessar um valor por referência aumenta o desempenho, evitando uma operação de cópia potencialmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="2b2d1-164">Por exemplo, a instrução a seguir mostra como é possível definir um valor de local de ref que é usado para fazer referência a um valor.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="2b2d1-165">Observe que, nos dois exemplos, a palavra-chave `ref` deve ser usada em ambos os locais ou o compilador gera o erro CS8172, "Não é possível inicializar uma variável por referência com um valor".</span><span class="sxs-lookup"><span data-stu-id="2b2d1-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="2b2d1-166">A partir do C# 7.3, a variável de iteração da instrução `foreach` pode ser ref local ou a variável local ref readonly.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="2b2d1-167">Para saber mais, confira o artigo [Instrução foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="2b2d1-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="2b2d1-168">Locais somente leitura de referência</span><span class="sxs-lookup"><span data-stu-id="2b2d1-168">Ref readonly locals</span></span>

<span data-ttu-id="2b2d1-169">Um local ref readonly é usado para fazer referência a valores retornados pelo método ou propriedade que tem `ref readonly` na sua assinatura e usa `return ref`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="2b2d1-170">Uma variável `ref readonly` combina as propriedades de uma variável `ref` local com uma variável `readonly`: é um alias para o armazenamento ao qual está atribuído e não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="2b2d1-171">Um exemplo de ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="2b2d1-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="2b2d1-172">O exemplo a seguir define uma classe `Book` que tem dois campos <xref:System.String>, `Title` e `Author`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="2b2d1-173">Ele também define uma classe `BookCollection` que inclui uma matriz privada de objetos `Book`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="2b2d1-174">Objetos de catálogo individuais são retornados por referência chamando o respectivo método `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="2b2d1-175">Quando o chamador armazena o valor retornado pelo método `GetBookByTitle` como um ref local, as alterações que o chamador faz ao valor retornado são refletidas no objeto `BookCollection`, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="2b2d1-176">Tipos struct de referência</span><span class="sxs-lookup"><span data-stu-id="2b2d1-176">Ref struct types</span></span>

<span data-ttu-id="2b2d1-177">Adicionar o modificador `ref` a uma declaração `struct` define que instâncias desse tipo devem ser alocadas por pilha.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="2b2d1-178">Em outras palavras, instâncias desses tipos nunca podem ser criados no heap como um membro de outra classe.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="2b2d1-179">A principal motivação para esse recurso foi <xref:System.Span%601> e as estruturas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="2b2d1-180">A meta de manter um tipo `ref struct` como uma variável alocada na pilha apresenta várias regras que o compilador aplica para todos os tipos `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="2b2d1-181">Você não pode encaixotar um `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="2b2d1-182">Você não pode atribuir um tipo `ref struct` a uma variável do tipo `object`, `dynamic` ou de qualquer tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="2b2d1-183">Tipos `ref struct` não podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-183">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="2b2d1-184">Você não pode declarar um `ref struct` como um membro de uma classe ou de um struct normal.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-184">You can't declare a `ref struct` as a member of a class or a normal struct.</span></span>
- <span data-ttu-id="2b2d1-185">Você não pode declarar variáveis locais que são do tipo `ref struct` em métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-185">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="2b2d1-186">Você pode declará-las em métodos síncronos que retornam tipos semelhantes a <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `Task`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-186">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="2b2d1-187">Você não pode declarar as variáveis locais `ref struct` em iteradores.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-187">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="2b2d1-188">Você não pode capturar as variáveis `ref struct` em expressões lambda ou em funções locais.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-188">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="2b2d1-189">Essas restrições garantem que você não use acidentalmente um `ref struct` de maneira que possa promovê-lo para o heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-189">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="2b2d1-190">Você pode combinar modificadores para declarar um struct como `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-190">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="2b2d1-191">Um `readonly ref struct` combina os benefícios e as restrições de declarações `ref struct` e `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="2b2d1-191">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2b2d1-192">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2b2d1-192">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b2d1-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b2d1-193">See also</span></span>

- [<span data-ttu-id="2b2d1-194">Escrever código eficiente seguro</span><span class="sxs-lookup"><span data-stu-id="2b2d1-194">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="2b2d1-195">Retornos de ref e locais de ref</span><span class="sxs-lookup"><span data-stu-id="2b2d1-195">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="2b2d1-196">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="2b2d1-196">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="2b2d1-197">Operador de atribuição ref</span><span class="sxs-lookup"><span data-stu-id="2b2d1-197">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="2b2d1-198">Passando parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b2d1-198">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="2b2d1-199">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="2b2d1-199">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="2b2d1-200">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="2b2d1-200">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2b2d1-201">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2b2d1-201">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2b2d1-202">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="2b2d1-202">C# Keywords</span></span>](index.md)
