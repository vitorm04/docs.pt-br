---
title: "is (Referência de C#)"
keywords: palavra-chave is (C#), is (C#)
ms.date: 2017-02-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
dev_langs:
- CSharp
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
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
ms.openlocfilehash: 58b18284b12ca0c636ed3fa923c43d94f202597f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="is-c-reference"></a><span data-ttu-id="e8475-103">is (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e8475-103">is (C# Reference)</span></span> #

<span data-ttu-id="e8475-104">Verifica se um objeto é compatível com um determinado tipo ou (a partir do C# 7) testa uma expressão com relação a um padrão.</span><span class="sxs-lookup"><span data-stu-id="e8475-104">Checks if an object is compatible with a given type, or (starting with C# 7) tests an expression against a pattern.</span></span>

## <a name="testing-for-type-compatibility"></a><span data-ttu-id="e8475-105">Testando a compatibilidade de tipo</span><span class="sxs-lookup"><span data-stu-id="e8475-105">Testing for type compatibility</span></span> ##

<span data-ttu-id="e8475-106">A palavra-chave `is` avalia a compatibilidade de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e8475-106">The `is` keyword evaluates type compatibility at runtime.</span></span> <span data-ttu-id="e8475-107">Ela determina se uma instância de objeto ou o resultado de uma expressão pode ser convertido em um tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="e8475-107">It determines whether an object instance or the result of an expression can be converted to a specified type.</span></span> <span data-ttu-id="e8475-108">Ela tem a sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8475-108">It has the syntax</span></span>

```csharp
   expr is type
```

<span data-ttu-id="e8475-109">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, e *type* é o nome do tipo no qual o resultado de *expr* será convertido.</span><span class="sxs-lookup"><span data-stu-id="e8475-109">where *expr* is an expression that evaluates to an instance of some type, and *type* is the name of the type to which the result of *expr* is to be converted.</span></span> <span data-ttu-id="e8475-110">A instrução `is` será `true` se *expr* não for nulo e o objeto resultante da avaliação da expressão puder ser convertido em *type*; caso contrário, ela retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="e8475-110">The `is` statement is `true` if *expr* is non-null and the object that results from evaluating the expression can be converted to *type*; otherwise, it returns `false`.</span></span>

<span data-ttu-id="e8475-111">Por exemplo, o código a seguir determina se `obj` pode ser convertido em uma instância do tipo `Person`:</span><span class="sxs-lookup"><span data-stu-id="e8475-111">For example, the following code determines if `obj` can be cast to an instance of the `Person` type:</span></span>

<span data-ttu-id="e8475-112">[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="e8475-112">[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]</span></span>

<span data-ttu-id="e8475-113">A instrução `is` será verdadeira se:</span><span class="sxs-lookup"><span data-stu-id="e8475-113">The `is` statement is true if:</span></span>

- <span data-ttu-id="e8475-114">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-114">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="e8475-115">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-115">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="e8475-116">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-116">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="e8475-117">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-117">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="e8475-118">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="e8475-118">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="e8475-119">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="e8475-119">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="e8475-120">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-120">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="e8475-121">O exemplo a seguir mostra que a expressão `is` é avaliada como `true` para cada uma dessas conversões.</span><span class="sxs-lookup"><span data-stu-id="e8475-121">The following example shows that the `is` expression evaluates to `true` for each of these conversions.</span></span>

<span data-ttu-id="e8475-122">[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="e8475-122">[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]</span></span>

<span data-ttu-id="e8475-123">A palavra-chave `is` gera um aviso de tempo de compilação caso seja conhecido que a expressão sempre é `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="e8475-123">The `is` keyword generates a compile-time warning if the expression is known to always be either `true` or `false`.</span></span> <span data-ttu-id="e8475-124">Ela considera somente conversões de referência, conversões boxing e conversões unboxing, e não considera conversões definidas pelo usuário ou conversões definidas pelos operadores [implicit](implicit.md) e [explicit](explicit.md) de um tipo.</span><span class="sxs-lookup"><span data-stu-id="e8475-124">It only considers reference conversions, boxing conversions, and unboxing conversions; it does not consider user-defined conversions or conversions defined by a type's [implicit](implicit.md) and [explicit](explicit.md) operators.</span></span> <span data-ttu-id="e8475-125">O exemplo a seguir gera avisos porque o resultado da conversão é conhecido em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="e8475-125">The following example generates warnings because the result of the conversion is known at compile-time.</span></span> <span data-ttu-id="e8475-126">Observe que a expressão `is` para conversões de `int` para `long` e `double` retorna falso, pois essas conversões são tratadas pelo operador [implicit](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="e8475-126">Note that the `is` expression for conversions from `int` to `long` and `double` return false, since these conversions are handled by the [implicit](implicit.md) operator.</span></span>

<span data-ttu-id="e8475-127">[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="e8475-127">[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]</span></span>

<span data-ttu-id="e8475-128">`expr` pode ser qualquer expressão que retorna um valor, com exceção de métodos anônimos e expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="e8475-128">`expr` can be any expression that returns a value, with the exception of anonymous methods and lambda expressions.</span></span> <span data-ttu-id="e8475-129">O exemplo a seguir usa `is` para avaliar o valor retornado de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e8475-129">The following example uses  `is` to evaluate the return value of a method call.</span></span>   
<span data-ttu-id="e8475-130">[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]</span><span class="sxs-lookup"><span data-stu-id="e8475-130">[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]</span></span>

<span data-ttu-id="e8475-131">A partir do C# 7, você pode usar a correspondência de padrões com o [padrão de tipo](#type) para escrever códigos mais concisos que usam a instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="e8475-131">Starting with C# 7, you can use pattern matching with the [type pattern](#type) to write more concise code that uses the `is` statement.</span></span>

## <a name="pattern-matching-with-is"></a><span data-ttu-id="e8475-132">Correspondência de padrões com `is`</span><span class="sxs-lookup"><span data-stu-id="e8475-132">Pattern matching with `is`</span></span> ##

<span data-ttu-id="e8475-133">A partir do C# 7, as instruções `is` e [switch](../../../csharp/language-reference/keywords/switch.md) dão suporte à correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="e8475-133">Starting with C# 7, the `is` and [switch](../../../csharp/language-reference/keywords/switch.md) statements support pattern matching.</span></span> <span data-ttu-id="e8475-134">A palavra-chave `is` dá suporte aos seguintes padrões:</span><span class="sxs-lookup"><span data-stu-id="e8475-134">The `is` keyword supports the following patterns:</span></span>

- <span data-ttu-id="e8475-135">[Padrão de tipo](#type), que testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="e8475-135">[Type pattern](#type),  which tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span>

- <span data-ttu-id="e8475-136">[Padrão constante](#constant), que testa se uma expressão é avaliada como um valor constante especificado.</span><span class="sxs-lookup"><span data-stu-id="e8475-136">[Constant pattern](#constant), which tests whether an expression evaluates to a specified constant value.</span></span>

- <span data-ttu-id="e8475-137">[Padrão var](#var), uma correspondência que sempre é bem-sucedida e vincula o valor de uma expressão a uma nova variável local.</span><span class="sxs-lookup"><span data-stu-id="e8475-137">[var pattern](#var), a match that always succeeds and binds the value of an expression to a new local variable.</span></span> 

### <span data-ttu-id="e8475-138"><a name="type" /> Padrão de tipo </a></span><span class="sxs-lookup"><span data-stu-id="e8475-138"><a name="type" /> Type pattern </a></span></span>

<span data-ttu-id="e8475-139">Ao usar o padrão de tipo para realizar a correspondência de padrões, `is` testa se uma expressão pode ser convertida em um tipo especificado e, caso possa, a converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="e8475-139">When using the type pattern to perform pattern matching, `is` tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="e8475-140">Trata-se de uma extensão simples da instrução `is` que habilita a conversão e a avaliação de tipo concisas.</span><span class="sxs-lookup"><span data-stu-id="e8475-140">It is a straightforward extension of the `is` statement that enables concise type evaluation and conversion.</span></span> <span data-ttu-id="e8475-141">A forma geral do padrão de tipo `is` é:</span><span class="sxs-lookup"><span data-stu-id="e8475-141">The general form of the `is` type pattern is:</span></span>

```csharp
   expr is type varname 
```

<span data-ttu-id="e8475-142">em que *expr* é uma expressão que é avaliada como uma instância de algum tipo, *type* é o nome do tipo no qual o resultado de *expr* será convertido e *varname* é o objeto no qual o resultado de *expr* será convertido se o teste `is` for `true`.</span><span class="sxs-lookup"><span data-stu-id="e8475-142">where *expr* is an expression that evaluates to an instance of some type, *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the `is` test is `true`.</span></span> 

<span data-ttu-id="e8475-143">A expressão `is` será `true` se qualquer uma das condições seguintes for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="e8475-143">The `is` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="e8475-144">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-144">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="e8475-145">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-145">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="e8475-146">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-146">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="e8475-147">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-147">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="e8475-148">O *tipo de tempo de compilação* de uma variável é o tipo da variável, conforme definido em sua declaração.</span><span class="sxs-lookup"><span data-stu-id="e8475-148">The *compile-time type* of a variable is the variable's type as defined in its declaration.</span></span> <span data-ttu-id="e8475-149">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="e8475-149">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="e8475-150">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="e8475-150">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="e8475-151">Se *exp* for `true` e `is` for usado com uma instrução `if`, *varname* será atribuído e terá escopo local somente dentro da instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="e8475-151">If *exp* is `true` and `is` is used with an `if` statement, *varname* is assigned and has local scope within the `if` statement only.</span></span>

<span data-ttu-id="e8475-152">O exemplo a seguir usa o padrão de tipo `is` para fornecer a implementação do método <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> de um tipo.</span><span class="sxs-lookup"><span data-stu-id="e8475-152">The following example uses the `is` type pattern to provide the implementation of a type's <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> method.</span></span>

<span data-ttu-id="e8475-153">[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]</span><span class="sxs-lookup"><span data-stu-id="e8475-153">[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]</span></span>

<span data-ttu-id="e8475-154">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="e8475-154">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="e8475-155">O uso da correspondência de padrões de tipo produz código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null`.</span><span class="sxs-lookup"><span data-stu-id="e8475-155">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null`.</span></span>  

<span data-ttu-id="e8475-156">[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]</span><span class="sxs-lookup"><span data-stu-id="e8475-156">[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]</span></span>

<span data-ttu-id="e8475-157">O padrão de tipo `is` também produz código mais compacto ao determinar o tipo de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="e8475-157">The `is` type pattern also produces more compact code when determining the type of a value type.</span></span> <span data-ttu-id="e8475-158">O exemplo a seguir usa o padrão de tipo `is` para determinar se um objeto é uma instância de `Person` ou `Dog` antes de exibir o valor de uma propriedade adequada.</span><span class="sxs-lookup"><span data-stu-id="e8475-158">The following example uses the `is` type pattern to determine whether an object is a `Person` or a `Dog` instance before displaying the value of an appropriate property.</span></span> 

<span data-ttu-id="e8475-159">[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]</span><span class="sxs-lookup"><span data-stu-id="e8475-159">[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]</span></span>

<span data-ttu-id="e8475-160">O código equivalente sem correspondência de padrões requer uma atribuição separada que inclui uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="e8475-160">The equivalent code without pattern matching requires a separate assignment that includes an explicit cast.</span></span>

<span data-ttu-id="e8475-161">[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]</span><span class="sxs-lookup"><span data-stu-id="e8475-161">[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]</span></span>

### <a name="a-nameconstant--constant-pattern"></a><span data-ttu-id="e8475-162"><a name="constant" /> Padrão constante</span><span class="sxs-lookup"><span data-stu-id="e8475-162"><a name="constant" /> Constant pattern</span></span> ###

<span data-ttu-id="e8475-163">Ao executar a correspondência de padrões com o padrão constante, `is` testa se uma expressão é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="e8475-163">When performing pattern matching with the constant pattern, `is` tests whether an expression equals a specified constant.</span></span> <span data-ttu-id="e8475-164">No C# 6 e em versões anteriores, o padrão constante tem suporte da instrução [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="e8475-164">In C# 6 and earlier versions, the constant pattern is supported by the [switch](switch.md) statement.</span></span> <span data-ttu-id="e8475-165">A partir do C# 7, ele tem suporte também da instrução `is`.</span><span class="sxs-lookup"><span data-stu-id="e8475-165">Starting with C# 7, it is supported by the `is` statement as well.</span></span> <span data-ttu-id="e8475-166">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="e8475-166">Its syntax is:</span></span>

```csharp
   expr is constant
```

<span data-ttu-id="e8475-167">em que *expr* é a expressão a ser avaliada e *constant* é o valor a ser testado.</span><span class="sxs-lookup"><span data-stu-id="e8475-167">where *expr* is the expression to evaluate, and *constant* is the value to test for.</span></span> <span data-ttu-id="e8475-168">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="e8475-168">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="e8475-169">Um valor literal.</span><span class="sxs-lookup"><span data-stu-id="e8475-169">A literal value.</span></span>

- <span data-ttu-id="e8475-170">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="e8475-170">The name of a declared `const` variable.</span></span>

- <span data-ttu-id="e8475-171">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e8475-171">An enumeration constant.</span></span>

<span data-ttu-id="e8475-172">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e8475-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="e8475-173">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="e8475-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="e8475-174">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="e8475-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="e8475-175">O exemplo a seguir combina os padrões de tipo e constante para testar se um objeto é uma instância de `Dice` e, caso seja, para determinar se o valor de uma distribuição de dados é 6.</span><span class="sxs-lookup"><span data-stu-id="e8475-175">The following example combines the type and constant patterns to test whether an object is a `Dice` instance and, if it is, to determine whether the value of a dice roll is 6.</span></span>

<span data-ttu-id="e8475-176">[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]</span><span class="sxs-lookup"><span data-stu-id="e8475-176">[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]</span></span>
 
### <span data-ttu-id="e8475-177"><a name="var" /> Padrão var </a></span><span class="sxs-lookup"><span data-stu-id="e8475-177"><a name="var" /> var pattern </a></span></span>

<span data-ttu-id="e8475-178">Uma correspondência de padrões com o padrão var sempre terá êxito.</span><span class="sxs-lookup"><span data-stu-id="e8475-178">A pattern match with the var pattern always succeeds.</span></span> <span data-ttu-id="e8475-179">Sua sintaxe é</span><span class="sxs-lookup"><span data-stu-id="e8475-179">Its syntax is</span></span>

```csharp 
   expr is var varname
```

<span data-ttu-id="e8475-180">em que o valor de *expr* sempre é atribuído a uma variável local chamada *varname*.</span><span class="sxs-lookup"><span data-stu-id="e8475-180">where the value of *expr* is always assigned to a local variable named *varname*.</span></span> <span data-ttu-id="e8475-181">*varname* é uma variável estática do mesmo tipo que *expr*.</span><span class="sxs-lookup"><span data-stu-id="e8475-181">*varname* is a static variable of the same type as *expr*.</span></span> <span data-ttu-id="e8475-182">O exemplo a seguir usa o padrão var para atribuir uma expressão a uma variável chamada `obj`.</span><span class="sxs-lookup"><span data-stu-id="e8475-182">The following example uses the var pattern to assign an expression to a variable named `obj`.</span></span> <span data-ttu-id="e8475-183">Em seguida, ele exibe o valor e o tipo de `obj`.</span><span class="sxs-lookup"><span data-stu-id="e8475-183">It then displays the value and the type of `obj`.</span></span>

<span data-ttu-id="e8475-184">[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]</span><span class="sxs-lookup"><span data-stu-id="e8475-184">[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]</span></span>

<span data-ttu-id="e8475-185">Observe que, se *expr* for `null`, a expressão `is` ainda será verdadeira e atribuirá `null` a *varname*.</span><span class="sxs-lookup"><span data-stu-id="e8475-185">Note that if *expr* is `null`, the `is` expression still is true and assigns `null` to *varname*.</span></span> 

# <a name="c-language-specification"></a><span data-ttu-id="e8475-186">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e8475-186">C# Language Specification</span></span>
  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8475-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8475-187">See also</span></span>  
 <span data-ttu-id="e8475-188">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8475-188">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e8475-189">[Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8475-189">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e8475-190">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span><span class="sxs-lookup"><span data-stu-id="e8475-190">[typeof](../../../csharp/language-reference/keywords/typeof.md) </span></span>  
 <span data-ttu-id="e8475-191">[as](../../../csharp/language-reference/keywords/as.md) </span><span class="sxs-lookup"><span data-stu-id="e8475-191">[as](../../../csharp/language-reference/keywords/as.md) </span></span>  
 [<span data-ttu-id="e8475-192">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="e8475-192">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

