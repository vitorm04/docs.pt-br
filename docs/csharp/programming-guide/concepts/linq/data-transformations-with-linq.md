---
title: Transformações de dados com LINQ (C#)
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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635944"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="7a430-102">Transformações de dados com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7a430-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="7a430-103">A consulta integrada à linguagem (LINQ) não se refere apenas à recuperação de dados.</span><span class="sxs-lookup"><span data-stu-id="7a430-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="7a430-104">Também é uma ferramenta poderosa para transformação de dados.</span><span class="sxs-lookup"><span data-stu-id="7a430-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="7a430-105">Usando uma consulta LINQ, você pode usar uma sequência de origem como entrada e modificá-la de várias maneiras para criar uma nova sequência de saída.</span><span class="sxs-lookup"><span data-stu-id="7a430-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="7a430-106">Você pode modificar a própria sequência sem modificar os respectivos elementos, classificando-os e agrupando-os.</span><span class="sxs-lookup"><span data-stu-id="7a430-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="7a430-107">Mas talvez o recurso mais poderoso das consultas LINQ seja a capacidade de criar novos tipos.</span><span class="sxs-lookup"><span data-stu-id="7a430-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="7a430-108">Isso é feito na cláusula [select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7a430-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="7a430-109">Por exemplo, é possível executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="7a430-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="7a430-110">Mesclar várias sequências de entrada em uma única sequência de saída que tenha um novo tipo.</span><span class="sxs-lookup"><span data-stu-id="7a430-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="7a430-111">Criar sequências de saída cujos elementos consistem em apenas uma ou várias propriedades de cada elemento da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="7a430-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="7a430-112">Criar sequências de saída cujos elementos consistem nos resultados das operações realizadas nos dados de origem.</span><span class="sxs-lookup"><span data-stu-id="7a430-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="7a430-113">Criar sequências de saída em um formato diferente.</span><span class="sxs-lookup"><span data-stu-id="7a430-113">Create output sequences in a different format.</span></span> <span data-ttu-id="7a430-114">Por exemplo, você pode transformar dados de linhas do SQL ou de arquivos de texto em XML.</span><span class="sxs-lookup"><span data-stu-id="7a430-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="7a430-115">Esses são apenas alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="7a430-115">These are just several examples.</span></span> <span data-ttu-id="7a430-116">É claro que essas transformações podem ser combinadas de diversas maneiras na mesma consulta.</span><span class="sxs-lookup"><span data-stu-id="7a430-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="7a430-117">Além disso, a sequência de saída de uma consulta pode ser usada como a sequência de entrada de uma nova consulta.</span><span class="sxs-lookup"><span data-stu-id="7a430-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="7a430-118">Ingressando Várias Entradas em uma Única Sequência de Saída</span><span class="sxs-lookup"><span data-stu-id="7a430-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="7a430-119">Você pode usar uma consulta LINQ para criar uma sequência de saída que contenha elementos de mais de uma sequência de entrada.</span><span class="sxs-lookup"><span data-stu-id="7a430-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="7a430-120">O exemplo a seguir mostra como combinar duas estruturas de dados na memória, mas os mesmos princípios podem ser aplicados para combinar dados de origens de XML, SQL ou DataSet.</span><span class="sxs-lookup"><span data-stu-id="7a430-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="7a430-121">Considere os dois tipos de classe a seguir:</span><span class="sxs-lookup"><span data-stu-id="7a430-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="7a430-122">O exemplo a seguir mostra a consulta:</span><span class="sxs-lookup"><span data-stu-id="7a430-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="7a430-123">Para obter mais informações, consulte [cláusula join](../../../language-reference/keywords/join-clause.md) e [cláusula select](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7a430-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="7a430-124">Selecionando um Subconjunto de Cada Elemento de Origem</span><span class="sxs-lookup"><span data-stu-id="7a430-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="7a430-125">Há duas maneiras principais de selecionar um subconjunto de cada elemento na sequência de origem:</span><span class="sxs-lookup"><span data-stu-id="7a430-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="7a430-126">Para selecionar apenas um membro do elemento de origem, use a operação de ponto.</span><span class="sxs-lookup"><span data-stu-id="7a430-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="7a430-127">No exemplo a seguir, suponha que um objeto `Customer` contém várias propriedades públicas, incluindo uma cadeia de caracteres denominada `City`.</span><span class="sxs-lookup"><span data-stu-id="7a430-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="7a430-128">Quando executada, essa consulta produzirá uma sequência de saída de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7a430-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="7a430-129">Para criar elementos que contenham mais de uma propriedade do elemento de origem, você pode usar um inicializador de objeto com um objeto nomeado ou um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="7a430-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="7a430-130">O exemplo a seguir mostra o uso de um tipo anônimo para encapsular duas propriedades de cada elemento `Customer`:</span><span class="sxs-lookup"><span data-stu-id="7a430-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="7a430-131">Para obter mais informações, consulte [Inicializadores de coleção e de objeto](../../classes-and-structs/object-and-collection-initializers.md) e [Tipos anônimos](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a430-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="7a430-132">Transformando Objetos na Memória em XML</span><span class="sxs-lookup"><span data-stu-id="7a430-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="7a430-133">As consultas do LINQ facilitam a transformação de dados entre estruturas de dados na memória, bancos de dados SQL, ADO.NET e fluxos XML ou documentos.</span><span class="sxs-lookup"><span data-stu-id="7a430-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="7a430-134">O exemplo a seguir transforma objetos de uma estrutura de dados na memória em elementos XML.</span><span class="sxs-lookup"><span data-stu-id="7a430-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="7a430-135">O código produz a seguinte saída XML:</span><span class="sxs-lookup"><span data-stu-id="7a430-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="7a430-136">Para obter mais informações, consulte [Criando árvores XML em C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="7a430-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="7a430-137">Realizando Operações em Elementos de Origem</span><span class="sxs-lookup"><span data-stu-id="7a430-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="7a430-138">Uma sequência de saída pode não conter os elementos ou propriedades de elementos da sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="7a430-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="7a430-139">Em vez disso, a saída pode ser uma sequência de valores que é calculada usando os elementos de origem como argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="7a430-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="7a430-140">Esta simples consulta a seguir, quando executada, produz uma sequência de cadeias de caracteres cujos valores representam um cálculo com base na sequência de origem de elementos do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="7a430-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a430-141">Não há suporte para chamar métodos em expressões de consulta se a consulta será movida para outro domínio.</span><span class="sxs-lookup"><span data-stu-id="7a430-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="7a430-142">Por exemplo, você não pode chamar um método comum de C# no [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] porque o SQL Server não tem contexto para ele.</span><span class="sxs-lookup"><span data-stu-id="7a430-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="7a430-143">No entanto, você pode mapear procedimentos armazenados para os métodos e chamá-los.</span><span class="sxs-lookup"><span data-stu-id="7a430-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="7a430-144">Para obter mais informações, consulte [Procedimentos armazenados](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7a430-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="7a430-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="7a430-145">See also</span></span>

- [<span data-ttu-id="7a430-146">LINQ (consulta integrada à linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="7a430-146">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="7a430-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7a430-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="7a430-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7a430-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="7a430-149">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7a430-149">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="7a430-150">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="7a430-150">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="7a430-151">Cláusula select</span><span class="sxs-lookup"><span data-stu-id="7a430-151">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
