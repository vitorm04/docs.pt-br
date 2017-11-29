---
title: "into (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords: into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a><span data-ttu-id="056c3-102">into (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="056c3-102">into (C# Reference)</span></span>
<span data-ttu-id="056c3-103">A palavra-chave contextual `into` pode ser usada para criar um identificador temporário para armazenar os resultados de uma cláusula [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) ou [select](../../../csharp/language-reference/keywords/select-clause.md) em um novo identificador.</span><span class="sxs-lookup"><span data-stu-id="056c3-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="056c3-104">Esse identificador por si só pode ser um gerador de comandos de consulta adicionais.</span><span class="sxs-lookup"><span data-stu-id="056c3-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="056c3-105">Quando usado em uma cláusula `group` ou `select`, o uso do novo identificador é, às vezes, conhecido como uma *continuação*.</span><span class="sxs-lookup"><span data-stu-id="056c3-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="056c3-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="056c3-106">Example</span></span>  
 <span data-ttu-id="056c3-107">O exemplo a seguir mostra o uso da palavra-chave `into` para habilitar um identificador temporário `fruitGroup` que tem um tipo inferido de `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="056c3-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="056c3-108">Usando o identificador, é possível invocar o método <xref:System.Linq.Enumerable.Count%2A> em cada grupo e selecionar apenas os grupos que contêm duas ou mais palavras.</span><span class="sxs-lookup"><span data-stu-id="056c3-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 <span data-ttu-id="056c3-109">O uso de `into` em uma cláusula `group` só é necessário quando você deseja realizar operações de consulta adicionais em cada grupo.</span><span class="sxs-lookup"><span data-stu-id="056c3-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="056c3-110">Para obter mais informações, consulte [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="056c3-110">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="056c3-111">Para obter um exemplo do uso de `into` em uma cláusula `join`, consulte [cláusula join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="056c3-111">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056c3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="056c3-112">See Also</span></span>  
 [<span data-ttu-id="056c3-113">Palavras-chave de Consulta (LINQ)</span><span class="sxs-lookup"><span data-stu-id="056c3-113">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="056c3-114">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="056c3-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="056c3-115">Cláusula group</span><span class="sxs-lookup"><span data-stu-id="056c3-115">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)
