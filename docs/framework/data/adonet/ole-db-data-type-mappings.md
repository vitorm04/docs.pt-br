---
title: Mapeamentos de tipo de dados do OLE DB
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 407f194a8530f9b9e4241a6bdb4d26a4b891aa46
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="ole-db-data-type-mappings"></a>Mapeamentos de tipo de dados do OLE DB
A tabela a seguir mostra o deduzido [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo para tipos de dados do .NET Framework Data Provider para ADO e OLE DB (<xref:System.Data.OleDb>). Os métodos de acessador tipado para o <xref:System.Data.OleDb.OleDbDataReader> também são listados.  
  
|Tipo de ADO|Tipo de OLE DB|Tipo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] acessador tipado|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|Cadeia de Caracteres|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Suporte por meio de `DataReader`. Consulte [recuperando dados usando um DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|Cadeia de Caracteres|GetString()|  
|adCurrency|DBTYPE_CY|Decimal|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Decimal|GetDecimal()|  
|adDouble|DBTYPE_R8|Duplo|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Objeto|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Objeto|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Decimal|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Objeto|GetValue()|  
|adSingle|DBTYPE_R4|Simples|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Objeto|GetValue()|  
|adWChar|DBTYPE_WSTR|Cadeia de Caracteres|GetString()|  
|adUserDefined|DBTYPE_UDT|sem suporte||  
|adVarNumeric|DBTYPE_VARNUMERIC|sem suporte||  
  
 \* Para os tipos de OLE DB `DBTYPE_IUNKNOWN` e `DBTYPE_IDISPATCH`, a referência de objeto é uma representação de marshaling do ponteiro.  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
