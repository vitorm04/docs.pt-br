---
title: parâmetros
ms.date: 12/13/2019
description: Aprenda a usar parâmetros SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400452"
---
# <a name="parameters"></a>parâmetros

Os parâmetros são usados para proteger contra ataques de injeção SQL. Em vez de concatenar a entrada do usuário com instruções SQL, use parâmetros para garantir que a entrada seja tratada apenas como um valor literal e nunca executada. No SQLite, os parâmetros são normalmente permitidos em qualquer lugar que um literal seja permitido em declarações SQL.

Os parâmetros podem `:`ser `@`prefixados com ou , ou `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Consulte [os tipos de dados](types.md) para obter detalhes sobre como os valores .NET são mapeados para os valores do SQLite.

## <a name="truncation"></a>Truncation

Use <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> a propriedade para truncar valores de TEXTO e BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Tipos alternativos

Às vezes, você pode querer usar um tipo SQLite alternativo. Faça isso definindo a <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> propriedade.

Os seguintes mapeamentos de tipo alternativos podem ser usados. Para os mapeamentos padrão, consulte [Tipos de dados](types.md).

| Valor          | SqliteType | Comentários          |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| Datetime       | Real       | Valor do dia de Julian |
| DateTimeOffset | Real       | Valor do dia de Julian |
| Guid           | Blob       |                  |
| TimeSpan       | Real       | Em dias          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Parâmetros de saída

O SQLite não suporta parâmetros de saída. Em vez disso, os valores de retorno nos resultados da consulta.

## <a name="see-also"></a>Confira também

* [Tipos de dados](types.md)
