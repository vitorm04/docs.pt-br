---
title: Cláusula group – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 59bffc3df7155780fab90f9959ed99a21bda8eba
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635919"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="4a154-102">Cláusula group (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4a154-102">group clause (C# Reference)</span></span>

<span data-ttu-id="4a154-103">A cláusula `group` retorna uma sequência de objetos <xref:System.Linq.IGrouping%602> que contêm zero ou mais itens que correspondem ao valor de chave do grupo.</span><span class="sxs-lookup"><span data-stu-id="4a154-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="4a154-104">Por exemplo, é possível agrupar uma sequência de cadeias de caracteres de acordo com a primeira letra de cada cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4a154-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="4a154-105">Nesse caso, a primeira letra é a chave, tem um tipo [char](../builtin-types/char.md) e é armazenada na propriedade `Key` de cada objeto <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="4a154-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="4a154-106">O compilador infere o tipo da chave.</span><span class="sxs-lookup"><span data-stu-id="4a154-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="4a154-107">É possível finalizar uma expressão de consulta com uma cláusula `group`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a154-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="4a154-108">Caso deseje executar mais operações de consulta em cada grupo, é possível especificar um identificador temporário usando a palavra-chave contextual [into](into.md).</span><span class="sxs-lookup"><span data-stu-id="4a154-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="4a154-109">Ao usar `into`, é necessário continuar a consulta e, em algum momento, finalizá-la com uma instrução `select` ou outra cláusula `group`, conforme mostrado no trecho a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a154-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="4a154-110">Exemplos mais completos do uso de `group` com e sem `into` serão apresentados na seção Exemplo deste artigo.</span><span class="sxs-lookup"><span data-stu-id="4a154-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="4a154-111">Enumerando os resultados de uma consulta de grupo</span><span class="sxs-lookup"><span data-stu-id="4a154-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="4a154-112">Como os objetos <xref:System.Linq.IGrouping%602> produzidos por uma consulta `group` são essencialmente uma lista de listas, você deve usar um loop aninhado [foreach](foreach-in.md) para acessar os itens em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="4a154-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="4a154-113">O loop externo itera nas chaves de grupo e o loop interno itera em cada item do grupo em si.</span><span class="sxs-lookup"><span data-stu-id="4a154-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="4a154-114">Um grupo pode ter uma chave sem nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="4a154-114">A group may have a key but no elements.</span></span> <span data-ttu-id="4a154-115">Este é o loop `foreach` que executa a consulta nos exemplos de código anteriores:</span><span class="sxs-lookup"><span data-stu-id="4a154-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="4a154-116">Tipos de chave</span><span class="sxs-lookup"><span data-stu-id="4a154-116">Key types</span></span>

<span data-ttu-id="4a154-117">As chaves de grupo podem ser de qualquer tipo, como uma cadeia de caracteres, um tipo numérico interno, um tipo nomeado definido pelo usuário ou um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="4a154-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="4a154-118">Agrupar por cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4a154-118">Grouping by string</span></span>

<span data-ttu-id="4a154-119">Os exemplos de código anteriores usaram um `char`.</span><span class="sxs-lookup"><span data-stu-id="4a154-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="4a154-120">Em vez disso, uma chave de cadeia de caracteres pode facilmente ter sido especificada, por exemplo, o sobrenome completo:</span><span class="sxs-lookup"><span data-stu-id="4a154-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="4a154-121">Agrupar por bool</span><span class="sxs-lookup"><span data-stu-id="4a154-121">Grouping by bool</span></span>

<span data-ttu-id="4a154-122">O exemplo a seguir mostra o uso de um valor booliano para uma chave dividir os resultados em dois grupos.</span><span class="sxs-lookup"><span data-stu-id="4a154-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="4a154-123">Observe que o valor é produzido por uma subexpressão na cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="4a154-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="4a154-124">Agrupar por alcance numérico</span><span class="sxs-lookup"><span data-stu-id="4a154-124">Grouping by numeric range</span></span>

<span data-ttu-id="4a154-125">O próximo exemplo usa uma expressão para criar chaves de grupo numéricas que representam um intervalo de percentil.</span><span class="sxs-lookup"><span data-stu-id="4a154-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="4a154-126">Observe o uso de [let](let-clause.md) como um local conveniente para armazenar um resultado de chamada de método, para que não seja necessário chamar o método duas vezes na cláusula `group`.</span><span class="sxs-lookup"><span data-stu-id="4a154-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="4a154-127">Para obter mais informações sobre como usar métodos em expressões de consulta com segurança, consulte [tratar exceções em expressões de consulta](../../linq/handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4a154-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="4a154-128">Agrupando por chaves compostas</span><span class="sxs-lookup"><span data-stu-id="4a154-128">Grouping by composite keys</span></span>

<span data-ttu-id="4a154-129">Use uma chave composta para agrupar elementos de acordo com mais de uma chave.</span><span class="sxs-lookup"><span data-stu-id="4a154-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="4a154-130">Uma chave composta é criada usando um tipo anônimo ou nomeado para armazenar o elemento-chave.</span><span class="sxs-lookup"><span data-stu-id="4a154-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="4a154-131">No exemplo a seguir, suponha que uma classe `Person` foi declarada com membros nomeados `surname` e `city`.</span><span class="sxs-lookup"><span data-stu-id="4a154-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="4a154-132">A cláusula `group` faz com que um grupo separado seja criado para cada conjunto de pessoas com o mesmo sobrenome e a mesma cidade.</span><span class="sxs-lookup"><span data-stu-id="4a154-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="4a154-133">Use um tipo nomeado se for necessário passar a variável de consulta para outro método.</span><span class="sxs-lookup"><span data-stu-id="4a154-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="4a154-134">Crie uma classe especial usando as propriedades autoimplementadas das chaves e, em seguida, substitua os métodos <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a154-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="4a154-135">Também é possível usar um struct; nesse caso, não é exatamente necessário substituir esses métodos.</span><span class="sxs-lookup"><span data-stu-id="4a154-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="4a154-136">Para obter mais informações, consulte [como implementar uma classe leve com propriedades implementadas automaticamente](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) e [como consultar arquivos duplicados em uma árvore de diretórios](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4a154-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="4a154-137">O último artigo apresenta um exemplo de código que demonstra como usar uma chave composta com um tipo nomeado.</span><span class="sxs-lookup"><span data-stu-id="4a154-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="4a154-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a154-138">Example</span></span>

<span data-ttu-id="4a154-139">O exemplo a seguir mostra a norma padrão para ordenar dados de origem em grupos quando nenhuma lógica de consulta adicional for aplicada aos grupos.</span><span class="sxs-lookup"><span data-stu-id="4a154-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="4a154-140">Isso é chamado de “agrupamento sem uma continuação”.</span><span class="sxs-lookup"><span data-stu-id="4a154-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="4a154-141">Os elementos em uma matriz de cadeias de caracteres são agrupados de acordo com a primeira letra.</span><span class="sxs-lookup"><span data-stu-id="4a154-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="4a154-142">O resultado da consulta é um tipo <xref:System.Linq.IGrouping%602> que contém uma propriedade `Key` pública do tipo `char` e uma coleção <xref:System.Collections.Generic.IEnumerable%601> que contém cada item no agrupamento.</span><span class="sxs-lookup"><span data-stu-id="4a154-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="4a154-143">O resultado de uma cláusula `group` é uma sequência de sequências.</span><span class="sxs-lookup"><span data-stu-id="4a154-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="4a154-144">Portanto, para acessar os elementos individuais dentro de cada grupo retornado, use um loop aninhado `foreach` dentro do loop que itera as chaves de grupo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a154-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="4a154-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a154-145">Example</span></span>

<span data-ttu-id="4a154-146">Este exemplo mostra como executar a lógica adicional nos grupos depois criá-los, usando uma *continuação* com `into`.</span><span class="sxs-lookup"><span data-stu-id="4a154-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="4a154-147">Para obter mais informações, consulte [into](into.md).</span><span class="sxs-lookup"><span data-stu-id="4a154-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="4a154-148">O exemplo a seguir consulta cada grupo para selecionar apenas aqueles cujo valor da chave é uma vogal.</span><span class="sxs-lookup"><span data-stu-id="4a154-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="4a154-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a154-149">Remarks</span></span>

<span data-ttu-id="4a154-150">No tempo de compilação, as cláusulas `group` são convertidas em chamadas para o método <xref:System.Linq.Enumerable.GroupBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a154-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a154-151">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a154-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="4a154-152">Palavras-chave de consulta</span><span class="sxs-lookup"><span data-stu-id="4a154-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="4a154-153">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="4a154-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="4a154-154">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="4a154-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="4a154-155">Agrupar resultados de consultas</span><span class="sxs-lookup"><span data-stu-id="4a154-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="4a154-156">Executar uma subconsulta em uma operação de agrupamento</span><span class="sxs-lookup"><span data-stu-id="4a154-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
