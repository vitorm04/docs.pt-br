---
title: Variáveis locais de tipo implícito – Guia de Programação em C#
description: A palavra-chave var no C# instrui o compilador a inferir o tipo da variável a partir da expressão no lado direito da instrução de inicialização.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 6badb8588dedda80227ab38bee027cf2890c8672
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864209"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="dec29-103">Variáveis locais de tipo implícito (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="dec29-103">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="dec29-104">Variáveis locais podem ser declaradas sem fornecer um tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="dec29-104">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="dec29-105">A palavra-chave `var` instrui o compilador a inferir o tipo da variável da expressão no lado direito da instrução de inicialização.</span><span class="sxs-lookup"><span data-stu-id="dec29-105">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="dec29-106">O tipo inferido pode ser um tipo interno, um tipo anônimo, um tipo definido pelo usuário ou um tipo definido na biblioteca de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="dec29-106">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET class library.</span></span> <span data-ttu-id="dec29-107">Para obter mais informações sobre como inicializar matrizes com `var`, consulte [Matrizes de tipo implícito](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-107">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="dec29-108">Os exemplos a seguir mostram várias maneiras em que as variáveis locais podem ser declaradas com `var`:</span><span class="sxs-lookup"><span data-stu-id="dec29-108">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="dec29-109">É importante entender que a palavra-chave `var` não significa "variante" e não indica que a variável é vagamente tipada ou de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="dec29-109">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="dec29-110">Isso apenas significa que o compilador determina e atribui o tipo mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="dec29-110">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="dec29-111">A palavra-chave `var` pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="dec29-111">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="dec29-112">Em variáveis locais (variáveis declaradas no escopo do método) conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="dec29-112">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="dec29-113">Em uma instrução de inicialização [for](../../language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-113">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="dec29-114">Em uma instrução de inicialização [foreach](../../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-114">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="dec29-115">Em uma instrução [using](../../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-115">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="dec29-116">Para obter mais informações, consulte [como usar variáveis locais e matrizes de tipo implícito em uma expressão de consulta](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-116">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="dec29-117">Tipos var e anônimos</span><span class="sxs-lookup"><span data-stu-id="dec29-117">var and anonymous types</span></span>

<span data-ttu-id="dec29-118">Em muitos casos, o uso de `var` é opcional e é apenas uma conveniência sintática.</span><span class="sxs-lookup"><span data-stu-id="dec29-118">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="dec29-119">No entanto, quando uma variável é inicializada com um tipo anônimo você deve declarar a variável como `var` se precisar acessar as propriedades do objeto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="dec29-119">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="dec29-120">Esse é um cenário comum em expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="dec29-120">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="dec29-121">Para obter mais informações, consulte [Tipos Anônimos](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="dec29-121">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="dec29-122">Da perspectiva do código-fonte, um tipo anônimo não tem nome.</span><span class="sxs-lookup"><span data-stu-id="dec29-122">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="dec29-123">Portanto, se uma variável de consulta tiver sido inicializada com `var`, a única maneira de acessar as propriedades na sequência retornada será usar `var` como o tipo da variável de iteração na instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="dec29-123">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="dec29-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dec29-124">Remarks</span></span>

<span data-ttu-id="dec29-125">As seguintes restrições se aplicam às declarações de variável de tipo implícito:</span><span class="sxs-lookup"><span data-stu-id="dec29-125">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="dec29-126">`var` pode ser usado apenas quando uma variável local é declarada e inicializada na mesma instrução, a variável não pode ser inicializada como nula, um grupo de métodos ou uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="dec29-126">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="dec29-127">`var` não pode ser usado em campos no escopo da classe.</span><span class="sxs-lookup"><span data-stu-id="dec29-127">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="dec29-128">Variáveis declaradas usando `var` não podem ser usadas na expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="dec29-128">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="dec29-129">Em outras palavras, essa expressão é válida: `int i = (i = 20);` mas essa expressão produz um erro de tempo de compilação:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="dec29-129">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="dec29-130">Diversas variáveis de tipo implícito não podem ser inicializadas na mesma instrução.</span><span class="sxs-lookup"><span data-stu-id="dec29-130">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="dec29-131">Se um tipo nomeado `var` estiver no escopo, a palavra-chave `var` será resolvida para esse nome de tipo e não será tratada como parte de uma declaração de variável local de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="dec29-131">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="dec29-132">Tipagem implícita com a palavra-chave `var` só pode ser aplicada às variáveis no escopo do método local.</span><span class="sxs-lookup"><span data-stu-id="dec29-132">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="dec29-133">Digitação implícita não está disponível para os campos de classe, uma vez que o compilador C# encontraria um paradoxo lógico ao processar o código: o compilador precisa saber o tipo do campo, mas não é possível determinar o tipo até que a expressão de atribuição seja analisada. A expressão não pode ser avaliada sem saber o tipo.</span><span class="sxs-lookup"><span data-stu-id="dec29-133">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="dec29-134">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="dec29-134">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="dec29-135">`bookTitles` é um campo de classe dado o tipo `var`.</span><span class="sxs-lookup"><span data-stu-id="dec29-135">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="dec29-136">Como o campo não tem nenhuma expressão para avaliar, é impossível para o compilador inferir que tipo `bookTitles` deveria ser.</span><span class="sxs-lookup"><span data-stu-id="dec29-136">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="dec29-137">Além disso, também é insuficiente adicionar uma expressão ao campo (como você faria para uma variável local):</span><span class="sxs-lookup"><span data-stu-id="dec29-137">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="dec29-138">Quando o compilador encontra campos durante a compilação de código, ele registra cada tipo de campo antes de processar quaisquer expressões associadas.</span><span class="sxs-lookup"><span data-stu-id="dec29-138">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="dec29-139">O compilador encontra o mesmo paradoxo ao tentar analisar `bookTitles`: ele precisa saber o tipo do campo, mas o compilador normalmente determinaria o tipo de `var` analisando a expressão, o que não possível sem saber o tipo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="dec29-139">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="dec29-140">Você pode descobrir que `var` também pode ser útil com expressões de consulta em que o tipo construído exato da variável de consulta é difícil de ser determinado.</span><span class="sxs-lookup"><span data-stu-id="dec29-140">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="dec29-141">Isso pode ocorrer com operações de agrupamento e classificação.</span><span class="sxs-lookup"><span data-stu-id="dec29-141">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="dec29-142">A palavra-chave `var` também pode ser útil quando o tipo específico da variável é enfadonho de digitar no teclado, é óbvio ou não acrescenta à legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="dec29-142">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="dec29-143">Um exemplo em que `var` é útil dessa maneira é com os tipos genéricos aninhados, como os usados com operações de grupo.</span><span class="sxs-lookup"><span data-stu-id="dec29-143">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="dec29-144">Na consulta a seguir, o tipo da variável de consulta é `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="dec29-144">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="dec29-145">Contanto que você e as outras pessoas que devem manter o código entendam isso, não há problema em usar a tipagem implícita por questões de conveniência e brevidade.</span><span class="sxs-lookup"><span data-stu-id="dec29-145">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="dec29-146">O uso de `var` ajuda a simplificar seu código, mas seu uso deve ser restrito a casos em que é necessário, ou quando torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="dec29-146">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="dec29-147">Para obter mais informações sobre quando usar `var` corretamente, consulte a seção [variáveis locais digitadas implicitamente](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) no artigo diretrizes de codificação em C#.</span><span class="sxs-lookup"><span data-stu-id="dec29-147">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="dec29-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="dec29-148">See also</span></span>

- [<span data-ttu-id="dec29-149">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="dec29-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="dec29-150">Matrizes de tipo implícito</span><span class="sxs-lookup"><span data-stu-id="dec29-150">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="dec29-151">Como usar matrizes e variáveis locais de tipo implícito em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="dec29-151">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="dec29-152">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="dec29-152">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="dec29-153">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="dec29-153">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="dec29-154">var</span><span class="sxs-lookup"><span data-stu-id="dec29-154">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="dec29-155">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="dec29-155">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="dec29-156">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="dec29-156">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="dec29-157">for</span><span class="sxs-lookup"><span data-stu-id="dec29-157">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="dec29-158">foreach, in</span><span class="sxs-lookup"><span data-stu-id="dec29-158">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="dec29-159">Instrução using</span><span class="sxs-lookup"><span data-stu-id="dec29-159">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
