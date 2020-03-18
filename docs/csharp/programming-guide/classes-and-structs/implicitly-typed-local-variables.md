---
title: Variáveis locais de tipo implícito – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399822"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="d8beb-102">Variáveis locais de tipo implícito (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d8beb-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="d8beb-103">Variáveis locais podem ser declaradas sem fornecer um tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="d8beb-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="d8beb-104">A palavra-chave `var` instrui o compilador a inferir o tipo da variável da expressão no lado direito da instrução de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d8beb-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="d8beb-105">O tipo inferido pode ser um tipo interno, um tipo anônimo, um tipo definido pelo usuário ou um tipo definido na biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8beb-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="d8beb-106">Para obter mais informações sobre como inicializar matrizes com `var`, consulte [Matrizes de tipo implícito](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="d8beb-107">Os exemplos a seguir mostram várias maneiras em que as variáveis locais podem ser declaradas com `var`:</span><span class="sxs-lookup"><span data-stu-id="d8beb-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="d8beb-108">É importante entender que a palavra-chave `var` não significa "variante" e não indica que a variável é vagamente tipada ou de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="d8beb-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="d8beb-109">Isso apenas significa que o compilador determina e atribui o tipo mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="d8beb-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="d8beb-110">A palavra-chave `var` pode ser usada nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="d8beb-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="d8beb-111">Em variáveis locais (variáveis declaradas no escopo do método) conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d8beb-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="d8beb-112">Em uma instrução de inicialização [for](../../language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="d8beb-113">Em uma instrução de inicialização [foreach](../../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="d8beb-114">Em uma instrução [using](../../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="d8beb-115">Para obter mais informações, consulte [Como usar variáveis e matrizes locais digitadas implicitamente em uma expressão de consulta](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="d8beb-116">Tipos var e anônimos</span><span class="sxs-lookup"><span data-stu-id="d8beb-116">var and anonymous types</span></span>

<span data-ttu-id="d8beb-117">Em muitos casos, o uso de `var` é opcional e é apenas uma conveniência sintática.</span><span class="sxs-lookup"><span data-stu-id="d8beb-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="d8beb-118">No entanto, quando uma variável é inicializada com um tipo anônimo você deve declarar a variável como `var` se precisar acessar as propriedades do objeto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="d8beb-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="d8beb-119">Este é um cenário comum nas expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="d8beb-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="d8beb-120">Para obter mais informações, consulte [Tipos Anônimos](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d8beb-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="d8beb-121">Da perspectiva do código-fonte, um tipo anônimo não tem nome.</span><span class="sxs-lookup"><span data-stu-id="d8beb-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="d8beb-122">Portanto, se uma variável de consulta tiver sido inicializada com `var`, a única maneira de acessar as propriedades na sequência retornada será usar `var` como o tipo da variável de iteração na instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d8beb-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="d8beb-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8beb-123">Remarks</span></span>

<span data-ttu-id="d8beb-124">As seguintes restrições se aplicam às declarações de variável de tipo implícito:</span><span class="sxs-lookup"><span data-stu-id="d8beb-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="d8beb-125">`var` pode ser usado apenas quando uma variável local é declarada e inicializada na mesma instrução, a variável não pode ser inicializada como nula, um grupo de métodos ou uma função anônima.</span><span class="sxs-lookup"><span data-stu-id="d8beb-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="d8beb-126">`var` não pode ser usado em campos no escopo da classe.</span><span class="sxs-lookup"><span data-stu-id="d8beb-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="d8beb-127">Variáveis declaradas usando `var` não podem ser usadas na expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d8beb-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="d8beb-128">Em outras palavras, essa `int i = (i = 20);` expressão é legal: mas essa expressão produz um erro de tempo de compilação:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="d8beb-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="d8beb-129">Diversas variáveis de tipo implícito não podem ser inicializadas na mesma instrução.</span><span class="sxs-lookup"><span data-stu-id="d8beb-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="d8beb-130">Se um tipo nomeado `var` estiver no escopo, a palavra-chave `var` será resolvida para esse nome de tipo e não será tratada como parte de uma declaração de variável local de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="d8beb-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="d8beb-131">Tipagem implícita com a palavra-chave `var` só pode ser aplicada às variáveis no escopo do método local.</span><span class="sxs-lookup"><span data-stu-id="d8beb-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="d8beb-132">Digitação implícita não está disponível para os campos de classe, uma vez que o compilador C# encontraria um paradoxo lógico ao processar o código: o compilador precisa saber o tipo do campo, mas não é possível determinar o tipo até que a expressão de atribuição seja analisada. A expressão não pode ser avaliada sem saber o tipo.</span><span class="sxs-lookup"><span data-stu-id="d8beb-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="d8beb-133">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d8beb-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="d8beb-134">`bookTitles` é um campo de classe dado o tipo `var`.</span><span class="sxs-lookup"><span data-stu-id="d8beb-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="d8beb-135">Como o campo não tem nenhuma expressão para avaliar, é impossível para o compilador inferir que tipo `bookTitles` deveria ser.</span><span class="sxs-lookup"><span data-stu-id="d8beb-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="d8beb-136">Além disso, também é insuficiente adicionar uma expressão ao campo (como você faria para uma variável local):</span><span class="sxs-lookup"><span data-stu-id="d8beb-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="d8beb-137">Quando o compilador encontra campos durante a compilação de código, ele registra cada tipo de campo antes de processar quaisquer expressões associadas.</span><span class="sxs-lookup"><span data-stu-id="d8beb-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="d8beb-138">O compilador encontra o mesmo paradoxo ao tentar analisar `bookTitles`: ele precisa saber o tipo do campo, mas o compilador normalmente determinaria o tipo de `var` analisando a expressão, o que não possível sem saber o tipo com antecedência.</span><span class="sxs-lookup"><span data-stu-id="d8beb-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="d8beb-139">Você pode descobrir que `var` também pode ser útil com expressões de consulta em que o tipo construído exato da variável de consulta é difícil de ser determinado.</span><span class="sxs-lookup"><span data-stu-id="d8beb-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="d8beb-140">Isso pode ocorrer com operações de agrupamento e classificação.</span><span class="sxs-lookup"><span data-stu-id="d8beb-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="d8beb-141">A palavra-chave `var` também pode ser útil quando o tipo específico da variável é enfadonho de digitar no teclado, é óbvio ou não acrescenta à legibilidade do código.</span><span class="sxs-lookup"><span data-stu-id="d8beb-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="d8beb-142">Um exemplo em que `var` é útil dessa maneira é com os tipos genéricos aninhados, como os usados com operações de grupo.</span><span class="sxs-lookup"><span data-stu-id="d8beb-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="d8beb-143">Na consulta a seguir, o tipo da variável de consulta é `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="d8beb-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="d8beb-144">Contanto que você e as outras pessoas que devem manter o código entendam isso, não há problema em usar a tipagem implícita por questões de conveniência e brevidade.</span><span class="sxs-lookup"><span data-stu-id="d8beb-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="d8beb-145">O uso `var` de ajuda a simplificar seu código, mas seu uso deve ser restrito aos casos em que é necessário, ou quando torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="d8beb-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="d8beb-146">Para obter mais informações `var` sobre quando usar corretamente, consulte a seção [de variáveis locais digitadas implicitamente](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) no artigo C# Coding Guidelines.</span><span class="sxs-lookup"><span data-stu-id="d8beb-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8beb-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="d8beb-147">See also</span></span>

- [<span data-ttu-id="d8beb-148">C# Referência</span><span class="sxs-lookup"><span data-stu-id="d8beb-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="d8beb-149">Matrizes de tipo implícito</span><span class="sxs-lookup"><span data-stu-id="d8beb-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="d8beb-150">Como usar variáveis e matrizes locais digitadas implicitamente em uma expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="d8beb-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="d8beb-151">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="d8beb-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="d8beb-152">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="d8beb-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="d8beb-153">Var</span><span class="sxs-lookup"><span data-stu-id="d8beb-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="d8beb-154">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="d8beb-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="d8beb-155">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="d8beb-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="d8beb-156">Para</span><span class="sxs-lookup"><span data-stu-id="d8beb-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="d8beb-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="d8beb-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="d8beb-158">usando a Declaração</span><span class="sxs-lookup"><span data-stu-id="d8beb-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
