---
title: Manipular valores nulos em expressões de consulta (LINQ em C#)
description: Saiba como manipular valores nulos em expressões de consulta LINQ em C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736861"
---
# <a name="handle-null-values-in-query-expressions"></a>Manipular valores nulos em expressões de consulta

Este exemplo mostra como tratar os possíveis valores nulos em coleções de origem. Uma coleção de objetos, tal como uma <xref:System.Collections.Generic.IEnumerable%601>, pode conter elementos cujo valor é [null](../language-reference/keywords/null.md). Se uma coleção de origem for nula ou contiver um elemento cujo valor for null e sua consulta não lidar com valores null, uma <xref:System.NullReferenceException> será gerada ao executar a consulta.

## <a name="example"></a>Exemplo

Você pode escrever o código defensivamente para evitar uma exceção de referência nula conforme mostrado no exemplo a seguir:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

No exemplo anterior, a cláusula `where` filtra todos os elementos nulos na sequência de categorias. Essa técnica é independente da verificação de nulos na cláusula join. A expressão condicional com null nesse exemplo funciona porque `Products.CategoryID` é do tipo `int?` que é uma abreviação para `Nullable<int>`.

## <a name="example"></a>Exemplo

Em uma cláusula join, se apenas uma das chaves de comparação for um tipo de valor que permite valor nulo, você pode converter a outra para um tipo que permite valor nulo na expressão de consulta. No exemplo a seguir, suponha que `EmployeeID` é uma coluna que contém os valores do tipo `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Nullable%601>
- [LINQ (Consulta Integrada à Linguagem)](index.md)
- [Tipos de valor anuláveis](../language-reference/builtin-types/nullable-value-types.md)
