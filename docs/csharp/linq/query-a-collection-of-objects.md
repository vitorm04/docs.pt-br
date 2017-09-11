---
title: "Consultar uma coleção de objetos"
description: "Como consultar coleções."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e08f2e5877ffe24f5a238ab19abb9760cb442f2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="b46c4-104">Consultar uma coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="b46c4-104">Query a collection of objects</span></span>
<span data-ttu-id="b46c4-105">Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="b46c4-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="b46c4-106">Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.</span><span class="sxs-lookup"><span data-stu-id="b46c4-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="b46c4-107">Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.</span><span class="sxs-lookup"><span data-stu-id="b46c4-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b46c4-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b46c4-108">Example</span></span>  
 <span data-ttu-id="b46c4-109">A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.</span><span class="sxs-lookup"><span data-stu-id="b46c4-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 <span data-ttu-id="b46c4-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b46c4-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span></span>  
  
 <span data-ttu-id="b46c4-111">Essa consulta é intencionalmente simples para que você possa testar.</span><span class="sxs-lookup"><span data-stu-id="b46c4-111">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="b46c4-112">Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="b46c4-112">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="b46c4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b46c4-113">See also</span></span>  
 [<span data-ttu-id="b46c4-114">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="b46c4-114">LINQ Query Expressions</span></span>](index.md)

