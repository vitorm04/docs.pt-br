---
title: "Coleções de esquema ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a>Coleções de esquema ODBC
Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Driver ODBC do Microsoft SQL Server  
 O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Índices  
  
-   Colunas  
  
-   Procedimentos  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Exibições  
  
### <a name="tables-and-views"></a>Tabelas e exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Cadeia de caracteres|  
|TABLE_SCHEM|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|COMENTÁRIOS|Cadeia de caracteres|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Cadeia de caracteres|  
|TABLE_SCHEM|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|Cadeia de caracteres|  
|INDEX_NAME|Cadeia de caracteres|  
|TIPO DE|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|Cadeia de caracteres|  
|ASC_OR_DESC|Cadeia de caracteres|  
|CARDINALIDADE|Int32|  
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de caracteres|  
|SS_TYPE_SCHEMA|Cadeia de caracteres|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CAT|Cadeia de caracteres|  
|TABLE_SCHEM|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|COLUMN_DEF|Cadeia de caracteres|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Cadeia de caracteres|  
|SS_TYPE_CATALOG|Cadeia de caracteres|  
|SS_TYPE_SCHEMA|Cadeia de caracteres|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Cadeia de caracteres|  
|PROCEDURE_SCHEM|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|COMENTÁRIOS|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Cadeia de caracteres|  
|PROCEDURE_SCHEM|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|COLUMN_DEF|Cadeia de caracteres|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Cadeia de caracteres|  
|SS_TYPE_CATALOG|Cadeia de caracteres|  
|SS_TYPE_SCHEMA|Cadeia de caracteres|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Cadeia de caracteres|  
|PROCEDURE_SCHEM|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|COLUMN_DEF|Cadeia de caracteres|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Cadeia de caracteres|  
|SS_TYPE_CATALOG|Cadeia de caracteres|  
|SS_TYPE_SCHEMA|Cadeia de caracteres|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Driver ODBC do Microsoft Oracle  
 O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Colunas  
  
-   Procedimentos  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Exibições  
  
-   Índices  
  
### <a name="tables-and-views"></a>Tabelas e exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Cadeia de caracteres|  
|TABLE_OWNER|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|COMENTÁRIOS|Cadeia de caracteres|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Cadeia de caracteres|  
|TABLE_OWNER|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|PRECISÃO|Int32|  
|COMPRIMENTO|Int32|  
|ESCALA|Int16|  
|BASE|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Cadeia de caracteres|  
|PROCEDURE_OWNER|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Cadeia de caracteres|  
|PROCEDURE_OWNER|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|PRECISÃO|Int32|  
|COMPRIMENTO|Int32|  
|ESCALA|Int16|  
|BASE|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|SOBRECARGA|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Driver ODBC do Microsoft Jet  
 O Driver de ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Índices  
  
-   Colunas  
  
-   Procedimentos  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Exibições  
  
### <a name="tables-and-views"></a>Tabelas e exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Cadeia de caracteres|  
|TABLE_OWNER|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|COMENTÁRIOS|Cadeia de caracteres|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|Cadeia de caracteres|  
|TABLE_OWNER|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|PRECISÃO|Int32|  
|COMPRIMENTO|Int32|  
|ESCALA|Int16|  
|BASE|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Cadeia de caracteres|  
|PROCEDURE_OWNER|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|Cadeia de caracteres|  
|PROCEDURE_OWNER|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|PRECISÃO|Int32|  
|COMPRIMENTO|Int32|  
|ESCALA|Int16|  
|BASE|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|SOBRECARGA|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CAT|Cadeia de caracteres|  
|PROCEDURE_SCHEM|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|Cadeia de caracteres|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de caracteres|  
|COLUMN_DEF|Cadeia de caracteres|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|Cadeia de caracteres|  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
