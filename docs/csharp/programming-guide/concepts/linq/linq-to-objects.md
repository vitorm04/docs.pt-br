---
title: LINQ to Objects (C#)
description: Saiba mais sobre LINQ to Objects em C#, que usa consultas LINQ com qualquer coleção IEnumerable ou IEnumerable <T> sem um provedor LINQ intermediário ou API.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 575708f14487670a4371d470dcdcf650b03c3175
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202520"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="ecbaf-103">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-103">LINQ to Objects (C#)</span></span>

<span data-ttu-id="ecbaf-104">O termo "LINQ to Objects" refere-se ao uso de consultas LINQ com qualquer coleção <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> diretamente, sem o uso de uma API ou provedor LINQ intermediário como o [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) ou [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ecbaf-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="ecbaf-105">Você pode usar o LINQ para consultar qualquer coleção enumerável ​​como <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="ecbaf-106">A coleção pode ser definida pelo usuário ou pode ser retornada por uma API do .NET.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-106">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="ecbaf-107">Basicamente, o LINQ to Objects representa uma nova abordagem às coleções.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="ecbaf-108">Na forma antiga, você precisava escrever loops `foreach` complexos que especificavam como recuperar dados de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-108">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="ecbaf-109">Na abordagem da LINQ, você escreve o código declarativo que descreve o que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="ecbaf-110">Além disso, as consultas LINQ oferecem três principais vantagens sobre os loops `foreach` tradicionais:</span><span class="sxs-lookup"><span data-stu-id="ecbaf-110">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="ecbaf-111">Elas são mais concisas e legíveis, especialmente quando você filtra várias condições.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="ecbaf-112">Elas fornecem poderosos recursos de filtragem, ordenação e agrupamento com um mínimo de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="ecbaf-113">Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="ecbaf-114">Em geral, quanto mais complexa for a operação que você deseja executar nos dados, mais benefícios você perceberá usando LINQ em vez de técnicas de iteração tradicionais.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-114">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="ecbaf-115">O objetivo desta seção é demonstrar a abordagem LINQ com alguns exemplos selecionados.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="ecbaf-116">Não tem a intenção de ser exaustiva.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-116">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecbaf-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ecbaf-117">In This Section</span></span>  

 [<span data-ttu-id="ecbaf-118">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="ecbaf-119">Explica como a LINQ pode ser usada para consultar e transformar cadeias de caracteres e coleções de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="ecbaf-120">Também inclui links para artigos que demonstram esses princípios.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-120">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="ecbaf-121">LINQ e reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-121">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="ecbaf-122">Contém um link para um exemplo que demonstra como a LINQ usa a reflexão.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="ecbaf-123">LINQ e diretórios de arquivos (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-123">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="ecbaf-124">Explica como a LINQ pode ser usada para interagir com sistemas de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="ecbaf-125">Também inclui links para artigos que demonstram esses conceitos.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-125">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="ecbaf-126">Como consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-126">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="ecbaf-127">Demonstra como consultar um ArrayList no C#.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="ecbaf-128">Como adicionar métodos personalizados para consultas LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-128">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="ecbaf-129">Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando os métodos de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="ecbaf-130">LINQ (Consulta Integrada à Linguagem) (C#)</span><span class="sxs-lookup"><span data-stu-id="ecbaf-130">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="ecbaf-131">Fornece links para artigos que explicam o LINQ e fornecem exemplos de código que executa consultas.</span><span class="sxs-lookup"><span data-stu-id="ecbaf-131">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
