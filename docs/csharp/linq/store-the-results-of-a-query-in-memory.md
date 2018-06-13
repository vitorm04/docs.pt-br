---
title: Armazenar os resultados de uma consulta na memória
description: Como armazenar os resultados.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279627"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Armazenar os resultados de uma consulta na memória

Uma consulta é basicamente um conjunto de instruções sobre como recuperar e organizar os dados. As consultas são executadas lentamente, conforme cada item subsequente no resultado é solicitado. Quando você usa `foreach` para iterar os resultados, os itens são retornados conforme acessado. Para avaliar uma consulta e armazenar os resultados sem executar um loop `foreach`, basta chamar um dos métodos a seguir na variável de consulta:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Recomendamos que ao armazenar os resultados da consulta, você atribua o objeto da coleção retornado a uma nova variável conforme mostrado no exemplo a seguir:  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
