---
title: Mapeamentos de tipo de dados Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: c1fb3a6838e6a1b242255d4035c10ab0ec07d536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104566"
---
# <a name="oracle-data-type-mappings"></a>Mapeamentos de tipo de dados Oracle
A tabela a seguir lista os tipos de dados Oracle e seus mapeamentos para o <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Tipo de dados Oracle|Tipo de dados do .NET Framework retornado por OracleDataReader.GetValue|Tipo de dados OracleClient retornado por OracleDataReader.GetOracleValue|Comentários|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **número** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor de ponto flutuante. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**NVARCHAR2**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||A Oracle **REF CURSOR** tipo de dados não tem suporte a <xref:System.Data.OracleClient.OracleDataReader> objeto.|  
|**ROWID**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**Número**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro sem sinal. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**VARCHAR2**|**Cadeia de Caracteres**|<xref:System.Data.OracleClient.OracleString>||  
  
 A tabela a seguir lista os tipos de dados Oracle e os tipos de dados do .NET Framework (**2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>) a ser usado ao associá-los como parâmetros.  
  
|Tipo de dados Oracle|Enumeração DbType a ser associada como um parâmetro|Enumeração OracleType a ser associada como um parâmetro|Comentários|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle só permite associar um **BFILE** como um **BFILE** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**BFILE** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle só permite associar um **BLOB** como um **BLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**BLOB** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle só permite associar um **CLOB** como um **CLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**CLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> disponível somente quando está usando ambos os software da Oracle 9i cliente e servidor.|  
|**INTERVAL DAY TO SECOND**|**Objeto**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> disponível somente quando está usando ambos os software da Oracle 9i cliente e servidor.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binário**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle só permite associar um **NCLOB** como um **NCLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**NCLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**NUMBER**|**VarNumeric**|**Número**||  
|**NVARCHAR2**|**Cadeia de Caracteres**|**NVarChar**||  
|**RAW**|**Binário**|**Raw**||  
|**REF CURSOR**||**Cursor**|Para obter mais informações, consulte [REF CURSORs do Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**Timestamp**|<xref:System.Data.OracleClient.OracleType> disponível somente quando está usando ambos os software da Oracle 9i cliente e servidor.|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> disponível somente quando está usando ambos os software da Oracle 9i cliente e servidor.|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> disponível somente quando está usando ambos os software da Oracle 9i cliente e servidor.|  
|**UNSIGNED INTEGER**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 O **InputOutput**, **saída**, e **ReturnValue** **ParameterDirection** valores usados pelo <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriedade do <xref:System.Data.OracleClient.OracleParameter> objeto são tipos de dados do .NET Framework, a menos que o valor de entrada é um tipo de dados Oracle (por exemplo, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Isso não se aplica ao **REF CURSOR**, **BFILE**, ou **LOB** tipos de dados.  
  
## <a name="see-also"></a>Consulte também

- [Oracle e ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
