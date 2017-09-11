---
title: LINQ e cadeias de caracteres (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 49c51595ffff45df503308b9eba55fc67b4da2e8
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="linq-and-strings-c"></a><span data-ttu-id="cdfd0-102">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-102">LINQ and Strings (C#)</span></span>
<span data-ttu-id="cdfd0-103">A LINQ pode ser usada para consultar e transformar as cadeias de caracteres e coleções de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="cdfd0-104">Ele pode ser especialmente útil com os dados semiestruturados em arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="cdfd0-105">Consultas LINQ podem ser combinadas com expressões regulares e funções de cadeia de caracteres tradicionais.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="cdfd0-106">Por exemplo, você pode usar o método <xref:System.String.Split%2A> ou <xref:System.Text.RegularExpressions.Regex.Split%2A> para criar uma matriz de cadeias de caracteres que você pode consultar ou modificar usando o LINQ.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="cdfd0-107">Você pode usar o método <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> na cláusula `where` de uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="cdfd0-108">E você pode usar o LINQ para consultar ou modificar os resultados de <xref:System.Text.RegularExpressions.MatchCollection> retornados por uma expressão regular.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="cdfd0-109">Você também pode usar as técnicas descritas nessa seção para transformar dados de texto semiestruturados em XML.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="cdfd0-110">Para obter mais informações, consulte [Como gerar um XML de arquivos CSV](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).</span><span class="sxs-lookup"><span data-stu-id="cdfd0-110">For more information, see [How to: Generate XML from CSV Files](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd).</span></span>  
  
 <span data-ttu-id="cdfd0-111">Os exemplos nesta seção se enquadram em duas categorias:</span><span class="sxs-lookup"><span data-stu-id="cdfd0-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="cdfd0-112">Consultando um bloco de texto</span><span class="sxs-lookup"><span data-stu-id="cdfd0-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="cdfd0-113">Consultar, analisar e modificar os blocos de texto dividindo-os em uma matriz de cadeias de caracteres menores consultáveis usando o método <xref:System.String.Split%2A> ou o método <xref:System.Text.RegularExpressions.Regex.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="cdfd0-114">Você pode dividir o texto de origem em palavras, frases, parágrafos, páginas ou quaisquer outros critérios e, em seguida, executar divisões adicionais se elas forem necessárias em sua consulta.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="cdfd0-115">Como contar ocorrências de uma palavra em uma cadeia de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-115">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="cdfd0-116">Mostra como usar a LINQ para consultas simples em texto.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="cdfd0-117">Como consultar sentenças que contenham um conjunto especificado de palavras (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)  
 <span data-ttu-id="cdfd0-118">Mostra como dividir os arquivos de texto em limites arbitrários e como executar consultas em cada parte.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="cdfd0-119">Como consultar caracteres em uma cadeia de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="cdfd0-120">Demonstra que uma cadeia de caracteres é de um tipo passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="cdfd0-121">Como combinar consultas LINQ com expressões regulares (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-121">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="cdfd0-122">Mostra como usar expressões regulares em consultas LINQ para correspondência de padrões complexos em resultados de consulta filtrados.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="cdfd0-123">Consultando dados semiestruturados em formato de texto</span><span class="sxs-lookup"><span data-stu-id="cdfd0-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="cdfd0-124">Muitos tipos diferentes de arquivos de texto consistem em uma série de linhas, geralmente com formatação semelhante, como arquivos delimitados por tabulação ou vírgula ou linhas de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="cdfd0-125">Depois de ler um arquivo de texto na memória, você pode usar a LINQ para consultar e/ou modificar as linhas.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="cdfd0-126">As consultas LINQ também simplificam a tarefa de combinar dados de várias fontes.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="cdfd0-127">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="cdfd0-128">Mostra como localizar todas as cadeias de caracteres que estão presentes em uma lista, mas não na outra.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="cdfd0-129">Como classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="cdfd0-130">Mostra como classificar linhas de texto com base em qualquer palavra ou campo.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="cdfd0-131">Como reordenar os campos de um arquivo delimitado (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-reorder-the-fields-of-a-delimited-file-linq.md)  
 <span data-ttu-id="cdfd0-132">Mostra como reordenar campos em uma linha em um arquivo .csv.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="cdfd0-133">Como combinar e comparar coleções de cadeias de caracteres (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-133">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="cdfd0-134">Mostra como combinar listas de cadeias de caracteres de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="cdfd0-135">Como preencher coleções de objetos de várias fontes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="cdfd0-136">Mostra como criar coleções de objetos usando vários arquivos de texto como fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="cdfd0-137">Como unir conteúdo de arquivos diferentes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="cdfd0-138">Mostra como combinar cadeias de caracteres em duas listas em uma única cadeia de caracteres usando uma chave correspondente.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="cdfd0-139">Como dividir um arquivo em vários arquivos usando grupos (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="cdfd0-140">Mostra como criar novos arquivos usando um único arquivo como uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="cdfd0-141">Como computar valores de coluna em um arquivo de texto CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="cdfd0-141">How to: Compute Column Values in a CSV Text File (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="cdfd0-142">Mostra como executar cálculos matemáticos em dados de texto em arquivos .csv.</span><span class="sxs-lookup"><span data-stu-id="cdfd0-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfd0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdfd0-143">See Also</span></span>  
 <span data-ttu-id="cdfd0-144">[LINQ (Consulta Integrada à Linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="cdfd0-144">[Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md) </span></span>  
 [<span data-ttu-id="cdfd0-145">Como gerar um XML de arquivos CSV</span><span class="sxs-lookup"><span data-stu-id="cdfd0-145">How to: Generate XML from CSV Files</span></span>](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)

