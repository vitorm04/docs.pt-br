---
title: LINQ to Objects (Visual Basic) | Documentos do Microsoft
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
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 82094ee6232ef5b1884f1b4b15eacb635be758aa
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="5d345-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="5d345-103">O termo "LINQ to Objects" refere-se ao uso do LINQ consulta com qualquer <xref:System.Collections.IEnumerable>ou <xref:System.Collections.Generic.IEnumerable%601>coleção diretamente, sem o uso de um provedor LINQ intermediário ou a API como [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) ou [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="5d345-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="5d345-104">Você pode usar o LINQ para consultar qualquer coleção enumerável como <xref:System.Collections.Generic.List%601>, <xref:System.Array>, ou <xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="5d345-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="5d345-105">A coleção pode ser definido pelo usuário ou pode ser retornada por uma API do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d345-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="5d345-106">Basicamente, o LINQ to Objects representa uma nova abordagem para coleções.</span><span class="sxs-lookup"><span data-stu-id="5d345-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="5d345-107">Na forma antiga, você precisava escrever loops `For Each` complexos que especificavam como recuperar dados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5d345-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="5d345-108">A abordagem do LINQ, você escreve código declarativo que descreve o que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="5d345-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="5d345-109">Além disso, consultas LINQ oferecem três principais vantagens tradicionais `For Each` loops:</span><span class="sxs-lookup"><span data-stu-id="5d345-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1.  <span data-ttu-id="5d345-110">Elas são mais concisas e legíveis, especialmente quando você filtra várias condições.</span><span class="sxs-lookup"><span data-stu-id="5d345-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="5d345-111">Elas fornecem poderosos recursos de filtragem, ordenação e agrupamento com um mínimo de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5d345-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="5d345-112">Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="5d345-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="5d345-113">Em geral, quanto mais complexa a operação que você deseja executar nos dados, o maior benefício você perceberá usando LINQ em vez de técnicas tradicionais de iteração.</span><span class="sxs-lookup"><span data-stu-id="5d345-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="5d345-114">O objetivo desta seção é demonstrar a abordagem do LINQ com alguns exemplos selecionados.</span><span class="sxs-lookup"><span data-stu-id="5d345-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="5d345-115">Não pretendemos que ela seja detalhada.</span><span class="sxs-lookup"><span data-stu-id="5d345-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d345-116">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5d345-116">In This Section</span></span>  
 [<span data-ttu-id="5d345-117">LINQ e cadeias de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="5d345-118">Explica como o LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5d345-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="5d345-119">Também inclui links para tópicos que demonstram esses princípios.</span><span class="sxs-lookup"><span data-stu-id="5d345-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="5d345-120">LINQ e reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="5d345-121">Links para um exemplo que demonstra como LINQ usa reflexão.</span><span class="sxs-lookup"><span data-stu-id="5d345-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="5d345-122">LINQ e diretórios de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="5d345-123">Explica como o LINQ pode ser usado para interagir com sistemas de arquivos.</span><span class="sxs-lookup"><span data-stu-id="5d345-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="5d345-124">Também inclui links para tópicos que demonstram esses conceitos.</span><span class="sxs-lookup"><span data-stu-id="5d345-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="5d345-125">Como: consultar um ArrayList com LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="5d345-126">Demonstra como consultar um ArrayList no c#.</span><span class="sxs-lookup"><span data-stu-id="5d345-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="5d345-127">Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="5d345-128">Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5d345-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="5d345-129">Consulta integrada à linguagem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d345-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="5d345-130">Fornece links para tópicos que explicam o LINQ e fornecem exemplos de código que executam consultas.</span><span class="sxs-lookup"><span data-stu-id="5d345-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
