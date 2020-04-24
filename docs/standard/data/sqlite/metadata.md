---
title: Metadados
ms.date: 12/13/2019
description: Saiba como recuperar metadados sobre o banco de dados.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447191"
---
# <a name="metadata"></a><span data-ttu-id="c3ce5-103">Metadados</span><span class="sxs-lookup"><span data-stu-id="c3ce5-103">Metadata</span></span>

<span data-ttu-id="c3ce5-104">Há duas APIs para recuperar metadados em ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="c3ce5-105">Uma recupera metadados sobre os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="c3ce5-106">O outro recupera metadados sobre o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="c3ce5-107">Metadados do resultado da consulta</span><span class="sxs-lookup"><span data-stu-id="c3ce5-107">Query result metadata</span></span>

<span data-ttu-id="c3ce5-108">Você pode recuperar metadados sobre os resultados de uma consulta usando o <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> método em `SqliteDataReader`.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="c3ce5-109">O retornado <xref:System.Data.DataTable> contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="c3ce5-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="c3ce5-110">Coluna</span><span class="sxs-lookup"><span data-stu-id="c3ce5-110">Column</span></span>             | <span data-ttu-id="c3ce5-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="c3ce5-111">Type</span></span>    | <span data-ttu-id="c3ce5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3ce5-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="c3ce5-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-113">Boolean</span></span> | <span data-ttu-id="c3ce5-114">True se a coluna de origem puder ser nula.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="c3ce5-115">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-115">String</span></span>  | <span data-ttu-id="c3ce5-116">O nome do banco de dados da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-116">The name of the origin column's database.</span></span> <span data-ttu-id="c3ce5-117">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="c3ce5-118">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-118">String</span></span>  | <span data-ttu-id="c3ce5-119">O nome sem alias da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="c3ce5-120">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="c3ce5-121">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-121">String</span></span>  | <span data-ttu-id="c3ce5-122">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-122">Always NULL.</span></span> <span data-ttu-id="c3ce5-123">O SQLite não dá suporte a esquemas.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="c3ce5-124">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-124">String</span></span>  | <span data-ttu-id="c3ce5-125">O caminho para o arquivo de banco de dados especificado na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="c3ce5-126">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-126">String</span></span>  | <span data-ttu-id="c3ce5-127">O nome da tabela da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-127">The name of the origin column's table.</span></span> <span data-ttu-id="c3ce5-128">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="c3ce5-129">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-129">String</span></span>  | <span data-ttu-id="c3ce5-130">O nome ou alias da coluna no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="c3ce5-131">Int32</span><span class="sxs-lookup"><span data-stu-id="c3ce5-131">Int32</span></span>   | <span data-ttu-id="c3ce5-132">O ordinal da coluna no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="c3ce5-133">Int32</span><span class="sxs-lookup"><span data-stu-id="c3ce5-133">Int32</span></span>   | <span data-ttu-id="c3ce5-134">Sempre-1.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-134">Always -1.</span></span> <span data-ttu-id="c3ce5-135">Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="c3ce5-136">Tipo</span><span class="sxs-lookup"><span data-stu-id="c3ce5-136">Type</span></span>    | <span data-ttu-id="c3ce5-137">O tipo de dados padrão do .NET da coluna.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="c3ce5-138">String</span><span class="sxs-lookup"><span data-stu-id="c3ce5-138">String</span></span>  | <span data-ttu-id="c3ce5-139">O tipo de dados do SQLite da coluna.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="c3ce5-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-140">Boolean</span></span> | <span data-ttu-id="c3ce5-141">True se o nome da coluna tiver um alias no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="c3ce5-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-142">Boolean</span></span> | <span data-ttu-id="c3ce5-143">True se a coluna de origem tiver sido criada com a palavra-chave AutoIncrement.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="c3ce5-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-144">Boolean</span></span> | <span data-ttu-id="c3ce5-145">True se a coluna se originar de uma expressão na consulta.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="c3ce5-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-146">Boolean</span></span> | <span data-ttu-id="c3ce5-147">True se a coluna de origem fizer parte da chave primária.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="c3ce5-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3ce5-148">Boolean</span></span> | <span data-ttu-id="c3ce5-149">True se a coluna de origem for exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="c3ce5-150">Int16</span><span class="sxs-lookup"><span data-stu-id="c3ce5-150">Int16</span></span>   | <span data-ttu-id="c3ce5-151">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-151">Always NULL.</span></span> <span data-ttu-id="c3ce5-152">Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="c3ce5-153">Int16</span><span class="sxs-lookup"><span data-stu-id="c3ce5-153">Int16</span></span>   | <span data-ttu-id="c3ce5-154">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-154">Always NULL.</span></span> <span data-ttu-id="c3ce5-155">Isso pode ser alterado em versões futuras `Microsoft.Data.Sqlite`do.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="c3ce5-156">O exemplo a seguir mostra como usar `GetSchemaTable` o para criar uma cadeia de caracteres de depuração que mostra metadados sobre um resultado:</span><span class="sxs-lookup"><span data-stu-id="c3ce5-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="c3ce5-157">Por exemplo, essa consulta produziria a seguinte cadeia de caracteres de depuração:</span><span class="sxs-lookup"><span data-stu-id="c3ce5-157">For example, this query would produce the following debug string:</span></span>

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a><span data-ttu-id="c3ce5-158">Metadados do esquema</span><span class="sxs-lookup"><span data-stu-id="c3ce5-158">Schema metadata</span></span>

<span data-ttu-id="c3ce5-159">Microsoft. Data. sqlite não implementa o método GetSchema em DbConnection.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="c3ce5-160">Em vez disso, você pode consultar diretamente as informações de esquema usando as instruções Table [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) e PRAGMA como [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) e [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span><span class="sxs-lookup"><span data-stu-id="c3ce5-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="c3ce5-161">Por exemplo, essa consulta recuperará metadados sobre todas as colunas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c3ce5-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="c3ce5-162">Veja também</span><span class="sxs-lookup"><span data-stu-id="c3ce5-162">See also</span></span>

* [<span data-ttu-id="c3ce5-163">Armazenamento do esquema do banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="c3ce5-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="c3ce5-164">Instruções PRAGMA</span><span class="sxs-lookup"><span data-stu-id="c3ce5-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="c3ce5-165">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="c3ce5-165">Data types</span></span>](types.md)
