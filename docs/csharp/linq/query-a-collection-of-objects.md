---
title: Consultar uma coleção de objetos (LINQ em C#)
description: Saiba como consultar coleções usando LINQ em C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659800"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="7b09d-103">Consultar uma coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="7b09d-103">Query a collection of objects</span></span>

<span data-ttu-id="7b09d-104">Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="7b09d-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="7b09d-105">Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.</span><span class="sxs-lookup"><span data-stu-id="7b09d-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="7b09d-106">Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.</span><span class="sxs-lookup"><span data-stu-id="7b09d-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b09d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b09d-107">Example</span></span>

<span data-ttu-id="7b09d-108">A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.</span><span class="sxs-lookup"><span data-stu-id="7b09d-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="7b09d-109">Essa consulta é intencionalmente simples para que você possa testar.</span><span class="sxs-lookup"><span data-stu-id="7b09d-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="7b09d-110">Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="7b09d-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b09d-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b09d-111">See also</span></span>

- [<span data-ttu-id="7b09d-112">Consulta Integrada ao Idioma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7b09d-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="7b09d-113">Interpolação de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b09d-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
