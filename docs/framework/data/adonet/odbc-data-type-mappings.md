---
title: Mapeamentos de tipo de dados ODBC
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: 6611ca35ab5e5b44fa9adacfe25593bb4a5b9c44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783517"
---
# <a name="odbc-data-type-mappings"></a>Mapeamentos de tipo de dados ODBC
A tabela a seguir mostra o tipo de .NET Framework inferido para tipos de dados do .NET Framework Provedor de Dados para<xref:System.Data.Odbc>ODBC (). Os métodos de acessadores <xref:System.Data.Odbc.OdbcDataReader> tipados para o também são listados.  
  
|Tipo de ODBC|Tipo do .NET Framework|Acessador .NET Framework tipado|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte[]|GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|Cadeia de Caracteres<br /><br /> Char[]|GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Decimal|GetDecimal()|  
|SQL_DOUBLE|Duplo|GetDouble()|  
|SQL_GUID|Guid|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|Cadeia de Caracteres<br /><br /> Char[]|GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte[]|GetBytes()|  
|SQL_NUMERIC|Decimal|GetDecimal()|  
|SQL_REAL|Simples|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DateTime|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DateTime|GetDateTime()|  
|SQL_VARBINARY|Byte[]|GetBytes()|  
|SQL_WCHAR|Cadeia de Caracteres<br /><br /> Char[]|GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|Cadeia de Caracteres<br /><br /> Char[]|GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|Cadeia de Caracteres<br /><br /> Char[]|GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Consulte também

- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
