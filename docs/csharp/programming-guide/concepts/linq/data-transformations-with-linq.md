---
title: Transformações de dados com LINQ (C#)
description: Saiba como usar consultas LINQ em C# para transformar dados. Você pode modificar a sequência classificando e agrupando e criando novos tipos usando a cláusula SELECT.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 2fb4166b9dbcecebf06b9dc3a780b02751dd4dc7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159144"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="3eb27-104">Transformações de dados com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3eb27-104">Data Transformations with LINQ (C#)</span></span>

<span data-ttu-id="3eb27-105">A consulta integrada à linguagem (LINQ) não se refere apenas à recuperação de dados.</span><span class="sxs-lookup"><span data-stu-id="3eb27-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="3eb27-106">Também é uma ferramenta poderosa para transformação de dados.</span><span class="sxs-lookup"><span data-stu-id="3eb27-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="3eb27-107">Usando uma consulta LINQ, você pode usar uma sequência de origem como entrada e modificá-la de várias maneiras para criar uma nova sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="3eb27-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="3eb27-108">Você pode modificar a própria sequência sem modificar os respectivos elementos, classificando-os e agrupando-os.</span><span class="sxs-lookup"><span data-stu-id="3eb27-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="3eb27-109">Mas talvez o recurso mais poderoso das consultas LINQ seja a capacidade de criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="3eb27-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="3eb27-110">Isso é feito na cláusula [select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="3eb27-111">Por exemplo, é possível executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3eb27-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="3eb27-112">Mesclar várias sequências de entrada em uma única sequência de saída que tenha um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="3eb27-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="3eb27-113">Criar sequências de saída cujos elementos consistem em apenas uma ou várias propriedades de cada elemento da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="3eb27-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="3eb27-114">Criar sequências de saída cujos elementos consistem nos resultados das operações realizadas nos dados de origem.</span><span class="sxs-lookup"><span data-stu-id="3eb27-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="3eb27-115">Criar sequências de saída em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="3eb27-115">Create output sequences in a different format.</span></span> <span data-ttu-id="3eb27-116">Por exemplo, você pode transformar dados de linhas do SQL ou de arquivos de texto em XML.</span><span class="sxs-lookup"><span data-stu-id="3eb27-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="3eb27-117">Esses são apenas alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="3eb27-117">These are just several examples.</span></span> <span data-ttu-id="3eb27-118">É claro que essas transformações podem ser combinadas de diversas maneiras na mesma consulta.</span><span class="sxs-lookup"><span data-stu-id="3eb27-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="3eb27-119">Além disso, a sequência de saída de uma consulta pode ser usada como a sequência de entrada de uma nova consulta.</span><span class="sxs-lookup"><span data-stu-id="3eb27-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="3eb27-120">Ingressando Várias Entradas em uma Única Sequência de Saída</span><span class="sxs-lookup"><span data-stu-id="3eb27-120">Joining Multiple Inputs into One Output Sequence</span></span>  

 <span data-ttu-id="3eb27-121">Você pode usar uma consulta LINQ para criar uma sequência de saída que contenha elementos de mais de uma sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="3eb27-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="3eb27-122">O exemplo a seguir mostra como combinar duas estruturas de dados na memória, mas os mesmos princípios podem ser aplicados para combinar dados de origens de XML, SQL ou DataSet.</span><span class="sxs-lookup"><span data-stu-id="3eb27-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="3eb27-123">Considere os dois tipos de classe a seguir:</span><span class="sxs-lookup"><span data-stu-id="3eb27-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="3eb27-124">O exemplo a seguir mostra a consulta:</span><span class="sxs-lookup"><span data-stu-id="3eb27-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="3eb27-125">Para obter mais informações, consulte [cláusula join](../../../language-reference/keywords/join-clause.md) e [cláusula select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="3eb27-126">Selecionando um Subconjunto de Cada Elemento de Origem</span><span class="sxs-lookup"><span data-stu-id="3eb27-126">Selecting a Subset of each Source Element</span></span>  

 <span data-ttu-id="3eb27-127">Há duas maneiras principais de selecionar um subconjunto de cada elemento na sequência de origem:</span><span class="sxs-lookup"><span data-stu-id="3eb27-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="3eb27-128">Para selecionar apenas um membro do elemento de origem, use a operação de ponto.</span><span class="sxs-lookup"><span data-stu-id="3eb27-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="3eb27-129">No exemplo a seguir, suponha que um objeto `Customer` contém várias propriedades públicas, incluindo uma cadeia de caracteres denominada `City`.</span><span class="sxs-lookup"><span data-stu-id="3eb27-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="3eb27-130">Quando executada, essa consulta produzirá uma sequência de saída de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3eb27-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="3eb27-131">Para criar elementos que contenham mais de uma propriedade do elemento de origem, você pode usar um inicializador de objeto com um objeto nomeado ou um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="3eb27-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="3eb27-132">O exemplo a seguir mostra o uso de um tipo anônimo para encapsular duas propriedades de cada elemento `Customer`:</span><span class="sxs-lookup"><span data-stu-id="3eb27-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="3eb27-133">Para obter mais informações, consulte [Inicializadores de coleção e de objeto](../../classes-and-structs/object-and-collection-initializers.md) e [Tipos anônimos](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="3eb27-134">Transformando Objetos na Memória em XML</span><span class="sxs-lookup"><span data-stu-id="3eb27-134">Transforming in-Memory Objects into XML</span></span>  

 <span data-ttu-id="3eb27-135">As consultas do LINQ facilitam a transformação de dados entre estruturas de dados na memória, bancos de dados SQL, ADO.NET e fluxos XML ou documentos.</span><span class="sxs-lookup"><span data-stu-id="3eb27-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="3eb27-136">O exemplo a seguir transforma objetos de uma estrutura de dados na memória em elementos XML.</span><span class="sxs-lookup"><span data-stu-id="3eb27-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="3eb27-137">O código produz a seguinte saída XML:</span><span class="sxs-lookup"><span data-stu-id="3eb27-137">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="3eb27-138">Para obter mais informações, consulte [Criando árvores XML em C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="3eb27-139">Realizando Operações em Elementos de Origem</span><span class="sxs-lookup"><span data-stu-id="3eb27-139">Performing Operations on Source Elements</span></span>  

 <span data-ttu-id="3eb27-140">Uma sequência de saída pode não conter os elementos ou propriedades de elementos da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="3eb27-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="3eb27-141">Em vez disso, a saída pode ser uma sequência de valores que é calculada usando os elementos de origem como argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="3eb27-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="3eb27-142">A consulta a seguir usará uma sequência de números que representam raios de círculos, calculará a área para cada raio e retornará uma sequência de saída contendo cadeias de caracteres formatadas com a área calculada.</span><span class="sxs-lookup"><span data-stu-id="3eb27-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="3eb27-143">Cada cadeia de caracteres da sequência de saída será formatada usando [interpolação de cadeia de caracteres](../../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="3eb27-144">Uma cadeia de caracteres interpolada terá uma `$` na frente das aspas de abertura da cadeia de caracteres, e as operações poderão ser executadas dentro das chaves colocadas dentro da cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="3eb27-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="3eb27-145">Depois que essas operações forem executadas, os resultados serão concatenados.</span><span class="sxs-lookup"><span data-stu-id="3eb27-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3eb27-146">Não há suporte para chamar métodos em expressões de consulta se a consulta será movida para outro domínio.</span><span class="sxs-lookup"><span data-stu-id="3eb27-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="3eb27-147">Por exemplo, você não pode chamar um método comum de C# no [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] porque o SQL Server não tem contexto para ele.</span><span class="sxs-lookup"><span data-stu-id="3eb27-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="3eb27-148">No entanto, você pode mapear procedimentos armazenados para os métodos e chamá-los.</span><span class="sxs-lookup"><span data-stu-id="3eb27-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="3eb27-149">Para obter mais informações, consulte [Procedimentos armazenados](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3eb27-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="3eb27-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="3eb27-150">See also</span></span>

- [<span data-ttu-id="3eb27-151">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="3eb27-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="3eb27-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3eb27-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="3eb27-153">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3eb27-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="3eb27-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3eb27-154">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)
- [<span data-ttu-id="3eb27-155">Expressões de Consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="3eb27-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="3eb27-156">cláusula SELECT</span><span class="sxs-lookup"><span data-stu-id="3eb27-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
