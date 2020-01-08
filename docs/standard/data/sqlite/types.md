---
title: Tipos de dados
ms.date: 12/13/2019
description: Descreve os tipos de dados com suporte e algumas das limitações em relação a eles.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447177"
---
# <a name="data-types"></a>Tipos de dados

O SQLite tem apenas quatro tipos de dados primitivos: inteiro, REAL, texto e BLOB. As APIs que retornam valores de banco de dados como um `object` apenas retornará um desses quatro tipos. Os tipos .NET adicionais são suportados pelo Microsoft. Data. sqlite, mas os valores são, em última análise, impostos entre esses tipos e um dos quatro tipos primitivos.

| .NET           | SQLite  | Comentários                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Booliano        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DateTime       | TEXT    | aaaa-MM-DD HH: mm: SS. FFFFFFF                                   |
| DateTimeOffset | TEXT    | aaaa-MM-DD HH: mm: SS. FFFFFFFzzz                                |
| Decimal        | TEXT    | formato de `0.0###########################`. REAL seria uma perda. |
| Duplo         | REAL    |                                                               |
| {1&gt;Guid&lt;1}           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Simples         | REAL    |                                                               |
| Cadeia de caracteres         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: SS. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Estouro de valores grandes                                         |

## <a name="alternative-types"></a>Tipos alternativos

Alguns tipos .NET podem ser lidos de tipos SQLite alternativos. Os parâmetros também podem ser configurados para usar esses tipos alternativos. Para obter mais informações, confira [Parâmetros](parameters.md#alternative-types).

| .NET           | SQLite  | Comentários          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | REAL    | Valor do dia Juliano |
| DateTimeOffset | REAL    | Valor do dia Juliano |
| {1&gt;Guid&lt;1}           | BLOB    |                  |
| TimeSpan       | REAL    | Em dias          |

Por exemplo, a consulta a seguir lê um valor TimeSpan de uma coluna REAL no conjunto de resultados.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Tipos de coluna

O SQLite usa um sistema de tipos dinâmico em que o tipo de um valor é associado ao próprio valor e não à coluna onde ele está armazenado. Você está livre para usar qualquer nome de tipo de coluna desejado. Microsoft. Data. sqlite não aplicará nenhuma semântica adicional a esses nomes.

O nome do tipo de coluna tem um impacto sobre a [afinidade de tipo](https://www.sqlite.org/datatype3.html#type_affinity). Uma pegadinha comum é que o uso de um tipo de coluna de cadeia de caracteres tentará converter valores em inteiro ou REAL, o que pode levar a resultados inesperados. É recomendável usar apenas os quatro nomes de tipo do SQLite primitivo: inteiro, REAL, texto e BLOB.

O SQLite permite que você especifique facetas de tipo, como comprimento, precisão e escala, mas elas não são impostas pelo mecanismo de banco de dados. Seu aplicativo é responsável por impor esses.

## <a name="see-also"></a>Veja também

- [Tipos de texto no SQLite](https://www.sqlite.org/datatype3.html)
