---
title: "LINQ e tipos genéricos (C#)"
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
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 177db64491d58b31ca50cef0bb2eda8c2cb65078
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="linq-and-generic-types-c"></a><span data-ttu-id="58d9d-102">LINQ e tipos genéricos (C#)</span><span class="sxs-lookup"><span data-stu-id="58d9d-102">LINQ and Generic Types (C#)</span></span>
<span data-ttu-id="58d9d-103">As consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] são baseadas em tipos genéricos, que foram introduzidos na versão 2.0 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58d9d-103">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries are based on generic types, which were introduced in version 2.0 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="58d9d-104">Não é necessário um conhecimento profundo sobre os genéricos antes de começar a escrever consultas.</span><span class="sxs-lookup"><span data-stu-id="58d9d-104">You do not need an in-depth knowledge of generics before you can start writing queries.</span></span> <span data-ttu-id="58d9d-105">No entanto, convém entender dois conceitos básicos:</span><span class="sxs-lookup"><span data-stu-id="58d9d-105">However, you may want to understand two basic concepts:</span></span>  
  
1.  <span data-ttu-id="58d9d-106">Quando você cria uma instância de uma classe de coleção genérica, como <xref:System.Collections.Generic.List%601>, substitua o "T" pelo tipo dos objetos que a lista bloqueia.</span><span class="sxs-lookup"><span data-stu-id="58d9d-106">When you create an instance of a generic collection class such as <xref:System.Collections.Generic.List%601>, you replace the "T" with the type of objects that the list will hold.</span></span> <span data-ttu-id="58d9d-107">Por exemplo, uma lista de cadeias de caracteres é expressa como `List<string>` e uma lista de objetos `Customer` é expressa como `List<Customer>`.</span><span class="sxs-lookup"><span data-stu-id="58d9d-107">For example, a list of strings is expressed as `List<string>`, and a list of `Customer` objects is expressed as `List<Customer>`.</span></span> <span data-ttu-id="58d9d-108">Uma lista genérica é fortemente tipada e oferece muitos benefícios em coleções que armazenam seus elementos como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="58d9d-108">A generic list is strongly typed and provides many benefits over collections that store their elements as <xref:System.Object>.</span></span> <span data-ttu-id="58d9d-109">Se tentar adicionar um `Customer` em uma `List<string>`, você obterá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="58d9d-109">If you try to add a `Customer` to a `List<string>`, you will get an error at compile time.</span></span> <span data-ttu-id="58d9d-110">É fácil usar coleções genéricas, porque você não precisa realizar a conversão de tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="58d9d-110">It is easy to use generic collections because you do not have to perform run-time type-casting.</span></span>  
  
2.  <span data-ttu-id="58d9d-111">A <xref:System.Collections.Generic.IEnumerable%601> é a interface que permite que as classes de coleção genérica sejam enumeradas usando a instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="58d9d-111"><xref:System.Collections.Generic.IEnumerable%601> is the interface that enables generic collection classes to be enumerated by using the `foreach` statement.</span></span> <span data-ttu-id="58d9d-112">Classes de coleção genéricas dão suporte a <xref:System.Collections.Generic.IEnumerable%601> do mesmo modo que classes de coleção não genéricas, tais como <xref:System.Collections.ArrayList>, dão suporte a <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="58d9d-112">Generic collection classes support <xref:System.Collections.Generic.IEnumerable%601> just as non-generic collection classes such as <xref:System.Collections.ArrayList> support <xref:System.Collections.IEnumerable>.</span></span>  
  
 <span data-ttu-id="58d9d-113">Para obter mais informações sobre os genéricos, consulte [Genéricos](../../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="58d9d-113">For more information about generics, see [Generics](../../../../csharp/programming-guide/generics/index.md).</span></span>  
  
## <a name="ienumerablet-variables-in-linq-queries"></a><span data-ttu-id="58d9d-114">Variáveis IEnumerable<T\> em consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="58d9d-114">IEnumerable<T\> variables in LINQ Queries</span></span>  
 <span data-ttu-id="58d9d-115">Variáveis de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] são digitadas como <xref:System.Collections.Generic.IEnumerable%601> ou um tipo derivado, por exemplo, <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="58d9d-115">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query variables are typed as <xref:System.Collections.Generic.IEnumerable%601> or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="58d9d-116">Ao se deparar com uma variável de consulta que é tipada como `IEnumerable<Customer>`, significa apenas que a consulta, quando for executada, produzirá uma sequência de zero ou mais objetos `Customer`.</span><span class="sxs-lookup"><span data-stu-id="58d9d-116">When you see a query variable that is typed as `IEnumerable<Customer>`, it just means that the query, when it is executed, will produce a sequence of zero or more `Customer` objects.</span></span>  
  
 <span data-ttu-id="58d9d-117">[!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="58d9d-117">[!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]</span></span>  
  
 <span data-ttu-id="58d9d-118">Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="58d9d-118">For more information, see [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a><span data-ttu-id="58d9d-119">Permitir que o compilador manipule as declarações de tipo genérico</span><span class="sxs-lookup"><span data-stu-id="58d9d-119">Letting the Compiler Handle Generic Type Declarations</span></span>  
 <span data-ttu-id="58d9d-120">Se preferir, poderá evitar a sintaxe genérica, usando a palavra-chave [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="58d9d-120">If you prefer, you can avoid generic syntax by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword.</span></span> <span data-ttu-id="58d9d-121">A palavra-chave `var` instrui o compilador a inferir o tipo de uma variável de consulta, examinando a fonte de dados especificada na cláusula `from`.</span><span class="sxs-lookup"><span data-stu-id="58d9d-121">The `var` keyword instructs the compiler to infer the type of a query variable by looking at the data source specified in the `from` clause.</span></span> <span data-ttu-id="58d9d-122">O exemplo a seguir produz o mesmo código compilado que o exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="58d9d-122">The following example produces the same compiled code as the previous example:</span></span>  
  
 <span data-ttu-id="58d9d-123">[!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="58d9d-123">[!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]</span></span>  
  
 <span data-ttu-id="58d9d-124">A palavra-chave `var` é útil quando o tipo da variável for óbvio ou quando não é tão importante especificar explicitamente os tipos genéricos aninhados, como aqueles que são produzidos por consultas de grupo.</span><span class="sxs-lookup"><span data-stu-id="58d9d-124">The `var` keyword is useful when the type of the variable is obvious or when it is not that important to explicitly specify nested generic types such as those that are produced by group queries.</span></span> <span data-ttu-id="58d9d-125">É recomendável que você note que o código poderá se tornar mais difícil de ser lido por outras pessoas, caso você use a `var`.</span><span class="sxs-lookup"><span data-stu-id="58d9d-125">In general, we recommend that if you use `var`, realize that it can make your code more difficult for others to read.</span></span> <span data-ttu-id="58d9d-126">Para obter mais informações, consulte [Variáveis Locais de Tipo Implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="58d9d-126">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d9d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58d9d-127">See Also</span></span>  
 <span data-ttu-id="58d9d-128">[Introdução ao LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="58d9d-128">[Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 [<span data-ttu-id="58d9d-129">Genéricos</span><span class="sxs-lookup"><span data-stu-id="58d9d-129">Generics</span></span>](../../../../csharp/programming-guide/generics/index.md)

