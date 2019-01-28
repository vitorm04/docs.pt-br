---
title: Ordenar os resultados de uma cláusula join (LINQ em C#)
description: Saiba como ordenar os resultados de uma cláusula join de LINQ em C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857882"
---
# <a name="order-the-results-of-a-join-clause"></a>Ordenar os resultados de uma cláusula join

Este exemplo mostra como ordenar os resultados de uma operação de junção. Observe que a ordenação é executada após a junção. Embora você possa usar uma cláusula `orderby` com uma ou mais sequências de origem antes da junção, normalmente não é recomendável. Alguns provedores LINQ não podem preservar essa ordem após a junção.

## <a name="example"></a>Exemplo

Esta consulta cria uma junção de grupos e classifica os grupos com base no elemento de categoria, que ainda está no escopo. Dentro do inicializador de tipo anônimo, uma subconsulta ordena todos os elementos de correspondência da sequência de produtos.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](index.md)
- [Cláusula orderby](../language-reference/keywords/orderby-clause.md)
- [Cláusula join](../language-reference/keywords/join-clause.md)
