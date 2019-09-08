---
title: Coleções de esquema de OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783454"
---
# <a name="ole-db-schema-collections"></a>Coleções de esquema de OLE DB
Esta seção discute o suporte à coleta de esquemas para os provedores de OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Provedor de OLE DB de Microsoft SQL Server  
 O driver de OLE DB Microsoft SQL Server dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:  
  
- Tabelas  
  
- Colunas  
  
- Procedimentos  
  
- Procedimentoparameters  
  
- Catálogo  
  
- Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|TABLE_TYPE|Cadeia de Caracteres|  
|TABLE_GUID|Guid|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de Caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|  
|COLLATION_CATALOG|Cadeia de Caracteres|  
|COLLATION_SCHEMA|Cadeia de Caracteres|  
|COLLATION_NAME|Cadeia de Caracteres|  
|DOMAIN_CATALOG|Cadeia de Caracteres|  
|DOMAIN_SCHEMA|Cadeia de Caracteres|  
|DOMAIN_NAME|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de Caracteres|  
|PROCEDURE_SCHEMA|Cadeia de Caracteres|  
|PROCEDURE_NAME|Cadeia de Caracteres|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedureparameters"></a>Procedimentoparameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de Caracteres|  
|PROCEDURE_SCHEMA|Cadeia de Caracteres|  
|PROCEDURE_NAME|Cadeia de Caracteres|  
|PARAMETER_NAME|Cadeia de Caracteres|  
|ORDINAL_POSITION|Int32|  
|PARAMETER_TYPE|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|Cadeia de Caracteres|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|TYPE_NAME|Cadeia de Caracteres|  
|LOCAL_TYPE_NAME|Cadeia de Caracteres|  
  
### <a name="catalog"></a>Catálogo  
  
|ColumnName|DataType|  
|----------------|--------------|  
|CATALOG_NAME|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|INDEX_CATALOG|Cadeia de Caracteres|  
|INDEX_SCHEMA|Cadeia de Caracteres|  
|INDEX_NAME|Cadeia de Caracteres|  
|PRIMARY_KEY|Boolean|  
|DIFERENTE|Boolean|  
|CLUSTERED|Boolean|  
|ESCREVA|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PAGES|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|TOTALMENTE|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Provedor de OLE DB Microsoft Oracle  
 O driver Microsoft Oracle OLE DB dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:  
  
- Tabelas  
  
- Colunas  
  
- Procedimentos  
  
- ProcedureColumns  
  
- Procedimentoparameters  
  
- Exibições  
  
- Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|TABLE_TYPE|Cadeia de Caracteres|  
|TABLE_GUID|Guid|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de Caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|  
|COLLATION_CATALOG|Cadeia de Caracteres|  
|COLLATION_SCHEMA|Cadeia de Caracteres|  
|COLLATION_NAME|Cadeia de Caracteres|  
|DOMAIN_CATALOG|Cadeia de Caracteres|  
|DOMAIN_SCHEMA|Cadeia de Caracteres|  
|DOMAIN_NAME|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de Caracteres|  
|PROCEDURE_SCHEMA|Cadeia de Caracteres|  
|PROCEDURE_NAME|Cadeia de Caracteres|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de Caracteres|  
|PROCEDURE_SCHEMA|Cadeia de Caracteres|  
|PROCEDURE_NAME|Cadeia de Caracteres|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|SOBRECARGA|Int16|  
  
### <a name="views"></a>Exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|VIEW_DEFINITION|Cadeia de Caracteres|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|INDEX_CATALOG|Cadeia de Caracteres|  
|INDEX_SCHEMA|Cadeia de Caracteres|  
|INDEX_NAME|Cadeia de Caracteres|  
|PRIMARY_KEY|Boolean|  
|DIFERENTE|Boolean|  
|CLUSTERED|Boolean|  
|ESCREVA|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PAGES|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|TOTALMENTE|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Provedor de OLE DB do Microsoft Jet  
 O driver de OLE DB do Microsoft Jet dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:  
  
- Tabelas  
  
- Colunas  
  
- Procedimentos  
  
- Exibições  
  
- Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|TABLE_TYPE|Cadeia de Caracteres|  
|TABLE_GUID|Guid|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de Caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de Caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de Caracteres|  
|CHARACTER_SET_NAME|Cadeia de Caracteres|  
|COLLATION_CATALOG|Cadeia de Caracteres|  
|COLLATION_SCHEMA|Cadeia de Caracteres|  
|COLLATION_NAME|Cadeia de Caracteres|  
|DOMAIN_CATALOG|Cadeia de Caracteres|  
|DOMAIN_SCHEMA|Cadeia de Caracteres|  
|DOMAIN_NAME|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de Caracteres|  
|PROCEDURE_SCHEMA|Cadeia de Caracteres|  
|PROCEDURE_NAME|Cadeia de Caracteres|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|Cadeia de Caracteres|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="views"></a>Exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|VIEW_DEFINITION|Cadeia de Caracteres|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|DESCRIÇÃO|Cadeia de Caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de Caracteres|  
|TABLE_SCHEMA|Cadeia de Caracteres|  
|TABLE_NAME|Cadeia de Caracteres|  
|INDEX_CATALOG|Cadeia de Caracteres|  
|INDEX_SCHEMA|Cadeia de Caracteres|  
|INDEX_NAME|Cadeia de Caracteres|  
|PRIMARY_KEY|Boolean|  
|DIFERENTE|Boolean|  
|CLUSTERED|Boolean|  
|ESCREVA|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de Caracteres|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PAGES|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|TOTALMENTE|Boolean|  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
