---
title: Tipos de dados
ms.date: 12/13/2019
description: Descreve os tipos de dados com suporte e algumas das limitações em relação a eles.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389038"
---
# <a name="data-types"></a>Tipos de dados

O SQLite tem apenas quatro tipos de dados primitivos: inteiro, REAL, texto e BLOB. As APIs que retornam valores de `object` banco de dados como um só retornarão um desses quatro tipos. Os tipos .NET adicionais são suportados pelo Microsoft. Data. sqlite, mas os valores são, em última análise, impostos entre esses tipos e um dos quatro tipos primitivos.

| .NET           | SQLite  | Comentários                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| Datetime       | TEXT    | aaaa-MM-DD HH: mm: SS. FFFFFFF                                   |
| DateTimeOffset | TEXT    | aaaa-MM-DD HH: mm: SS. FFFFFFFzzz                                |
| Decimal        | TEXT    | `0.0###########################`ao. REAL seria uma perda. |
| Double         | real    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | real    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d. hh: mm: SS. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | Estouro de valores grandes                                         |

## <a name="alternative-types"></a>Tipos alternativos

Alguns tipos .NET podem ser lidos de tipos SQLite alternativos. Os parâmetros também podem ser configurados para usar esses tipos alternativos. Para obter mais informações, confira [Parâmetros](parameters.md#alternative-types).

| .NET           | SQLite  | Comentários          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| Datetime       | real    | Valor do dia Juliano |
| DateTimeOffset | real    | Valor do dia Juliano |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | Em dias          |

Por exemplo, a consulta a seguir lê um valor TimeSpan de uma coluna REAL no conjunto de resultados.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Tipos de coluna

O SQLite usa um sistema de tipos dinâmico em que o tipo de um valor é associado ao próprio valor e não à coluna onde ele está armazenado. Você está livre para usar qualquer nome de tipo de coluna desejado. Microsoft. Data. sqlite não aplicará nenhuma semântica adicional a esses nomes.

O nome do tipo de coluna tem um impacto sobre a [afinidade de tipo](https://www.sqlite.org/datatype3.html#type_affinity). Uma pegadinha comum é que o uso de um tipo de coluna de cadeia de caracteres tentará converter valores em inteiro ou REAL, o que pode levar a resultados inesperados. É recomendável usar apenas os quatro nomes de tipo do SQLite primitivo: inteiro, REAL, texto e BLOB.

O SQLite permite que você especifique facetas de tipo, como comprimento, precisão e escala, mas elas não são impostas pelo mecanismo de banco de dados. Seu aplicativo é responsável por impor esses.

## <a name="see-also"></a>Veja também

- [Tipos de texto no SQLite](https://www.sqlite.org/datatype3.html)
