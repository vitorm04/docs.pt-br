---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794722"
---
# <a name="odbc-schema-collections"></a>Coleções de esquema ODBC

Esta seção discute o suporte da coleção de esquemas para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.

## <a name="microsoft-sql-server-odbc-driver"></a>Microsoft SQL Server driver ODBC

O driver ODBC Microsoft SQL Server dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:

- Tabelas

- Índices

- Colunas

- Procedimentos

- ProcedureColumns

- Procedimentoparameters

- Exibições

### <a name="tables-and-views"></a>Tabelas e exibições

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Cadeia de Caracteres|
|TABLE_SCHEM|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|TABLE_TYPE|Cadeia de Caracteres|
|COMENTÁRIOS|Cadeia de Caracteres|

### <a name="indexes"></a>Índices

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Cadeia de Caracteres|
|TABLE_SCHEM|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|NON_UNIQUE|Int16|
|INDEX_QUALIFIER|Cadeia de Caracteres|
|INDEX_NAME|Cadeia de Caracteres|
|ESCREVA|Int16|
|ORDINAL_POSITION|Int16|
|COLUMN_NAME|Cadeia de Caracteres|
|ASC_OR_DESC|Cadeia de Caracteres|
|CARDINALIDADE|Int32|
|PAGES|Int32|
|FILTER_CONDITION|Cadeia de Caracteres|
|SS_TYPE_SCHEMA|Cadeia de Caracteres|
|SS_DATA_TYPE|Byte|

### <a name="columns"></a>Colunas

|ColumnName|DataType|
|----------------|--------------|
|TABLE_CAT|Cadeia de Caracteres|
|TABLE_SCHEM|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|COLUMN_DEF|Cadeia de Caracteres|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Cadeia de Caracteres|
|SS_TYPE_CATALOG|Cadeia de Caracteres|
|SS_TYPE_SCHEMA|Cadeia de Caracteres|
|SS_DATA_TYPE|Byte|

### <a name="procedures"></a>Procedimentos

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Cadeia de Caracteres|
|PROCEDURE_SCHEM|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|NUM_INPUT_PARAMS|Int32|
|NUM_OUTPUT_PARAMS|Int32|
|NUM_RESULT_SETS|Int32|
|COMENTÁRIOS|Cadeia de Caracteres|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Cadeia de Caracteres|
|PROCEDURE_SCHEM|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|COLUMN_DEF|Cadeia de Caracteres|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Cadeia de Caracteres|
|SS_TYPE_CATALOG|Cadeia de Caracteres|
|SS_TYPE_SCHEMA|Cadeia de Caracteres|
|SS_DATA_TYPE|Byte|

### <a name="procedureparameters"></a>Procedimentoparameters

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Cadeia de Caracteres|
|PROCEDURE_SCHEM|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|COLUMN_DEF|Cadeia de Caracteres|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Cadeia de Caracteres|
|SS_TYPE_CATALOG|Cadeia de Caracteres|
|SS_TYPE_SCHEMA|Cadeia de Caracteres|
|SS_DATA_TYPE|Byte|

## <a name="microsoft-oracle-odbc-driver"></a>Driver ODBC da Microsoft Oracle

O driver ODBC do Microsoft SQL Server da Oracle dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:

- Tabelas

- Colunas

- Procedimentos

- ProcedureColumns

- Procedimentoparameters

- Exibições

- Índices

### <a name="tables-and-views"></a>Tabelas e exibições

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Cadeia de Caracteres|
|TABLE_OWNER|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|TABLE_TYPE|Cadeia de Caracteres|
|COMENTÁRIOS|Cadeia de Caracteres|

### <a name="columns"></a>Colunas

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Cadeia de Caracteres|
|TABLE_OWNER|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|PRECISO|Int32|
|MUITO|Int32|
|ESCALONÁVE|Int16|
|RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|ORDINAL_POSITION|Int32|

### <a name="procedures"></a>Procedimentos

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Cadeia de Caracteres|
|PROCEDURE_OWNER|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|NUM_INPUT_PARAMS|Int16|
|NUM_OUTPUT_PARAMS|Int16|
|NUM_RESULT_SETS|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Cadeia de Caracteres|
|PROCEDURE_OWNER|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|PRECISO|Int32|
|MUITO|Int32|
|ESCALONÁVE|Int16|
|RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|SOBRECARGA|Int32|
|ORDINAL_POSITION|Int32|

## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC Driver

O driver ODBC do Microsoft Jet dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:

- Tabelas

- Índices

- Colunas

- Procedimentos

- ProcedureColumns

- Procedimentoparameters

- Exibições

### <a name="tables-and-views"></a>Tabelas e exibições

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Cadeia de Caracteres|
|TABLE_OWNER|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|TABLE_TYPE|Cadeia de Caracteres|
|COMENTÁRIOS|Cadeia de Caracteres|

### <a name="columns"></a>Colunas

|ColumnName|DataType|
|----------------|--------------|
|TABLE_QUALIFIER|Cadeia de Caracteres|
|TABLE_OWNER|Cadeia de Caracteres|
|TABLE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|PRECISO|Int32|
|MUITO|Int32|
|ESCALONÁVE|Int16|
|RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|ORDINAL_POSITION|Int32|

### <a name="procedures"></a>Procedimentos

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Cadeia de Caracteres|
|PROCEDURE_OWNER|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|NUM_INPUT_PARAMS|Int16|
|NUM_OUTPUT_PARAMS|Int16|
|NUM_RESULT_SETS|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|PROCEDURE_TYPE|Int16|

### <a name="procedurecolumns"></a>ProcedureColumns

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_QUALIFIER|Cadeia de Caracteres|
|PROCEDURE_OWNER|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|PRECISO|Int32|
|MUITO|Int32|
|ESCALONÁVE|Int16|
|RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|SOBRECARGA|Int32|
|ORDINAL_POSITION|Int32|

### <a name="procedureparameters"></a>Procedimentoparameters

|ColumnName|DataType|
|----------------|--------------|
|PROCEDURE_CAT|Cadeia de Caracteres|
|PROCEDURE_SCHEM|Cadeia de Caracteres|
|PROCEDURE_NAME|Cadeia de Caracteres|
|COLUMN_NAME|Cadeia de Caracteres|
|COLUMN_TYPE|Int16|
|DATA_TYPE|Int16|
|TYPE_NAME|Cadeia de Caracteres|
|COLUMN_SIZE|Int32|
|BUFFER_LENGTH|Int32|
|DECIMAL_DIGITS|Int16|
|NUM_PREC_RADIX|Int16|
|ANULA|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|COLUMN_DEF|Cadeia de Caracteres|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Cadeia de Caracteres|

## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
