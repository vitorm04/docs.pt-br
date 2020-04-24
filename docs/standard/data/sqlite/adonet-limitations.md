---
title: Limitações do ADO.NET
ms.date: 12/13/2019
description: Descreve algumas das limitações do ADO.NET que você pode encontrar.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901260"
---
# <a name="adonet-limitations"></a>Limitações do ADO.NET

O Microsoft. Data. sqlite fornece implementações de muitas das abstrações ADO.NET, mas há algumas limitações.

## <a name="database-schema-information"></a>Informações de esquema de banco de dados

Os metadados sobre os resultados da consulta estão <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> disponíveis usando o método.

`DbConnection.GetSchema()`Não está implementado. Essa API não é bem definida, portanto, é recomendável recuperar os metadados do banco de dados diretamente usando as APIs do SQLite padrão, como a tabela de [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) e o [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.

Para obter mais informações, consulte [metadados](metadata.md).

## <a name="systemtransactions"></a>System.Transactions

Microsoft. Data. sqlite ainda não dá suporte a System. Transactions. Em vez disso, use transações ADO.NET. Para obter mais informações, veja [Transações](transactions.md).

Forneça comentários sobre a falta de suporte para System. Transactions no problema [#13825](https://github.com/dotnet/efcore/issues/13825).

## <a name="data-adapters"></a>Adaptadores de dados

`DbDataAdapter`Ainda não está implementado pelo Microsoft. Data. sqlite. Isso significa que você só pode usar `DataSet` ADO.NET `DataTable` e carregar dados e não atualizá-los.

Use o Issue [#13838](https://github.com/dotnet/efcore/issues/13838) para fornecer comentários sobre `DbDataAdapter`a implementação.

## <a name="output-parameters"></a>Parâmetros de saída

O SQLite não dá suporte a parâmetros de saída.

## <a name="positional-parameters"></a>Parâmetros posicionais

Microsoft. Data. sqlite só dá suporte a [parâmetros](parameters.md)nomeados. Não há suporte para parâmetros posicionais.

## <a name="stored-procedures"></a>Procedimentos armazenados

O SQLite não dá suporte a procedimentos armazenados.

## <a name="isolation-levels"></a>Níveis de isolamento

Os `Chaos` níveis `Snapshot` de isolamento e não têm suporte em transações SQLite.

## <a name="see-also"></a>Veja também

* [Limitações assíncronas](async.md)
* [Tipos de dados](types.md)
* [Transactions](transactions.md)
