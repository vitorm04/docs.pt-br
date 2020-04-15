---
title: Tipos de dados
ms.date: 12/13/2019
description: Descreve os tipos de dados suportados e algumas das limitações ao seu redor.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389038"
---
# <a name="data-types"></a>Tipos de dados

O SQLite só tem quatro tipos de dados primitivos: INTEGER, REAL, TEXT e BLOB. As APIs que retornam `object` os valores do banco de dados como um só retornarão um desses quatro tipos. Tipos adicionais .NET são suportados pelo Microsoft.Data.Sqlite, mas os valores são, em última análise, coagidos entre esses tipos e um dos quatro tipos primitivos.

| .NET           | SQLite  | Comentários                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` ou `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| Datetime       | TEXT    | yyyy-MM-dd HH:mm:ss. Fffffff                                   |
| DateTimeOffset | TEXT    | yyyy-MM-dd HH:mm:ss. FFFFFFFzzz                                |
| Decimal        | TEXT    | `0.0###########################`Formato. REAL seria perda. |
| Double         | real    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | real    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| TimeSpan       | TEXT    | d.hh:mm:ss.fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | Grandes valores transbordam                                         |

## <a name="alternative-types"></a>Tipos alternativos

Alguns tipos .NET podem ser lidos a partir de tipos SQLite alternativos. Os parâmetros também podem ser configurados para usar esses tipos alternativos. Para obter mais informações, confira [Parâmetros](parameters.md#alternative-types).

| .NET           | SQLite  | Comentários          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| Datetime       | real    | Valor do dia de Julian |
| DateTimeOffset | real    | Valor do dia de Julian |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | Em dias          |

Por exemplo, a consulta a seguir lê um valor timespan de uma coluna REAL no conjunto de resultados.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Tipos de coluna

O SQLite usa um sistema de tipo dinâmico onde o tipo de valor está associado ao valor em si e não à coluna onde está armazenado. Você é livre para usar o nome do tipo de coluna que quiser. O Microsoft.Data.Sqlite não aplicará nenhuma semântica adicional a esses nomes.

O nome do tipo da coluna tem um impacto na afinidade do [tipo](https://www.sqlite.org/datatype3.html#type_affinity). Um gotcha comum é que o uso de um tipo de coluna de STRING tentará converter valores para INTEGER ou REAL, o que pode levar a resultados inesperados. Recomendamos apenas o uso dos quatro nomes do tipo SQLite primitivos: INTEGER, REAL, TEXT e BLOB.

O SQLite permite especificar facetas de tipo como comprimento, precisão e escala, mas elas não são aplicadas pelo mecanismo do banco de dados. Seu aplicativo é responsável por aplicá-los.

## <a name="see-also"></a>Confira também

- [Tipos de dados no SQLite](https://www.sqlite.org/datatype3.html)
