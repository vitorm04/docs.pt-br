---
title: "Operações de projeção (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a05a4f228e64405ba24d967193d9e7a487ae473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="projection-operations-c"></a><span data-ttu-id="1d797-102">Operações de projeção (C#)</span><span class="sxs-lookup"><span data-stu-id="1d797-102">Projection Operations (C#)</span></span>
<span data-ttu-id="1d797-103">Projeção refere-se à operação de transformar um objeto em um novo formulário que geralmente consiste apenas nas propriedades que serão usadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d797-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="1d797-104">Usando a projeção, você pode construir um novo tipo que é criado de cada objeto.</span><span class="sxs-lookup"><span data-stu-id="1d797-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="1d797-105">É possível projetar uma propriedade e executar uma função matemática nela.</span><span class="sxs-lookup"><span data-stu-id="1d797-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="1d797-106">Também é possível projetar o objeto original sem alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="1d797-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="1d797-107">Os métodos de operador de consulta padrão que realizam a projeção estão listados na seção a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d797-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d797-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="1d797-108">Methods</span></span>  
  
|<span data-ttu-id="1d797-109">Nome do método</span><span class="sxs-lookup"><span data-stu-id="1d797-109">Method Name</span></span>|<span data-ttu-id="1d797-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d797-110">Description</span></span>|<span data-ttu-id="1d797-111">Sintaxe de expressão de consulta C#</span><span class="sxs-lookup"><span data-stu-id="1d797-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="1d797-112">Mais informações</span><span class="sxs-lookup"><span data-stu-id="1d797-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1d797-113">Selecionar</span><span class="sxs-lookup"><span data-stu-id="1d797-113">Select</span></span>|<span data-ttu-id="1d797-114">Projeta valores com base em uma função de transformação.</span><span class="sxs-lookup"><span data-stu-id="1d797-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1d797-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1d797-115">SelectMany</span></span>|<span data-ttu-id="1d797-116">Projeta sequências de valores baseados em uma função de transformação e os mescla em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="1d797-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="1d797-117">Use várias cláusulas `from`</span><span class="sxs-lookup"><span data-stu-id="1d797-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="1d797-118">Exemplos de sintaxe de expressão de consulta</span><span class="sxs-lookup"><span data-stu-id="1d797-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="1d797-119">Selecionar</span><span class="sxs-lookup"><span data-stu-id="1d797-119">Select</span></span>  
 <span data-ttu-id="1d797-120">O exemplo a seguir usa a cláusula `select` para projetar a primeira letra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d797-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="1d797-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1d797-121">SelectMany</span></span>  
 <span data-ttu-id="1d797-122">O exemplo a seguir usa várias cláusulas `from` para projetar cada palavra de cada cadeia de caracteres em uma lista de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1d797-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="1d797-123">Select versus SelectMany</span><span class="sxs-lookup"><span data-stu-id="1d797-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="1d797-124">O trabalho de `Select()` e `SelectMany()` é produzir um valor (ou valores) de resultado dos valores de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="1d797-125">`Select()` produz um valor de resultado para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="1d797-126">O resultado geral, portanto, é uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="1d797-127">Por outro lado, `SelectMany()` produz um único resultado geral que contém subcoleções concatenadas de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="1d797-128">A função de transformação passada como um argumento para `SelectMany()` deve retornar uma sequência enumerável de valores para cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="1d797-129">Essas sequências enumeráveis, então, são concatenadas por `SelectMany()` para criar uma sequência grande.</span><span class="sxs-lookup"><span data-stu-id="1d797-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="1d797-130">As duas ilustrações a seguir mostram a diferença conceitual entre as ações desses dois métodos.</span><span class="sxs-lookup"><span data-stu-id="1d797-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="1d797-131">Em cada caso, presuma que a função de seletor (transformação) seleciona a matriz de flores de cada valor de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="1d797-132">A ilustração mostra como `Select()` retorna uma coleção que tem o mesmo número de elementos que a coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="1d797-133">![Ilustração conceitual da ação de Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="1d797-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="1d797-134">Esta ilustração mostra como `SelectMany()` concatena a sequência intermediária de matrizes em um valor de resultado final que contém cada valor de cada matriz intermediária.</span><span class="sxs-lookup"><span data-stu-id="1d797-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="1d797-135">![Gráfico mostrando a ação de SelectMany&#40;&#41;.] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="1d797-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="1d797-136">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="1d797-136">Code Example</span></span>  
 <span data-ttu-id="1d797-137">O exemplo a seguir compara o comportamento de `Select()` e de `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="1d797-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="1d797-138">O código cria um "buquê" de flores usando os dois primeiros itens de cada lista de nomes de flor na coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="1d797-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="1d797-139">Neste exemplo, o "valor único" que a função de transformação <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> usa é uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="1d797-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="1d797-140">Isso requer o loop `foreach` extra para enumerar cada cadeia de caracteres em cada subsequência.</span><span class="sxs-lookup"><span data-stu-id="1d797-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d797-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d797-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="1d797-142">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="1d797-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="1d797-143">Cláusula select</span><span class="sxs-lookup"><span data-stu-id="1d797-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="1d797-144">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1d797-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="1d797-145">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1d797-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
