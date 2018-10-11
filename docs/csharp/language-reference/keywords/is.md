---
title: is (Referência de C#)
ms.date: 02/17/2017
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 8e4103f8e71858ec74c348ee1f675828e6468eb2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170581"
---
# <a name="is-c-reference"></a><span data-ttu-id="1f5e1-102">is (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1f5e1-102">is (C# Reference)</span></span> #

<span data-ttu-id="1f5e1-103">Verifica se um objeto é compatível com um determinado tipo ou (começando com o C# 7.0) testa uma expressão em relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-103">Checks if an object is compatible with a given type, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="1f5e1-104">Testando a compatibilidade de tipo</span><span class="sxs-lookup"><span data-stu-id="1f5e1-104">Testing for type compatibility</span></span> ##

<span data-ttu-id="1f5e1-105">A palavra-chave `is` avalia a compatibilidade de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-105">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="1f5e1-106">Ela determina se uma instância de objeto ou o resultado de uma expressão pode ser convertido em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-106">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="1f5e1-107">Ela tem a sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f5e1-107">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="1f5e1-108">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, e *type* é o nome do tipo no qual o resultado de *expr* será convertido.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-108">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="1f5e1-109">A instrução `is` será `true` se *expr* não for nulo e o objeto resultante da avaliação da expressão puder ser convertido em *type*; caso contrário, ela retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-109">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="1f5e1-110">Por exemplo, o código a seguir determina se `obj` pode ser convertido em uma instância do tipo `Person`:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-110">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

[!code-csharp[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

<span data-ttu-id="1f5e1-111">A instrução `is` será verdadeira se:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-111">The `is` statement is true if:</span></span>

- <span data-ttu-id="1f5e1-112">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-112">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1f5e1-113">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-113">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1f5e1-114">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-114">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1f5e1-115">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-115">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1f5e1-116">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-116">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="1f5e1-117">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-117">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1f5e1-118">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-118">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1f5e1-119">O exemplo a seguir mostra que a expressão `is` é avaliada como `true` para cada uma dessas conversões.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-119">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

[!code-csharp[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

<span data-ttu-id="1f5e1-120">A palavra-chave `is` gera um aviso de tempo de compilação caso seja conhecido que a expressão sempre é `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-120">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="1f5e1-121">Ela considera somente conversões de referência, conversões boxing e conversões unboxing, e não considera conversões definidas pelo usuário ou conversões definidas pelos operadores [implicit](implicit.md) e [explicit](explicit.md) de um tipo.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-121">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="1f5e1-122">O exemplo a seguir gera avisos porque o resultado da conversão é conhecido em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-122">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="1f5e1-123">Observe que a expressão `is` para conversões de `int` para `long` e `double` retorna falso, pois essas conversões são tratadas pelo operador [implicit](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="1f5e1-123">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

[!code-csharp[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

<span data-ttu-id="1f5e1-124">`expr` pode ser qualquer expressão que retorna um valor, com exceção de métodos anônimos e expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-124">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="1f5e1-125">O exemplo a seguir usa `is` para avaliar o valor retornado de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-125">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
[!code-csharp[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

<span data-ttu-id="1f5e1-126">Começando com o C# 7.0, você pode usar a correspondência de padrões com o [padrão de tipo](#type) para escrever códigos mais concisos que usam a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-126">Starting with C# 7.0, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="1f5e1-127">Correspondência de padrões com `is`</span><span class="sxs-lookup"><span data-stu-id="1f5e1-127">Pattern matching with `is`</span></span> ##

<span data-ttu-id="1f5e1-128">Começando com o C# 7.0, as instruções `is` e [switch](../../../csharp/language-reference/keywords/switch.md) permitem a correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-128">Starting with C# 7.0, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="1f5e1-129">A palavra-chave `is` dá suporte aos seguintes padrões:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-129">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="1f5e1-130">[Padrão de tipo](#type), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-130">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="1f5e1-131">[Padrão constante](#constant), que testa se uma expressão é avaliada como um valor constante especificado.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-131">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="1f5e1-132">[Padrão var](#var), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-132">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="1f5e1-133"><a name="type" /> Padrão de tipo </a></span><span class="sxs-lookup"><span data-stu-id="1f5e1-133"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="1f5e1-134">Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-134">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="1f5e1-135">Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-135">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="1f5e1-136">A forma geral do padrão de tipo `is` é:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-136">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="1f5e1-137">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, *type* é o nome do tipo no qual o resultado de *expr* será convertido e *varname* é o objeto no qual o resultado de *expr* será convertido se o teste `is` for `true`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-137">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="1f5e1-138">A expressão `is` será `true` se *expr* não for `null` e qualquer um dos seguintes for verdadeiro:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-138">The `is` expression is `true` if *expr* is not `null`, and any of the following is true:</span></span>

- <span data-ttu-id="1f5e1-139">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-139">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="1f5e1-140">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-140">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="1f5e1-141">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-141">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="1f5e1-142">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-142">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="1f5e1-143">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-143">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="1f5e1-144">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-144">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="1f5e1-145">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-145">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="1f5e1-146">Se *expr* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído e terá escopo local somente dentro da instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-146">If *expr* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="1f5e1-147">O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> de um tipo.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-147">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> method.</span></span>

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

<span data-ttu-id="1f5e1-148">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-148">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="1f5e1-149">O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-149">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

<span data-ttu-id="1f5e1-150">O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-150">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="1f5e1-151">O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-151">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

<span data-ttu-id="1f5e1-152">O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-152">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="1f5e1-153"><a name="constant" /> Padrão constante</span><span class="sxs-lookup"><span data-stu-id="1f5e1-153"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="1f5e1-154">Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-154">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="1f5e1-155">No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="1f5e1-155">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="1f5e1-156">Começando com o C# 7.0, ele também é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-156">Starting with C# 7.0, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="1f5e1-157">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-157">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="1f5e1-158">em que *expr* é a expressão a ser avaliada e *constant* é o valor a ser testado.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-158">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="1f5e1-159">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-159">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="1f5e1-160">Um valor literal.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-160">A literal value.</span></span>

- <span data-ttu-id="1f5e1-161">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-161">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="1f5e1-162">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-162">An enumeration constant.</span></span>

<span data-ttu-id="1f5e1-163">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-163">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="1f5e1-164">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="1f5e1-164">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="1f5e1-165">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="1f5e1-165">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="1f5e1-166">O exemplo a seguir combina os padrões de tipo e constante para testar se um objeto é uma instância de `Dice` e, caso seja, para determinar se o valor de uma distribuição de dados é 6.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-166">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

<span data-ttu-id="1f5e1-167">É possível verificar em busca de `null` usando o padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-167">Checking for `null` can be performed using the constant pattern.</span></span> <span data-ttu-id="1f5e1-168">A palavra-chave `null` é compatível com a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-168">The `null` keyword is supported by the `is` statement.</span></span> <span data-ttu-id="1f5e1-169">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-169">Its syntax is:</span></span>

```csharp 
   expr is null
```

<span data-ttu-id="1f5e1-170">O exemplo a seguir demonstra uma comparação de verificações de `null`:</span><span class="sxs-lookup"><span data-stu-id="1f5e1-170">The following example shows a comparison of `null` checks:</span></span>

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]
 
### <span data-ttu-id="1f5e1-171"><a name="var" /> Padrão var </a></span><span class="sxs-lookup"><span data-stu-id="1f5e1-171"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="1f5e1-172">Uma correspondência de padrões com o padrão var sempre terá êxito.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-172">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="1f5e1-173">Sua sintaxe é</span><span class="sxs-lookup"><span data-stu-id="1f5e1-173">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="1f5e1-174">em que o valor de *expr* sempre é atribuído a uma variável local chamada *varname*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-174">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="1f5e1-175">*varname* é uma variável estática do mesmo tipo que *expr*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-175">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="1f5e1-176">O exemplo a seguir usa o padrão var para atribuir uma expressão a uma variável chamada `obj`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-176">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="1f5e1-177">Em seguida, ele exibe o valor e o tipo de `obj`.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-177">It then displays the value and the type of `obj`.</span></span>

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

<span data-ttu-id="1f5e1-178">Observe que, se *expr* for `null`, a expressão `is` ainda será verdadeira e atribuirá `null` a *varname*.</span><span class="sxs-lookup"><span data-stu-id="1f5e1-178">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="1f5e1-179">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1f5e1-179">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f5e1-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f5e1-180">See also</span></span>

- [<span data-ttu-id="1f5e1-181">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1f5e1-181">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1f5e1-182">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1f5e1-182">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="1f5e1-183">typeof</span><span class="sxs-lookup"><span data-stu-id="1f5e1-183">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
- [<span data-ttu-id="1f5e1-184">as</span><span class="sxs-lookup"><span data-stu-id="1f5e1-184">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
- [<span data-ttu-id="1f5e1-185">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="1f5e1-185">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
