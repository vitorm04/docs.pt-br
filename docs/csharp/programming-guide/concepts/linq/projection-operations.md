---
title: Operações de projeção (C#)
description: Saiba mais sobre as operações de projeção. Essas operações transformam um objeto em um novo formulário que geralmente consiste apenas em propriedades que serão usadas posteriormente.
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 289100ac9afcfc0d5b93b5f963adc0a123e0a5af
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299156"
---
# <a name="projection-operations-c"></a><span data-ttu-id="6c490-104">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="6c490-104">Projection Operations (C#)</span></span>
<span data-ttu-id="6c490-105">Projeção refere-se à operação de transformar um objeto em um novo formulário que geralmente consiste apenas nas propriedades que serão usadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="6c490-105">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="6c490-106">Usando a projeção, você pode construir um novo tipo que é criado de cada objeto.</span><span class="sxs-lookup"><span data-stu-id="6c490-106">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="6c490-107">É possível projetar uma propriedade e executar uma função matemática nela.</span><span class="sxs-lookup"><span data-stu-id="6c490-107">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="6c490-108">Também é possível projetar o objeto original sem alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="6c490-108">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="6c490-109">Os métodos de operador de consulta padrão que realizam a projeção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c490-109">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c490-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="6c490-110">Methods</span></span>  
  
|<span data-ttu-id="6c490-111">Nome do método</span><span class="sxs-lookup"><span data-stu-id="6c490-111">Method Name</span></span>|<span data-ttu-id="6c490-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c490-112">Description</span></span>|<span data-ttu-id="6c490-113">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="6c490-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="6c490-114">Mais informações</span><span class="sxs-lookup"><span data-stu-id="6c490-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6c490-115">Selecionar</span><span class="sxs-lookup"><span data-stu-id="6c490-115">Select</span></span>|<span data-ttu-id="6c490-116">Projeta valores com base em uma função de transformação.</span><span class="sxs-lookup"><span data-stu-id="6c490-116">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6c490-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="6c490-117">SelectMany</span></span>|<span data-ttu-id="6c490-118">Projeta sequências de valores baseados em uma função de transformação e os mescla em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="6c490-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="6c490-119">Use várias cláusulas `from`</span><span class="sxs-lookup"><span data-stu-id="6c490-119">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6c490-120">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="6c490-120">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="6c490-121">Selecionar</span><span class="sxs-lookup"><span data-stu-id="6c490-121">Select</span></span>  
 <span data-ttu-id="6c490-122">O exemplo a seguir usa a cláusula `select` para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6c490-122">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="6c490-123">SelectMany</span><span class="sxs-lookup"><span data-stu-id="6c490-123">SelectMany</span></span>  
 <span data-ttu-id="6c490-124">O exemplo a seguir usa várias cláusulas `from` para projetar cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6c490-124">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="6c490-125">Select versus SelectMany</span><span class="sxs-lookup"><span data-stu-id="6c490-125">Select versus SelectMany</span></span>  
 <span data-ttu-id="6c490-126">O trabalho de `Select()` e `SelectMany()` é produzir um valor (ou valores) de resultado dos valores de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-126">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="6c490-127">`Select()` produz um valor de resultado para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-127">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="6c490-128">O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-128">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="6c490-129">Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-129">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="6c490-130">A função de transformação passada como um argumento para `SelectMany()` deve retornar uma sequência enumerável de valores para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-130">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="6c490-131">Essas sequências enumeráveis, então, são concatenadas por `SelectMany()` para criar uma sequência grande.</span><span class="sxs-lookup"><span data-stu-id="6c490-131">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="6c490-132">As duas ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="6c490-132">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="6c490-133">Em cada caso, presuma que a função de seletor (transformação) seleciona a matriz de flores de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-133">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="6c490-134">A ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-134">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Gráfico que mostra a ação de Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="6c490-136">Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediária.</span><span class="sxs-lookup"><span data-stu-id="6c490-136">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Gráfico mostrando a ação de SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="6c490-138">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="6c490-138">Code Example</span></span>  
 <span data-ttu-id="6c490-139">O exemplo a seguir compara o comportamento de `Select()` e de `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="6c490-139">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="6c490-140">O código cria um "buquê" de flores usando os dois primeiros itens de cada lista de nomes de flor na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="6c490-140">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="6c490-141">Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> usa é uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="6c490-141">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="6c490-142">Isso requer o loop `foreach` extra para enumerar cada cadeia de caracteres em cada subsequência.</span><span class="sxs-lookup"><span data-stu-id="6c490-142">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c490-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="6c490-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6c490-144">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="6c490-144">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="6c490-145">cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="6c490-145">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="6c490-146">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c490-146">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="6c490-147">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c490-147">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
