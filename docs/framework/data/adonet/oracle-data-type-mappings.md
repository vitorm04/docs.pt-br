---
title: Mappings1 de tipo de dados Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 9057a19abb1abc22924b5542f06e21a57a36ed94
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856329"
---
# <a name="oracle-data-type-mappings"></a>Mapeamentos de tipo de dados Oracle
A tabela a seguir lista os tipos de dados Oracle e seus mapeamentos para o <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Tipo de dados Oracle|Tipo de dados do .NET Framework retornado por OracleDataReader.GetValue|Tipo de dados OracleClient retornado por OracleDataReader.GetOracleValue|Comentários|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **número** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor de ponto flutuante. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVALO-DIA PARA SEGUNDO**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**NÚMERO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**NVARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||A Oracle **REF CURSOR** tipo de dados não tem suporte a <xref:System.Data.OracleClient.OracleDataReader> objeto.|  
|**ROWID**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE HORA COM FUSO HORÁRIO LOCAL**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE HORA COM FUSO HORÁRIO**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**INTEIRO SEM SINAL**|**Número**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro sem sinal. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**VARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
  
 A tabela a seguir lista os tipos de dados Oracle e os tipos de dados do .NET Framework (**2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>) a ser usado ao associá-los como parâmetros.  
  
|Tipo de dados Oracle|Enumeração DbType a ser associada como um parâmetro|Enumeração OracleType a ser associada como um parâmetro|Comentários|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle só permite associar um **BFILE** como um **BFILE** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**BFILE** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle só permite associar um **BLOB** como um **BLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**BLOB** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle só permite associar um **CLOB** como um **CLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**CLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, Double, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**INTERVALO-DIA PARA SEGUNDO**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**nChar**||  
|**NCLOB**||**NClob**|Oracle só permite associar um **NCLOB** como um **NCLOB** parâmetro. O provedor de dados .NET para Oracle não construirá um automaticamente para você se você tentar associar um não -**NCLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**NÚMERO**|**VarNumeric**|**Número**||  
|**NVARCHAR2**|**Cadeia de caracteres**|**NVarChar**||  
|**RAW**|**Binary**|**bruto**||  
|**REF CURSOR**||**cursor**|Para obter mais informações, consulte [REF CURSORs do Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**RowId**||  
|**TIMESTAMP**|**DateTime**|**Carimbo de data/hora**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE HORA COM FUSO HORÁRIO LOCAL**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE HORA COM FUSO HORÁRIO**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**INTEIRO SEM SINAL**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **2&gt;System.Data.DbType&lt;2** e <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 O **InputOutput**, **saída**, e **ReturnValue** **ParameterDirection** valores usados pelo <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriedade do <xref:System.Data.OracleClient.OracleParameter> objeto são tipos de dados do .NET Framework, a menos que o valor de entrada é um tipo de dados Oracle (por exemplo, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Isso não se aplica ao **REF CURSOR**, **BFILE**, ou **LOB** tipos de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
