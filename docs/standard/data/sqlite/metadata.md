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
# <a name="metadata"></a><span data-ttu-id="78cf8-103">Metadados</span><span class="sxs-lookup"><span data-stu-id="78cf8-103">Metadata</span></span>

<span data-ttu-id="78cf8-104">Há duas APIs para recuperar metadados em ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="78cf8-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="78cf8-105">Uma recupera metadados sobre os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="78cf8-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="78cf8-106">O outro recupera metadados sobre o esquema de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="78cf8-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="78cf8-107">Metadados do resultado da consulta</span><span class="sxs-lookup"><span data-stu-id="78cf8-107">Query result metadata</span></span>

<span data-ttu-id="78cf8-108">Você pode recuperar metadados sobre os resultados de uma consulta usando o método <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> em `SqliteDataReader`.</span><span class="sxs-lookup"><span data-stu-id="78cf8-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="78cf8-109">O <xref:System.Data.DataTable> retornado contém as seguintes colunas:</span><span class="sxs-lookup"><span data-stu-id="78cf8-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="78cf8-110">Column</span><span class="sxs-lookup"><span data-stu-id="78cf8-110">Column</span></span>             | <span data-ttu-id="78cf8-111">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="78cf8-111">Type</span></span>    | <span data-ttu-id="78cf8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="78cf8-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="78cf8-113">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-113">Boolean</span></span> | <span data-ttu-id="78cf8-114">True se a coluna de origem puder ser nula.</span><span class="sxs-lookup"><span data-stu-id="78cf8-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="78cf8-115">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-115">String</span></span>  | <span data-ttu-id="78cf8-116">O nome do banco de dados da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="78cf8-116">The name of the origin column's database.</span></span> <span data-ttu-id="78cf8-117">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="78cf8-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="78cf8-118">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-118">String</span></span>  | <span data-ttu-id="78cf8-119">O nome sem alias da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="78cf8-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="78cf8-120">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="78cf8-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="78cf8-121">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-121">String</span></span>  | <span data-ttu-id="78cf8-122">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="78cf8-122">Always NULL.</span></span> <span data-ttu-id="78cf8-123">O SQLite não dá suporte a esquemas.</span><span class="sxs-lookup"><span data-stu-id="78cf8-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="78cf8-124">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-124">String</span></span>  | <span data-ttu-id="78cf8-125">O caminho para o arquivo de banco de dados especificado na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="78cf8-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="78cf8-126">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-126">String</span></span>  | <span data-ttu-id="78cf8-127">O nome da tabela da coluna de origem.</span><span class="sxs-lookup"><span data-stu-id="78cf8-127">The name of the origin column's table.</span></span> <span data-ttu-id="78cf8-128">Sempre nulo para expressões.</span><span class="sxs-lookup"><span data-stu-id="78cf8-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="78cf8-129">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-129">String</span></span>  | <span data-ttu-id="78cf8-130">O nome ou alias da coluna no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="78cf8-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="78cf8-131">Int32</span><span class="sxs-lookup"><span data-stu-id="78cf8-131">Int32</span></span>   | <span data-ttu-id="78cf8-132">O ordinal da coluna no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="78cf8-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="78cf8-133">Int32</span><span class="sxs-lookup"><span data-stu-id="78cf8-133">Int32</span></span>   | <span data-ttu-id="78cf8-134">Sempre-1.</span><span class="sxs-lookup"><span data-stu-id="78cf8-134">Always -1.</span></span> <span data-ttu-id="78cf8-135">Isso pode ser alterado em versões futuras do `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="78cf8-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="78cf8-136">{1&gt;Tipo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="78cf8-136">Type</span></span>    | <span data-ttu-id="78cf8-137">O tipo de dados padrão do .NET da coluna.</span><span class="sxs-lookup"><span data-stu-id="78cf8-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="78cf8-138">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="78cf8-138">String</span></span>  | <span data-ttu-id="78cf8-139">O tipo de dados do SQLite da coluna.</span><span class="sxs-lookup"><span data-stu-id="78cf8-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="78cf8-140">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-140">Boolean</span></span> | <span data-ttu-id="78cf8-141">True se o nome da coluna tiver um alias no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="78cf8-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="78cf8-142">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-142">Boolean</span></span> | <span data-ttu-id="78cf8-143">True se a coluna de origem tiver sido criada com a palavra-chave AutoIncrement.</span><span class="sxs-lookup"><span data-stu-id="78cf8-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="78cf8-144">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-144">Boolean</span></span> | <span data-ttu-id="78cf8-145">True se a coluna se originar de uma expressão na consulta.</span><span class="sxs-lookup"><span data-stu-id="78cf8-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="78cf8-146">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-146">Boolean</span></span> | <span data-ttu-id="78cf8-147">True se a coluna de origem fizer parte da chave primária.</span><span class="sxs-lookup"><span data-stu-id="78cf8-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="78cf8-148">Booliano</span><span class="sxs-lookup"><span data-stu-id="78cf8-148">Boolean</span></span> | <span data-ttu-id="78cf8-149">True se a coluna de origem for exclusiva.</span><span class="sxs-lookup"><span data-stu-id="78cf8-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="78cf8-150">Int16</span><span class="sxs-lookup"><span data-stu-id="78cf8-150">Int16</span></span>   | <span data-ttu-id="78cf8-151">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="78cf8-151">Always NULL.</span></span> <span data-ttu-id="78cf8-152">Isso pode ser alterado em versões futuras do `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="78cf8-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="78cf8-153">Int16</span><span class="sxs-lookup"><span data-stu-id="78cf8-153">Int16</span></span>   | <span data-ttu-id="78cf8-154">Sempre nulo.</span><span class="sxs-lookup"><span data-stu-id="78cf8-154">Always NULL.</span></span> <span data-ttu-id="78cf8-155">Isso pode ser alterado em versões futuras do `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="78cf8-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="78cf8-156">O exemplo a seguir mostra como usar `GetSchemaTable` para criar uma cadeia de caracteres de depuração que mostra metadados sobre um resultado:</span><span class="sxs-lookup"><span data-stu-id="78cf8-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="78cf8-157">Por exemplo, essa consulta produziria a seguinte cadeia de caracteres de depuração:</span><span class="sxs-lookup"><span data-stu-id="78cf8-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="78cf8-158">Metadados do esquema</span><span class="sxs-lookup"><span data-stu-id="78cf8-158">Schema metadata</span></span>

<span data-ttu-id="78cf8-159">Microsoft. Data. sqlite não implementa o método GetSchema em DbConnection.</span><span class="sxs-lookup"><span data-stu-id="78cf8-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="78cf8-160">Em vez disso, você pode consultar diretamente as informações de esquema usando as instruções Table [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) e PRAGMA como [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) e [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span><span class="sxs-lookup"><span data-stu-id="78cf8-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="78cf8-161">Por exemplo, essa consulta recuperará metadados sobre todas as colunas no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="78cf8-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="78cf8-162">Veja também</span><span class="sxs-lookup"><span data-stu-id="78cf8-162">See also</span></span>

* [<span data-ttu-id="78cf8-163">Armazenamento do esquema do banco de dados SQL</span><span class="sxs-lookup"><span data-stu-id="78cf8-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="78cf8-164">Instruções PRAGMA</span><span class="sxs-lookup"><span data-stu-id="78cf8-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="78cf8-165">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="78cf8-165">Data types</span></span>](types.md)
