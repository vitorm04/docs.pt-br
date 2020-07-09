---
title: Escolhendo entre tipos anônimos e de tupla
description: Saiba quando é apropriado escolher entre tipos anônimos e tipo de tupla.
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9140250ad1f48501bf1d2e53a1c179e6823f19cd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100958"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="6d54a-103">Escolhendo entre tipos anônimos e de tupla</span><span class="sxs-lookup"><span data-stu-id="6d54a-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="6d54a-104">Escolher o tipo apropriado envolve considerar sua usabilidade, desempenho e compensações em comparação com outros tipos.</span><span class="sxs-lookup"><span data-stu-id="6d54a-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="6d54a-105">Os tipos anônimos estão disponíveis desde o C# 3,0, enquanto os <xref:System.Tuple%602?displayProperty=nameWithType> tipos genéricos foram introduzidos com .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="6d54a-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="6d54a-106">Desde então, novas opções foram introduzidas com suporte de nível de idioma, como <xref:System.ValueTuple%602?displayProperty=nameWithType> -que como o nome sugere, forneça um tipo de valor com a flexibilidade de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="6d54a-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="6d54a-107">Neste artigo, você aprenderá quando for apropriado escolher um tipo no outro.</span><span class="sxs-lookup"><span data-stu-id="6d54a-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="6d54a-108">Usabilidade e funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6d54a-108">Usability and functionality</span></span>

<span data-ttu-id="6d54a-109">Os tipos anônimos foram introduzidos em C# 3,0 com expressões LINQ (consulta integrada à linguagem).</span><span class="sxs-lookup"><span data-stu-id="6d54a-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="6d54a-110">Com o LINQ, os desenvolvedores geralmente projetam resultados de consultas em tipos anônimos que contêm algumas propriedades Select dos objetos com os quais estão trabalhando.</span><span class="sxs-lookup"><span data-stu-id="6d54a-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="6d54a-111">Considere o exemplo a seguir, que instancia uma matriz de <xref:System.DateTime> objetos e itera através deles projetando em um tipo anônimo com duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="6d54a-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="6d54a-112">Os tipos anônimos são instanciados usando o [`new`](../../csharp/language-reference/operators/new-operator.md) operador, e os nomes e tipos de propriedade são inferidos da declaração.</span><span class="sxs-lookup"><span data-stu-id="6d54a-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="6d54a-113">Se dois ou mais inicializadores de objeto anônimo no mesmo assembly especificarem uma sequência de propriedades que estão na mesma ordem e que têm os mesmos nomes e tipos, o compilador tratará os objetos como instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6d54a-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="6d54a-114">Eles compartilham o mesmo tipo de informação gerado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="6d54a-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="6d54a-115">O trecho C# anterior projeta um tipo anônimo com duas propriedades, assim como a seguinte classe C# gerada pelo compilador:</span><span class="sxs-lookup"><span data-stu-id="6d54a-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="6d54a-116">Para obter mais informações, consulte [tipos anônimos](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="6d54a-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="6d54a-117">A mesma funcionalidade existe com tuplas ao projetar em consultas LINQ, você pode selecionar propriedades em tuplas.</span><span class="sxs-lookup"><span data-stu-id="6d54a-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="6d54a-118">Essas tuplas fluem pela consulta, assim como os tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="6d54a-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="6d54a-119">Agora, considere o exemplo a seguir usando o `System.Tuple<string, long>` .</span><span class="sxs-lookup"><span data-stu-id="6d54a-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="6d54a-120">Com o <xref:System.Tuple%602?displayProperty=nameWithType> , a instância expõe as propriedades de item numeradas, como `Item1` e `Item2` .</span><span class="sxs-lookup"><span data-stu-id="6d54a-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="6d54a-121">Esses nomes de propriedade podem dificultar a compreensão da intenção dos valores de propriedade, uma vez que o nome da propriedade fornece apenas o ordinal.</span><span class="sxs-lookup"><span data-stu-id="6d54a-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="6d54a-122">Além disso, os `System.Tuple` tipos são `class` tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="6d54a-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="6d54a-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>No entanto, é um `struct` tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="6d54a-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="6d54a-124">O trecho de código C# a seguir usa o `ValueTuple<string, long>` para projetar no.</span><span class="sxs-lookup"><span data-stu-id="6d54a-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="6d54a-125">Ao fazer isso, ele atribui usando uma sintaxe literal.</span><span class="sxs-lookup"><span data-stu-id="6d54a-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="6d54a-126">O C# fornece suporte a idiomas de tuplas com o <xref:System.ValueTuple> tipo e a semântica para:</span><span class="sxs-lookup"><span data-stu-id="6d54a-126">C# provides language support of tuples with the <xref:System.ValueTuple> type, and semantics for:</span></span>

- [<span data-ttu-id="6d54a-127">Atribuição de tupla</span><span class="sxs-lookup"><span data-stu-id="6d54a-127">Tuple assignment</span></span>](../../csharp/tuples.md#assignment-and-tuples)
- <span data-ttu-id="6d54a-128">[Desconstrução de tupla](../../csharp/deconstruct.md) (não limitada a tuplas)</span><span class="sxs-lookup"><span data-stu-id="6d54a-128">[Tuple deconstruction](../../csharp/deconstruct.md) (not limited to tuples)</span></span>
- [<span data-ttu-id="6d54a-129">Verificações de igualdade de tupla</span><span class="sxs-lookup"><span data-stu-id="6d54a-129">Tuple equality checks</span></span>](../../csharp/tuples.md#equality-and-tuples)
- [<span data-ttu-id="6d54a-130">Inicializadores de projeção de tupla</span><span class="sxs-lookup"><span data-stu-id="6d54a-130">Tuple projection initializers</span></span>](../../csharp/tuples.md#tuple-projection-initializers)

<span data-ttu-id="6d54a-131">No entanto, os exemplos anteriores são funcionalmente equivalentes; Há pequenas diferenças na usabilidade e nas implementações subjacentes.</span><span class="sxs-lookup"><span data-stu-id="6d54a-131">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="6d54a-132">Compensações</span><span class="sxs-lookup"><span data-stu-id="6d54a-132">Tradeoffs</span></span>

<span data-ttu-id="6d54a-133">Você talvez queira sempre usar os <xref:System.ValueTuple> <xref:System.Tuple> tipos anônimos e próprios, mas há compensações que você deve considerar.</span><span class="sxs-lookup"><span data-stu-id="6d54a-133">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="6d54a-134">Os <xref:System.ValueTuple> tipos são mutáveis, enquanto <xref:System.Tuple> são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6d54a-134">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="6d54a-135">Tipos anônimos podem ser usados em árvores de expressão, enquanto as tuplas não podem.</span><span class="sxs-lookup"><span data-stu-id="6d54a-135">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="6d54a-136">A tabela a seguir é uma visão geral de algumas das principais diferenças.</span><span class="sxs-lookup"><span data-stu-id="6d54a-136">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="6d54a-137">Principais diferenças</span><span class="sxs-lookup"><span data-stu-id="6d54a-137">Key differences</span></span>

| <span data-ttu-id="6d54a-138">Nome</span><span class="sxs-lookup"><span data-stu-id="6d54a-138">Name</span></span>                     | <span data-ttu-id="6d54a-139">Modificador de acesso</span><span class="sxs-lookup"><span data-stu-id="6d54a-139">Access modifier</span></span> | <span data-ttu-id="6d54a-140">Type</span><span class="sxs-lookup"><span data-stu-id="6d54a-140">Type</span></span>     | <span data-ttu-id="6d54a-141">Nome do membro personalizado</span><span class="sxs-lookup"><span data-stu-id="6d54a-141">Custom member name</span></span> | <span data-ttu-id="6d54a-142">Suporte à desconstrução</span><span class="sxs-lookup"><span data-stu-id="6d54a-142">Deconstruction support</span></span> | <span data-ttu-id="6d54a-143">Suporte à árvore de expressões</span><span class="sxs-lookup"><span data-stu-id="6d54a-143">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="6d54a-144">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="6d54a-144">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="6d54a-145">✔️</span><span class="sxs-lookup"><span data-stu-id="6d54a-145">✔️</span></span>                   | ❌                     | <span data-ttu-id="6d54a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="6d54a-146">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="6d54a-147">✔️</span><span class="sxs-lookup"><span data-stu-id="6d54a-147">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="6d54a-148">✔️</span><span class="sxs-lookup"><span data-stu-id="6d54a-148">✔️</span></span>                   | <span data-ttu-id="6d54a-149">✔️</span><span class="sxs-lookup"><span data-stu-id="6d54a-149">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="6d54a-150">Serialização</span><span class="sxs-lookup"><span data-stu-id="6d54a-150">Serialization</span></span>

<span data-ttu-id="6d54a-151">Uma consideração importante ao escolher um tipo, é se ele precisará ser serializado ou não.</span><span class="sxs-lookup"><span data-stu-id="6d54a-151">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="6d54a-152">A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado.</span><span class="sxs-lookup"><span data-stu-id="6d54a-152">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="6d54a-153">Para obter mais informações, consulte [serialização](../../csharp/programming-guide/concepts/serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d54a-153">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="6d54a-154">Quando a serialização é importante, a criação de uma `class` ou `struct` é preferida sobre tipos anônimos ou tipos de tupla.</span><span class="sxs-lookup"><span data-stu-id="6d54a-154">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="6d54a-155">Desempenho</span><span class="sxs-lookup"><span data-stu-id="6d54a-155">Performance</span></span>

<span data-ttu-id="6d54a-156">O desempenho entre esses tipos depende do cenário.</span><span class="sxs-lookup"><span data-stu-id="6d54a-156">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="6d54a-157">O grande impacto envolve a compensação entre as alocações e a cópia.</span><span class="sxs-lookup"><span data-stu-id="6d54a-157">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="6d54a-158">Na maioria dos cenários, o impacto é pequeno.</span><span class="sxs-lookup"><span data-stu-id="6d54a-158">In most scenarios, the impact is small.</span></span> <span data-ttu-id="6d54a-159">Quando os principais impactos podem surgir, as medidas devem ser tomadas para informar a decisão.</span><span class="sxs-lookup"><span data-stu-id="6d54a-159">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="6d54a-160">Conclusão</span><span class="sxs-lookup"><span data-stu-id="6d54a-160">Conclusion</span></span>

<span data-ttu-id="6d54a-161">Como um desenvolvedor escolhendo entre tuplas e tipos anônimos, há vários fatores a serem considerados.</span><span class="sxs-lookup"><span data-stu-id="6d54a-161">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="6d54a-162">Em termos gerais, se você não estiver trabalhando com [árvores de expressão](../../csharp/expression-trees.md)e estiver familiarizado com a sintaxe de tupla, escolha <xref:System.ValueTuple> como elas fornecem um tipo de valor com a flexibilidade para nomear Propriedades.</span><span class="sxs-lookup"><span data-stu-id="6d54a-162">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="6d54a-163">Se você estiver trabalhando com árvores de expressão e preferir nomear Propriedades, escolha tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="6d54a-163">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="6d54a-164">Caso contrário, use <xref:System.Tuple>.</span><span class="sxs-lookup"><span data-stu-id="6d54a-164">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d54a-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d54a-165">See also</span></span>

- [<span data-ttu-id="6d54a-166">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="6d54a-166">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="6d54a-167">Árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="6d54a-167">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="6d54a-168">Tipos de tupla</span><span class="sxs-lookup"><span data-stu-id="6d54a-168">Tuple types</span></span>](../../csharp/tuples.md)
- [<span data-ttu-id="6d54a-169">Diretrizes de design de tipo</span><span class="sxs-lookup"><span data-stu-id="6d54a-169">Type design guidelines</span></span>](../design-guidelines/type.md)
