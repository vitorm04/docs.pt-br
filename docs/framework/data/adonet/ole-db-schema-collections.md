---
title: "Coleções de esquema de banco de dados OLE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a>Coleções de esquema de banco de dados OLE
Esta seção discute o suporte de coleção de esquema para os provedores OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Provedor Microsoft SQL Server, OLE DB  
 O Microsoft OLE DB Driver do SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Colunas  
  
-   Procedimentos  
  
-   ProcedureParameters  
  
-   Catálogo  
  
-   Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|TABLE_GUID|GUID|  
|DESCRIÇÃO|Cadeia de caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de caracteres|  
|CHARACTER_SET_NAME|Cadeia de caracteres|  
|COLLATION_CATALOG|Cadeia de caracteres|  
|COLLATION_SCHEMA|Cadeia de caracteres|  
|COLLATION_NAME|Cadeia de caracteres|  
|DOMAIN_CATALOG|Cadeia de caracteres|  
|DOMAIN_SCHEMA|Cadeia de caracteres|  
|DOMAIN_NAME|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de caracteres|  
|PROCEDURE_SCHEMA|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
|DEFINIÇÃO_DO_PROCEDIMENTO|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de caracteres|  
|PROCEDURE_SCHEMA|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|PARAMETER_NAME|Cadeia de caracteres|  
|ORDINAL_POSITION|Int32|  
|TIPO_DE_PARÂMETRO|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|Cadeia de caracteres|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DESCRIÇÃO|Cadeia de caracteres|  
|TYPE_NAME|Cadeia de caracteres|  
|LOCAL_TYPE_NAME|Cadeia de caracteres|  
  
### <a name="catalog"></a>Catálogo  
  
|ColumnName|DataType|  
|----------------|--------------|  
|CATALOG_NAME|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|INDEX_CATALOG|Cadeia de caracteres|  
|INDEX_SCHEMA|Cadeia de caracteres|  
|INDEX_NAME|Cadeia de caracteres|  
|PRIMARY_KEY|Boolean|  
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO DE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Provedor OLE DB Microsoft Oracle  
 O Microsoft OLE DB Driver Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Colunas  
  
-   Procedimentos  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Exibições  
  
-   Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|TABLE_GUID|GUID|  
|DESCRIÇÃO|Cadeia de caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de caracteres|  
|CHARACTER_SET_NAME|Cadeia de caracteres|  
|COLLATION_CATALOG|Cadeia de caracteres|  
|COLLATION_SCHEMA|Cadeia de caracteres|  
|COLLATION_NAME|Cadeia de caracteres|  
|DOMAIN_CATALOG|Cadeia de caracteres|  
|DOMAIN_SCHEMA|Cadeia de caracteres|  
|DOMAIN_NAME|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de caracteres|  
|PROCEDURE_SCHEMA|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
|DEFINIÇÃO_DO_PROCEDIMENTO|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de caracteres|  
|PROCEDURE_SCHEMA|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DESCRIÇÃO|Cadeia de caracteres|  
|SOBRECARGA|Int16|  
  
### <a name="views"></a>Exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|VIEW_DEFINITION|Cadeia de caracteres|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|DESCRIÇÃO|Cadeia de caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|INDEX_CATALOG|Cadeia de caracteres|  
|INDEX_SCHEMA|Cadeia de caracteres|  
|INDEX_NAME|Cadeia de caracteres|  
|PRIMARY_KEY|Boolean|  
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO DE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Provedor do Microsoft Jet OLE DB  
 O Microsoft Jet OLE DB Driver suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:  
  
-   Tabelas  
  
-   Colunas  
  
-   Procedimentos  
  
-   Exibições  
  
-   Índices  
  
### <a name="tables"></a>Tabelas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|TABLE_TYPE|Cadeia de caracteres|  
|TABLE_GUID|GUID|  
|DESCRIÇÃO|Cadeia de caracteres|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Colunas  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|Cadeia de caracteres|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|Cadeia de caracteres|  
|CHARACTER_SET_SCHEMA|Cadeia de caracteres|  
|CHARACTER_SET_NAME|Cadeia de caracteres|  
|COLLATION_CATALOG|Cadeia de caracteres|  
|COLLATION_SCHEMA|Cadeia de caracteres|  
|COLLATION_NAME|Cadeia de caracteres|  
|DOMAIN_CATALOG|Cadeia de caracteres|  
|DOMAIN_SCHEMA|Cadeia de caracteres|  
|DOMAIN_NAME|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
  
### <a name="procedures"></a>Procedimentos  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|Cadeia de caracteres|  
|PROCEDURE_SCHEMA|Cadeia de caracteres|  
|PROCEDURE_NAME|Cadeia de caracteres|  
|PROCEDURE_TYPE|Int16|  
|DEFINIÇÃO_DO_PROCEDIMENTO|Cadeia de caracteres|  
|DESCRIÇÃO|Cadeia de caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="views"></a>Exibições  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|VIEW_DEFINITION|Cadeia de caracteres|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|DESCRIÇÃO|Cadeia de caracteres|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Índices  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|Cadeia de caracteres|  
|TABLE_SCHEMA|Cadeia de caracteres|  
|TABLE_NAME|Cadeia de caracteres|  
|INDEX_CATALOG|Cadeia de caracteres|  
|INDEX_SCHEMA|Cadeia de caracteres|  
|INDEX_NAME|Cadeia de caracteres|  
|PRIMARY_KEY|Boolean|  
|EXCLUSIVO|Boolean|  
|CLUSTERED|Boolean|  
|TIPO DE|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|Cadeia de caracteres|  
|COLUMN_GUID|GUID|  
|COLUMN_PROPID|Int64|  
|AGRUPAMENTO|Int16|  
|CARDINALIDADE|Decimal|  
|PÁGINAS|Int32|  
|FILTER_CONDITION|Cadeia de caracteres|  
|INTEGRADO|Boolean|  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
