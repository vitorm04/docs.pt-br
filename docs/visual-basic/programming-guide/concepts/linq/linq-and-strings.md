---
title: LINQ e cadeias de caracteres (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 94e9627efb183c08bbb67a7e6e82df9132ebdef2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="cd6d5-102">LINQ e cadeias de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="cd6d5-103">LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="cd6d5-104">Ele pode ser especialmente útil com dados estruturados em arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="cd6d5-105">Consultas LINQ podem ser combinadas com expressões regulares e funções de cadeia de caracteres tradicional.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="cd6d5-106">Por exemplo, você pode usar o <xref:System.String.Split%2A>ou <xref:System.Text.RegularExpressions.Regex.Split%2A>método para criar uma matriz de cadeias de caracteres que você pode consultar ou modificar usando LINQ.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="cd6d5-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="cd6d5-107">Você pode usar o <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>método de `where` cláusula de uma consulta LINQ.</xref:System.Text.RegularExpressions.Regex.IsMatch%2A></span><span class="sxs-lookup"><span data-stu-id="cd6d5-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="cd6d5-108">E você pode usar o LINQ para consultar ou modificar o <xref:System.Text.RegularExpressions.MatchCollection>resultados retornados por uma expressão regular.</xref:System.Text.RegularExpressions.MatchCollection></span><span class="sxs-lookup"><span data-stu-id="cd6d5-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="cd6d5-109">Você também pode usar as técnicas descritas nesta seção para transformar dados semi-estruturados texto para XML.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="cd6d5-110">Para obter mais informações, consulte [como: gerar XML de arquivos CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="cd6d5-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="cd6d5-111">Os exemplos nesta seção se enquadram em duas categorias:</span><span class="sxs-lookup"><span data-stu-id="cd6d5-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="cd6d5-112">Consultando um bloco de texto</span><span class="sxs-lookup"><span data-stu-id="cd6d5-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="cd6d5-113">Você pode consultar, analisar e modificar blocos de texto dividindo-os em uma matriz de cadeias de caracteres menores de que podem ser consultada usando o <xref:System.String.Split%2A>método ou o <xref:System.Text.RegularExpressions.Regex.Split%2A>método.</xref:System.Text.RegularExpressions.Regex.Split%2A> </xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="cd6d5-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="cd6d5-114">Você pode dividir o texto de origem em palavras, frases, parágrafos, páginas ou quaisquer outros critérios e, em seguida, executar divisões adicionais se eles forem necessários em sua consulta.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="cd6d5-115">Como: contar as ocorrências de uma palavra em uma cadeia de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="cd6d5-116">Mostra como usar o LINQ para consultas simples em texto.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="cd6d5-117">Como: consultar sentenças que contêm um conjunto especificado de palavras (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="cd6d5-118">Mostra como dividir os arquivos de texto em limites arbitrários e como executar consultas em cada parte.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="cd6d5-119">Como: consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="cd6d5-120">Demonstra uma cadeia de caracteres é um tipo que pode ser consultado.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="cd6d5-121">Como: combinar consultas LINQ com expressões regulares (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="cd6d5-122">Mostra como usar expressões regulares em consultas LINQ de padrões complexos correspondentes nos resultados de consulta filtrada.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="cd6d5-123">Consultando dados semi-estruturados em formato de texto</span><span class="sxs-lookup"><span data-stu-id="cd6d5-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="cd6d5-124">Muitos tipos diferentes de arquivos de texto consistem em uma série de linhas, geralmente com formatação semelhante, como arquivos delimitados por tabulação ou vírgula ou linhas de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="cd6d5-125">Depois de ler um arquivo de texto na memória, você pode usar o LINQ para consultar e/ou modifique as linhas.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="cd6d5-126">Consultas LINQ também simplificam a tarefa de combinar dados de várias fontes.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="cd6d5-127">Como: localizar a diferença definida entre as duas listas (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="cd6d5-128">Mostra como localizar todas as strings que estão presentes em uma lista, mas não o outro.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="cd6d5-129">Como: classificar ou filtrar dados de texto por qualquer palavra ou campo (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="cd6d5-130">Mostra como classificar linhas de texto com base em qualquer palavra ou campo.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="cd6d5-131">Como: reordenar os campos de um arquivo delimitado (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="cd6d5-132">Mostra como reordenar campos em uma linha em um arquivo. csv.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="cd6d5-133">Como: combinar e comparar coleções de cadeia de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="cd6d5-134">Mostra como combinar listas de cadeia de caracteres de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="cd6d5-135">Como: preencher coleções de objetos de várias fontes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="cd6d5-136">Mostra como criar coleções de objetos usando vários arquivos de texto, como fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="cd6d5-137">Como: unir conteúdo a partir de arquivos diferentes (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="cd6d5-138">Mostra como combinar cadeias de caracteres em duas listas em uma única cadeia de caracteres usando uma chave correspondente.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="cd6d5-139">Como: dividir um arquivo em vários arquivos usando grupos (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="cd6d5-140">Mostra como criar novos arquivos usando um único arquivo como uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="cd6d5-141">Como: calcular valores de coluna em um arquivo CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="cd6d5-142">Mostra como executar cálculos matemáticos em dados de texto em arquivos. csv.</span><span class="sxs-lookup"><span data-stu-id="cd6d5-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6d5-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd6d5-143">See Also</span></span>  
 <span data-ttu-id="cd6d5-144">[Consulta integrada à linguagem (LINQ) (Visual Basic)](index.md) </span><span class="sxs-lookup"><span data-stu-id="cd6d5-144">[Language-Integrated Query (LINQ) (Visual Basic)](index.md) </span></span>  
<span data-ttu-id="cd6d5-145"> [Como gerar um XML de arquivos CSV](how-to-generate-xml-from-csv-files.md)</span><span class="sxs-lookup"><span data-stu-id="cd6d5-145"> [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md)</span></span>

