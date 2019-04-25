---
title: is – Referência de C#
ms.custom: seodec18
ms.date: 04/09/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 9fb57caeafde9db5759300d938a85f4abf4d05f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672453"
---
# <a name="is-c-reference"></a><span data-ttu-id="80978-102">is (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="80978-102">is (C# Reference)</span></span>

<span data-ttu-id="80978-103">Verifica se um objeto é compatível com um determinado tipo ou (começando com o C# 7.0) testa uma expressão em relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="80978-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="80978-104">Testando a compatibilidade de tipo</span><span class="sxs-lookup"><span data-stu-id="80978-104">Testing for type compatibility</span></span>

<span data-ttu-id="80978-105">A palavra-chave `is` avalia a compatibilidade de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="80978-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="80978-106">Ela determina se uma instância de objeto ou o resultado de uma expressão pode ser convertido em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="80978-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="80978-107">Ela tem a sintaxe</span><span class="sxs-lookup"><span data-stu-id="80978-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="80978-108">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, e *type* é o nome do tipo no qual o resultado de *expr* será convertido.</span><span class="sxs-lookup"><span data-stu-id="80978-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="80978-109">A instrução `is` será `true` se *expr* não for nulo e o objeto resultante da avaliação da expressão puder ser convertido em *type*; caso contrário, ela retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="80978-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="80978-110">Por exemplo, o código a seguir determina se `obj` pode ser convertido em uma instância do tipo `Person`:</span><span class="sxs-lookup"><span data-stu-id="80978-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="80978-111">A instrução `is` será verdadeira se:</span><span class="sxs-lookup"><span data-stu-id="80978-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="80978-112">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="80978-113">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="80978-114">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="80978-115">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="80978-116">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="80978-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="80978-117">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="80978-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="80978-118">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="80978-119">O exemplo a seguir mostra que a expressão `is` é avaliada como `true` para cada uma dessas conversões.</span><span class="sxs-lookup"><span data-stu-id="80978-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="80978-120">A palavra-chave `is` gera um aviso de tempo de compilação caso seja conhecido que a expressão sempre é `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="80978-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="80978-121">Ela considera somente conversões de referência, conversões boxing e conversões unboxing, e não considera conversões definidas pelo usuário ou conversões definidas pelos operadores [implicit](implicit.md) e [explicit](explicit.md) de um tipo.</span><span class="sxs-lookup"><span data-stu-id="80978-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="80978-122">O exemplo a seguir gera avisos porque o resultado da conversão é conhecido em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="80978-122">The following example generates warnings because the result of the conversion is known at compile time.</span></span> <span data-ttu-id="80978-123">A expressão `is` para conversões de `int` para `long` e `double` retorna falso porque essas conversões são tratadas pelo operador [implicit](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="80978-123">The `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="80978-124">`expr` não pode ser um método anônimo ou uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="80978-124">`expr` cannot be an anonymous method or lambda expression.</span></span> <span data-ttu-id="80978-125">Pode ser qualquer outra expressão que retorne um valor.</span><span class="sxs-lookup"><span data-stu-id="80978-125">It can be any other expression that returns a value.</span></span> <span data-ttu-id="80978-126">O exemplo a seguir usa `is` para avaliar o valor retornado de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="80978-126">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="80978-127">Começando com o C# 7.0, você pode usar a correspondência de padrões com o [padrão de tipo](#type) para escrever códigos mais concisos que usam a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="80978-127">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="80978-128">Correspondência de padrões com `is`</span><span class="sxs-lookup"><span data-stu-id="80978-128">Pattern matching with `is`</span></span>

<span data-ttu-id="80978-129">Começando com o C# 7.0, as instruções `is` e [switch](../../../csharp/language-reference/keywords/switch.md) permitem a correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="80978-129">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="80978-130">A palavra-chave `is` dá suporte aos seguintes padrões:</span><span class="sxs-lookup"><span data-stu-id="80978-130">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="80978-131">[Padrão de tipo](#type), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="80978-131">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="80978-132">[Padrão constante](#constant), que testa se uma expressão é avaliada como um valor constante especificado.</span><span class="sxs-lookup"><span data-stu-id="80978-132">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="80978-133">[Padrão var](#var), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local.</span><span class="sxs-lookup"><span data-stu-id="80978-133">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <a name="a-nametype-type-pattern"></a><span data-ttu-id="80978-134"><a name="type" />Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="80978-134"><a name="type" />Type pattern</span></span>

<span data-ttu-id="80978-135">Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="80978-135">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="80978-136">Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas.</span><span class="sxs-lookup"><span data-stu-id="80978-136">It's a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="80978-137">A forma geral do padrão de tipo `is` é:</span><span class="sxs-lookup"><span data-stu-id="80978-137">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="80978-138">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, *type* é o nome do tipo no qual o resultado de *expr* será convertido e *varname* é o objeto no qual o resultado de *expr* será convertido se o teste `is` for `true`.</span><span class="sxs-lookup"><span data-stu-id="80978-138">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="80978-139">A expressão `is` será `true` se *expr* não for `null` e qualquer um dos seguintes for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="80978-139">The `is` expression is `true` if *expr* isn't `null`, and any of the following is true:</span></span>

- <span data-ttu-id="80978-140">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-140">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="80978-141">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-141">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="80978-142">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-142">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="80978-143">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-143">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="80978-144">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="80978-144">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="80978-145">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="80978-145">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="80978-146">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="80978-146">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="80978-147">A partir do C# 7.1, *expr* pode ter um tipo de tempo de compilação definido por um parâmetro de tipo genérico e suas restrições.</span><span class="sxs-lookup"><span data-stu-id="80978-147">Beginning with C# 7.1, *expr* may have a compile-time type defined by a generic type parameter and its constraints.</span></span> 

<span data-ttu-id="80978-148">Se *expr* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído e terá escopo local somente dentro da instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="80978-148">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="80978-149">O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> de um tipo.</span><span class="sxs-lookup"><span data-stu-id="80978-149">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="80978-150">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="80978-150">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="80978-151">O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.</span><span class="sxs-lookup"><span data-stu-id="80978-151">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="80978-152">O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="80978-152">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="80978-153">O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada.</span><span class="sxs-lookup"><span data-stu-id="80978-153">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="80978-154">O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="80978-154">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="80978-155"><a name="constant" /> Padrão constante</span><span class="sxs-lookup"><span data-stu-id="80978-155"><a name="constant" /> Constant pattern</span></span>

<span data-ttu-id="80978-156">Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="80978-156">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="80978-157">No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="80978-157">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="80978-158">A partir do C# 7.0, ele também é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="80978-158">Starting with C# 7.0, it's supported by the `is` statement as well.</span></span> <span data-ttu-id="80978-159">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="80978-159">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="80978-160">em que *expr* é a expressão a ser avaliada e *constant* é o valor a ser testado.</span><span class="sxs-lookup"><span data-stu-id="80978-160">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="80978-161">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="80978-161">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="80978-162">Um valor literal.</span><span class="sxs-lookup"><span data-stu-id="80978-162">A literal value.</span></span>

- <span data-ttu-id="80978-163">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="80978-163">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="80978-164">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="80978-164">An enumeration constant.</span></span>

<span data-ttu-id="80978-165">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="80978-165">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="80978-166">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="80978-166">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="80978-167">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="80978-167">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="80978-168">O exemplo a seguir combina os padrões de tipo e constante para testar se um objeto é uma instância de `Dice` e, caso seja, para determinar se o valor de uma distribuição de dados é 6.</span><span class="sxs-lookup"><span data-stu-id="80978-168">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="80978-169">É possível verificar em busca de `null` usando o padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="80978-169">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="80978-170">A palavra-chave `null` é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="80978-170">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="80978-171">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="80978-171">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="80978-172">O exemplo a seguir demonstra uma comparação de verificações de `null`:</span><span class="sxs-lookup"><span data-stu-id="80978-172">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="80978-173"><a name="var" /> Padrão var </a></span><span class="sxs-lookup"><span data-stu-id="80978-173"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="80978-174">O padrão `var` é um catch-all para qualquer tipo ou valor.</span><span class="sxs-lookup"><span data-stu-id="80978-174">The `var` pattern is a catch-all for any type or value.</span></span> <span data-ttu-id="80978-175">O valor de *expr* é sempre atribuído a uma variável local do mesmo tipo que o tipo de tempo de compilação de *expr*.</span><span class="sxs-lookup"><span data-stu-id="80978-175">The value of *expr* is always assigned to a local variable the same type as the compile time type of *expr*.</span></span> <span data-ttu-id="80978-176">O resultado da expressão `is` é sempre `true`.</span><span class="sxs-lookup"><span data-stu-id="80978-176">The result of the `is` expression is always `true`.</span></span> <span data-ttu-id="80978-177">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="80978-177">Its syntax is:</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="80978-178">O exemplo a seguir usa o padrão var para atribuir uma expressão a uma variável chamada `obj`.</span><span class="sxs-lookup"><span data-stu-id="80978-178">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="80978-179">Em seguida, ele exibe o valor e o tipo de `obj`.</span><span class="sxs-lookup"><span data-stu-id="80978-179">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="80978-180">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="80978-180">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80978-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80978-181">See also</span></span>

- [<span data-ttu-id="80978-182">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="80978-182">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="80978-183">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="80978-183">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="80978-184">typeof</span><span class="sxs-lookup"><span data-stu-id="80978-184">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)
- [<span data-ttu-id="80978-185">as</span><span class="sxs-lookup"><span data-stu-id="80978-185">as</span></span>](../../../csharp/language-reference/keywords/as.md)
- [<span data-ttu-id="80978-186">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="80978-186">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
