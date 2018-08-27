---
title: Consultar uma coleção de objetos (LINQ em C#)
description: Saiba como consultar coleções usando LINQ em C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935535"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="581f3-103">Consultar uma coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="581f3-103">Query a collection of objects</span></span>

<span data-ttu-id="581f3-104">Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="581f3-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="581f3-105">Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.</span><span class="sxs-lookup"><span data-stu-id="581f3-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="581f3-106">Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.</span><span class="sxs-lookup"><span data-stu-id="581f3-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="581f3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="581f3-107">Example</span></span>

<span data-ttu-id="581f3-108">A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.</span><span class="sxs-lookup"><span data-stu-id="581f3-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="581f3-109">Essa consulta é intencionalmente simples para que você possa testar.</span><span class="sxs-lookup"><span data-stu-id="581f3-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="581f3-110">Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="581f3-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581f3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="581f3-111">See also</span></span>

- [<span data-ttu-id="581f3-112">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="581f3-112">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="581f3-113">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="581f3-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)