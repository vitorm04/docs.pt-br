---
title: Coleções de esquema de OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771989"
---
# <a name="ole-db-schema-collections"></a>Coleções de esquema de OLE DB
Esta seção discute o suporte de coleção de esquema para os provedores OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Provedor Microsoft SQL Server, OLE DB  
 O Microsoft OLE DB Driver do SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:  
  
- Tabelas  
  
- Colunas  
  
- Procedimentos  
  
- ProcedureParameters  
  
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
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
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
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO|Int32|  
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
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Provedor OLE DB Microsoft Oracle  
 O Microsoft OLE DB Driver Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:  
  
- Tabelas  
  
- Colunas  
  
- Procedimentos  
  
- ProcedureColumns  
  
- ProcedureParameters  
  
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
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO|Int32|  
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
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Provedor OLE DB Microsoft Jet  
 O Microsoft Jet OLE DB Driver suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:  
  
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
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO|Int32|  
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
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de Caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
