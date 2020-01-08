---
title: Parâmetros
ms.date: 12/13/2019
description: Saiba como usar parâmetros SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447184"
---
# <a name="parameters"></a>Parâmetros

Os parâmetros são usados para proteger contra ataques de injeção de SQL. Em vez de concatenar a entrada do usuário com instruções SQL, use parâmetros para garantir que a entrada seja tratada apenas como um valor literal e nunca executada. No SQLite, os parâmetros são geralmente permitidos em qualquer lugar que um literal é permitido em instruções SQL.

Os parâmetros podem ter como prefixo `:`, `@`ou `$`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Consulte [tipos de dados](types.md) para obter detalhes sobre como os valores do .NET são mapeados para os valores do SQLite.

## <a name="truncation"></a>Truncamento

Use a propriedade <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> para truncar valores de texto e BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Tipos alternativos

Às vezes, talvez você queira usar um tipo SQLite alternativo. Faça isso definindo a propriedade <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>.

Os mapeamentos de tipo alternativo a seguir podem ser usados. Para os mapeamentos padrão, consulte [tipos de dados](types.md).

| Value          | Sqlitetype | Comentários          |
| -------------- | ---------- | ---------------- |
| Char           | Inteiro    | UTF-16           |
| DateTime       | Real       | Valor do dia Juliano |
| DateTimeOffset | Real       | Valor do dia Juliano |
| {1&gt;Guid&lt;1}           | Blob       |                  |
| TimeSpan       | Real       | Em dias          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Parâmetros de saída

O SQLite não dá suporte a parâmetros de saída. Em vez disso, retorna valores nos resultados da consulta.

## <a name="see-also"></a>Veja também

* [Tipos de dados](types.md)
