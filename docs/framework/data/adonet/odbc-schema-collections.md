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
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
|TIPO DE|Int16|  
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
|BASE|Int16|  
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
|BASE|Int16|  
|PERMITE VALOR NULO|Int16|  
|COMENTÁRIOS|Cadeia de Caracteres|  
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
|BASE|Int16|  
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
|BASE|Int16|  
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
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
