---
title: Mapeamentos de tipo de dados ODBC
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 82c4a84f1aee5872a899d8d42a06d22abc10b603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="odbc-data-type-mappings"></a>Mapeamentos de tipo de dados ODBC
A tabela a seguir mostra o deduzido [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo para tipos de dados do .NET Framework Data Provider para ODBC (<xref:System.Data.Odbc>). Os métodos de acessador tipado para o <xref:System.Data.Odbc.OdbcDataReader> também são listados.  
  
|Tipo de ODBC|Tipo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]acessador tipado|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte[]|GetBytes|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|Cadeia de caracteres<br /><br /> Char[]|GetString)<br /><br /> GetChars|  
|SQL_DECIMAL|Decimal|GetDecimal()|  
|SQL_DOUBLE|Duplo|GetDouble()|  
|SQL_GUID|GUID|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|Cadeia de caracteres<br /><br /> Char[]|GetString)<br /><br /> GetChars|  
|SQL_LONGVARBINARY|Byte[]|GetBytes|  
|SQL_NUMERIC|Decimal|GetDecimal()|  
|SQL_REAL|Simples|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Byte[]|GetBytes|  
|SQL_WCHAR|Cadeia de caracteres<br /><br /> Char[]|GetString)<br /><br /> GetChars|  
|SQL_WLONGVARCHAR|Cadeia de caracteres<br /><br /> Char[]|GetString)<br /><br /> GetChars|  
|SQL_WVARCHAR|Cadeia de caracteres<br /><br /> Char[]|GetString)<br /><br /> GetChars|  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
