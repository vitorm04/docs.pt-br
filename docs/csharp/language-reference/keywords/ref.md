---
title: Palavra-chave ref – Referência de C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 07e1b49605c83908f7b9af25e0cb2599a97257c5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102067"
---
# <a name="ref-c-reference"></a><span data-ttu-id="87700-102">ref (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="87700-102">ref (C# Reference)</span></span>

<span data-ttu-id="87700-103">A palavra-chave `ref` indica um valor que é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="87700-104">Ela é usada em quatro contextos diferentes:</span><span class="sxs-lookup"><span data-stu-id="87700-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="87700-105">Em uma assinatura de método e em uma chamada de método, para passar um argumento a um método por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="87700-106">Para obter mais informações, veja [Passar um argumento por referência](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="87700-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="87700-107">Em uma assinatura de método para retornar um valor para o chamador por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="87700-108">Para obter mais informações, consulte [Reference return values](#reference-return-values) (Valores retornados de referência).</span><span class="sxs-lookup"><span data-stu-id="87700-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="87700-109">Em um corpo de membro, para indicar que um valor retornado por referência é armazenado localmente como uma referência que o chamador pretende modificar ou, em geral, uma variável local acessa outro valor por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="87700-110">Para obter mais informações, veja [Locais de referência](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="87700-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="87700-111">Em uma declaração `struct` para declarar um `ref struct` ou um `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="87700-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="87700-112">Para obter mais [ `ref` ](../builtin-types/struct.md#ref-struct) informações, consulte a seção de estrutura do artigo [Tipos de Estrutura.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="87700-112">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="87700-113">Passando um argumento por referência</span><span class="sxs-lookup"><span data-stu-id="87700-113">Passing an argument by reference</span></span>

<span data-ttu-id="87700-114">Quando usado na lista de parâmetros do método, a palavra-chave `ref` indica que um argumento é passado por referência, não por valor.</span><span class="sxs-lookup"><span data-stu-id="87700-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="87700-115">A palavra-chave `ref` torna o parâmetro formal um alias para o argumento, que deve ser uma variável.</span><span class="sxs-lookup"><span data-stu-id="87700-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="87700-116">Em outras palavras, qualquer operação no parâmetro é feita no argumento.</span><span class="sxs-lookup"><span data-stu-id="87700-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="87700-117">Por exemplo, se o chamador passar uma expressão de variável local ou uma expressão de acesso a elemento de matriz, e o método chamado substituir o objeto ao qual o parâmetro de ref se refere, então a variável local do chamador ou o elemento de matriz agora se refere ao novo objeto quando o método retorna.</span><span class="sxs-lookup"><span data-stu-id="87700-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="87700-118">Não confunda o conceito de passar por referência com o conceito de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="87700-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="87700-119">Os dois conceitos não são iguais.</span><span class="sxs-lookup"><span data-stu-id="87700-119">The two concepts are not the same.</span></span> <span data-ttu-id="87700-120">Um parâmetro de método pode ser modificado por `ref`, independentemente de ele ser um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="87700-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="87700-121">Não há nenhuma conversão boxing de um tipo de valor quando ele é passado por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="87700-122">Para usar um parâmetro `ref`, a definição do método e o método de chamada devem usar explicitamente a palavra-chave `ref`, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="87700-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="87700-123">Um argumento passado para um parâmetro `ref` ou `in` precisa ser inicializado antes de ser passado.</span><span class="sxs-lookup"><span data-stu-id="87700-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="87700-124">Isso é diferente dos parâmetros [out](out-parameter-modifier.md), cujos argumentos não precisam ser inicializados explicitamente antes de serem passados.</span><span class="sxs-lookup"><span data-stu-id="87700-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="87700-125">Os membros de uma classe não podem ter assinaturas que se diferem somente por `ref`, `in` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="87700-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="87700-126">Ocorrerá um erro de compilador se a única diferença entre os dois membros de um tipo for que um deles tem um parâmetro `ref` e o outro tem um parâmetro `out` ou `in`.</span><span class="sxs-lookup"><span data-stu-id="87700-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="87700-127">O código a seguir, por exemplo, não é compilado.</span><span class="sxs-lookup"><span data-stu-id="87700-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="87700-128">No entanto, os métodos podem ser sobrecarregados quando um método tem um parâmetro `ref`, `in` ou `out` e o outro tem um parâmetro de valor, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="87700-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="87700-129">Em outras situações que exigem correspondência de assinatura, como ocultar ou substituir, `in`, `ref` e `out` fazem parte da assinatura e não são correspondentes.</span><span class="sxs-lookup"><span data-stu-id="87700-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="87700-130">Propriedades não são variáveis.</span><span class="sxs-lookup"><span data-stu-id="87700-130">Properties are not variables.</span></span> <span data-ttu-id="87700-131">Elas são métodos e não podem ser passadas para parâmetros `ref`.</span><span class="sxs-lookup"><span data-stu-id="87700-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="87700-132">Não é possível usar as palavras-chave `ref`, `in` e `out` para os seguintes tipos de métodos:</span><span class="sxs-lookup"><span data-stu-id="87700-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="87700-133">Métodos assíncronos, que você define usando o modificador [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="87700-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="87700-134">Métodos de iterador, que incluem uma instrução [yield return](yield.md) ou `yield break`.</span><span class="sxs-lookup"><span data-stu-id="87700-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="87700-135">Além disso, [os métodos de extensão](../../programming-guide/classes-and-structs/extension-methods.md) têm as seguintes restrições:</span><span class="sxs-lookup"><span data-stu-id="87700-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="87700-136">A `out` palavra-chave não pode ser usada no primeiro argumento de um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="87700-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="87700-137">A `ref` palavra-chave não pode ser usada no primeiro argumento de um método de extensão quando o argumento não é uma estrutura, ou um tipo genérico não constrangido a ser uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="87700-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="87700-138">A `in` palavra-chave não pode ser usada a menos que o primeiro argumento seja uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="87700-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="87700-139">A `in` palavra-chave não pode ser usada em qualquer tipo genérico, mesmo quando constrangida a ser uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="87700-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="87700-140">Passando um argumento por referência: um exemplo</span><span class="sxs-lookup"><span data-stu-id="87700-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="87700-141">Os exemplos anteriores passam tipos de valor por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="87700-142">Você também pode usar a palavra-chave `ref` para passar tipos de referência por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="87700-143">Passar um tipo de referência por referência permite que o método chamado substitua o objeto ao qual se refere o parâmetro de referência no chamador.</span><span class="sxs-lookup"><span data-stu-id="87700-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="87700-144">O local de armazenamento do objeto é passado para o método como o valor do parâmetro de referência.</span><span class="sxs-lookup"><span data-stu-id="87700-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="87700-145">Se você alterar o valor no local de armazenamento do parâmetro (para apontar para um novo objeto), irá alterar também o local de armazenamento ao qual se refere o chamador.</span><span class="sxs-lookup"><span data-stu-id="87700-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="87700-146">O exemplo a seguir passa uma instância de um tipo de referência como um parâmetro `ref`.</span><span class="sxs-lookup"><span data-stu-id="87700-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="87700-147">Para obter mais informações sobre como passar tipos de referência por valor e por referência, consulte [Passando parâmetros de tipo de referência](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="87700-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="87700-148">Valores retornados por referência</span><span class="sxs-lookup"><span data-stu-id="87700-148">Reference return values</span></span>

<span data-ttu-id="87700-149">Valores retornados por referência (ou ref returns) são valores que um método retorna por referência para o chamador.</span><span class="sxs-lookup"><span data-stu-id="87700-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="87700-150">Ou seja, o chamador pode modificar o valor retornado por um método, e essa alteração se reflete no estado do objeto no método de chamada.</span><span class="sxs-lookup"><span data-stu-id="87700-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="87700-151">Um valor retornado por referência é definido usando a palavra-chave `ref`:</span><span class="sxs-lookup"><span data-stu-id="87700-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="87700-152">Na assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="87700-152">In the method signature.</span></span> <span data-ttu-id="87700-153">Por exemplo, a assinatura de método a seguir indica que o método `GetCurrentPrice` retorna um valor <xref:System.Decimal> por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="87700-154">Entre o token `return` e a variável retornada em uma instrução `return` no método.</span><span class="sxs-lookup"><span data-stu-id="87700-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="87700-155">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="87700-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="87700-156">Para que o chamador modifique o estado do objeto, o valor retornado de referência deve ser armazenado em uma variável que é definida explicitamente como um [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="87700-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="87700-157">Aqui está um exemplo de retorno mais completo do ref, mostrando tanto a assinatura do método quanto o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="87700-157">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="87700-158">O método chamado também poderá declarar o valor retornado como `ref readonly` para retornar o valor por referência e, em seguida, impor que o código de chamada não possa modificar o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="87700-158">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="87700-159">O método de chamada pode evitar a cópia retornada com um valor ao armazenar o valor em um local [ref readonly](#ref-readonly-locals) variável.</span><span class="sxs-lookup"><span data-stu-id="87700-159">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="87700-160">Por exemplo, veja [A ref returns e ref locals exemplo](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="87700-160">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="87700-161">Ref locals</span><span class="sxs-lookup"><span data-stu-id="87700-161">Ref locals</span></span>

<span data-ttu-id="87700-162">Uma variável de ref local é usada para fazer referência a valores retornados usando `return ref`.</span><span class="sxs-lookup"><span data-stu-id="87700-162">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="87700-163">Uma variável local ref não pode ser inicializada para um valor retornado que não seja ref.</span><span class="sxs-lookup"><span data-stu-id="87700-163">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="87700-164">Em outras palavras, o lado direito da inicialização deve ser uma referência.</span><span class="sxs-lookup"><span data-stu-id="87700-164">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="87700-165">Todas as modificações ao valor do ref local são refletidas no estado do objeto cujo método retornou o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-165">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="87700-166">Você define um ref local usando a palavra-chave `ref` antes da declaração de variável, bem como imediatamente antes da chamada para o método que retorna o valor por referência.</span><span class="sxs-lookup"><span data-stu-id="87700-166">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="87700-167">Por exemplo, a instrução a seguir define um valor de ref local que é retornado por um método chamado `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="87700-167">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="87700-168">Você pode acessar um valor por referência da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="87700-168">You can access a value by reference in the same way.</span></span> <span data-ttu-id="87700-169">Em alguns casos, acessar um valor por referência aumenta o desempenho, evitando uma operação de cópia potencialmente dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="87700-169">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="87700-170">Por exemplo, a instrução a seguir mostra como é possível definir um valor de local de ref que é usado para fazer referência a um valor.</span><span class="sxs-lookup"><span data-stu-id="87700-170">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="87700-171">Em ambos os `ref` exemplos, a palavra-chave deve ser usada em ambos os lugares, ou o compilador gera erro CS8172, "Não é possível inicializar uma variável por referência com um valor."</span><span class="sxs-lookup"><span data-stu-id="87700-171">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="87700-172">A partir do C# 7.3, a variável de iteração da instrução `foreach` pode ser ref local ou a variável local ref readonly.</span><span class="sxs-lookup"><span data-stu-id="87700-172">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="87700-173">Para saber mais, confira o artigo [Instrução foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="87700-173">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="87700-174">Também começando com C# 7.3, você pode reatribuir um árbitro local ou ref readonly variável local com o [operador de atribuição de ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="87700-174">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="87700-175">Locais somente leitura de referência</span><span class="sxs-lookup"><span data-stu-id="87700-175">Ref readonly locals</span></span>

<span data-ttu-id="87700-176">Um local ref readonly é usado para fazer referência a valores retornados pelo método ou propriedade que tem `ref readonly` na sua assinatura e usa `return ref`.</span><span class="sxs-lookup"><span data-stu-id="87700-176">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="87700-177">Uma variável `ref readonly` combina as propriedades de uma variável `ref` local com uma variável `readonly`: é um alias para o armazenamento ao qual está atribuído e não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="87700-177">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="87700-178">Um exemplo de ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="87700-178">A ref returns and ref locals example</span></span>

<span data-ttu-id="87700-179">O exemplo a seguir define uma classe `Book` que tem dois campos <xref:System.String>, `Title` e `Author`.</span><span class="sxs-lookup"><span data-stu-id="87700-179">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="87700-180">Ele também define uma classe `BookCollection` que inclui uma matriz privada de objetos `Book`.</span><span class="sxs-lookup"><span data-stu-id="87700-180">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="87700-181">Objetos de catálogo individuais são retornados por referência chamando o respectivo método `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="87700-181">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="87700-182">Quando o chamador armazena o valor retornado pelo método `GetBookByTitle` como um ref local, as alterações que o chamador faz ao valor retornado são refletidas no objeto `BookCollection`, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="87700-182">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="87700-183">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="87700-183">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87700-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="87700-184">See also</span></span>

- [<span data-ttu-id="87700-185">Escreva um código eficiente seguro</span><span class="sxs-lookup"><span data-stu-id="87700-185">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="87700-186">Ref returns e ref locals</span><span class="sxs-lookup"><span data-stu-id="87700-186">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="87700-187">Expressão condicional ref</span><span class="sxs-lookup"><span data-stu-id="87700-187">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="87700-188">Parâmetros de passagem</span><span class="sxs-lookup"><span data-stu-id="87700-188">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="87700-189">Parâmetros de método</span><span class="sxs-lookup"><span data-stu-id="87700-189">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="87700-190">C# Referência</span><span class="sxs-lookup"><span data-stu-id="87700-190">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="87700-191">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="87700-191">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="87700-192">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="87700-192">C# Keywords</span></span>](index.md)
