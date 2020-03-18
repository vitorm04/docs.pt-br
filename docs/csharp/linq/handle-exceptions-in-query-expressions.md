---
title: Tratar exceções em expressões de consulta (LINQ em C#)
description: Saiba como tratar exceções em expressões de consulta LINQ em C#.
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688495"
---
# <a name="handle-exceptions-in-query-expressions"></a>Tratar exceções em expressões de consulta

É possível chamar qualquer método no contexto de uma expressão de consulta. No entanto, é recomendável que você evite chamar qualquer método em uma expressão de consulta que possa criar um efeito colateral, como modificar o conteúdo da fonte de dados ou gerar uma exceção. Este exemplo mostra como evitar exceções ao chamar métodos em uma expressão de consulta, sem violar as diretrizes gerais sobre tratamento de exceção do .NET. Essas diretrizes declaram que é aceitável capturar uma exceção específica quando você entende por que ela é gerada em um determinado contexto. Para obter mais informações, consulte [As Melhores Práticas para Exceções](../../standard/exceptions/best-practices-for-exceptions.md).

O último exemplo mostra como tratar os casos em que é necessário lançar uma exceção durante a execução de uma consulta.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como mover o código de tratamento de exceção para fora de uma expressão de consulta. Isso só é possível quando o método não depende de nenhuma variável que seja local para a consulta.

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a>Exemplo

Em alguns casos, a melhor resposta para uma exceção que é lançada de dentro de uma consulta poderá ser a interrupção imediata da execução da consulta. O exemplo a seguir mostra como tratar exceções que podem ser geradas de dentro de um corpo de consulta. Suponha que `SomeMethodThatMightThrow` possa causar uma exceção que exija que a execução da consulta seja interrompida.

Observe que o bloco `try` inclui o loop `foreach` e não a própria consulta. Isso ocorre porque o loop `foreach` é o ponto em que a consulta é realmente executada. Para obter mais informações, consulte [Introdução às consultas LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a>Confira também

- [Consulta Integrada ao Idioma (LINQ)](index.md)
