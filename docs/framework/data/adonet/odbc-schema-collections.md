---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772041"
---
# <a name="odbc-schema-collections"></a>Coleções de esquema ODBC

Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.

## <a name="microsoft-sql-server-odbc-driver"></a>Driver ODBC do Microsoft SQL Server

O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:

- Tabelas

- Índices

- Colunas

- Procedimentos

- ProcedureColumns

- ProcedureParameters

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
|TIPO|Int16|
|ORDINAL_POSITION|Int16|
|COLUMN_NAME|Cadeia de Caracteres|
|ASC_OR_DESC|Cadeia de Caracteres|
|CARDINALIDADE|Int32|
|PÁGINAS|Int32|
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
|PERMITE VALOR NULO|Int16|
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
|PERMITE VALOR NULO|Int16|
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

### <a name="procedureparameters"></a>ProcedureParameters

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
|PERMITE VALOR NULO|Int16|
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

## <a name="microsoft-oracle-odbc-driver"></a>Driver ODBC do Microsoft Oracle

O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:

- Tabelas

- Colunas

- Procedimentos

- ProcedureColumns

- ProcedureParameters

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
|PRECISÃO|Int32|
|COMPRIMENTO|Int32|
|ESCALA|Int16|
|RADIX|Int16|
|PERMITE VALOR NULO|Int16|
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
|PRECISÃO|Int32|
|COMPRIMENTO|Int32|
|ESCALA|Int16|
|RADIX|Int16|
|PERMITE VALOR NULO|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|SOBRECARGA|Int32|
|ORDINAL_POSITION|Int32|

## <a name="microsoft-jet-odbc-driver"></a>Microsoft Jet ODBC Driver

O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:

- Tabelas

- Índices

- Colunas

- Procedimentos

- ProcedureColumns

- ProcedureParameters

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
|PRECISÃO|Int32|
|COMPRIMENTO|Int32|
|ESCALA|Int16|
|RADIX|Int16|
|PERMITE VALOR NULO|Int16|
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
|PRECISÃO|Int32|
|COMPRIMENTO|Int32|
|ESCALA|Int16|
|RADIX|Int16|
|PERMITE VALOR NULO|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|SOBRECARGA|Int32|
|ORDINAL_POSITION|Int32|

### <a name="procedureparameters"></a>ProcedureParameters

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
|PERMITE VALOR NULO|Int16|
|COMENTÁRIOS|Cadeia de Caracteres|
|COLUMN_DEF|Cadeia de Caracteres|
|SQL_DATA_TYPE|Int16|
|SQL_DATETIME_SUB|Int16|
|CHAR_OCTET_LENGTH|Int32|
|ORDINAL_POSITION|Int32|
|IS_NULLABLE|Cadeia de Caracteres|

## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
