---
title: Consultar uma coleção de objetos
description: Como consultar coleções.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="29cf6-104">Consultar uma coleção de objetos</span><span class="sxs-lookup"><span data-stu-id="29cf6-104">Query a collection of objects</span></span>
<span data-ttu-id="29cf6-105">Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="29cf6-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="29cf6-106">Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.</span><span class="sxs-lookup"><span data-stu-id="29cf6-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="29cf6-107">Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.</span><span class="sxs-lookup"><span data-stu-id="29cf6-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29cf6-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29cf6-108">Example</span></span>  
 <span data-ttu-id="29cf6-109">A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.</span><span class="sxs-lookup"><span data-stu-id="29cf6-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="29cf6-110">Essa consulta é intencionalmente simples para que você possa testar.</span><span class="sxs-lookup"><span data-stu-id="29cf6-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="29cf6-111">Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.</span><span class="sxs-lookup"><span data-stu-id="29cf6-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="29cf6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29cf6-112">See also</span></span>  
 [<span data-ttu-id="29cf6-113">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="29cf6-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="29cf6-114">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="29cf6-114">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
