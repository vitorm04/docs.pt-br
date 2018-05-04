---
title: Mappings1 de tipo de dados Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 2b5a3a90c704dd6edf32e6fb77b551e6fc0f78ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
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
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **número** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor de ponto flutuante. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**DIA DE INTERVALO PARA O SEGUNDO**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**NÚMERO**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**NVARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||O Oracle **REF CURSOR** não há suporte para o tipo de dados o <xref:System.Data.OracleClient.OracleDataReader> objeto.|  
|**ROWID**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE HORA COM O FUSO HORÁRIO LOCAL**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE HORA COM O FUSO HORÁRIO**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**INTEIRO NÃO ASSINADO**|**Número**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o **NUMBER(38)** tipo de dados e foi projetado para que o <xref:System.Data.OracleClient.OracleDataReader> retorna um **decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro não assinado. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**VARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
  
 A tabela a seguir lista os tipos de dados Oracle e tipos de dados do .NET Framework (**System.Data.DbType** e <xref:System.Data.OracleClient.OracleType>) a ser usado ao associá-los como parâmetros.  
  
|Tipo de dados Oracle|Enumeração DbType a ser associada como um parâmetro|Enumeração OracleType a ser associada como um parâmetro|Comentários|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle permite somente a associação de um **BFILE** como um **BFILE** parâmetro. O provedor de dados .NET para Oracle não automaticamente constrói uma para você se você tentar associar não**BFILE** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle permite somente a associação de um **BLOB** como um **BLOB** parâmetro. O provedor de dados .NET para Oracle não automaticamente constrói uma para você se você tentar associar não**BLOB** valor, como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle permite somente a associação de um **CLOB** como um **CLOB** parâmetro. O provedor de dados .NET para Oracle não automaticamente constrói uma para você se você tentar associar não**CLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single, Double, Decimal**|**Flutuar, clique duas vezes, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **System.Data.DBType** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **System.Data.DBType** e <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**DIA DE INTERVALO PARA O SEGUNDO**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle permite somente a associação de um **NCLOB** como um **NCLOB** parâmetro. O provedor de dados .NET para Oracle não automaticamente constrói uma para você se você tentar associar não**NCLOB** valor, como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**NÚMERO**|**VarNumeric**|**Número**||  
|**NVARCHAR2**|**Cadeia de caracteres**|**NVarChar**||  
|**RAW**|**Binary**|**Bruto**||  
|**REF CURSOR**||**Cursor**|Para obter mais informações, consulte [REF CURSORs do Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**RowId**||  
|**TIMESTAMP**|**DateTime**|**Carimbo de data/hora**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE HORA COM O FUSO HORÁRIO LOCAL**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE HORA COM O FUSO HORÁRIO**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**INTEIRO NÃO ASSINADO**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Determina o **System.Data.DBType** e <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 O **InputOutput**, **saída**, e **ReturnValue** **ParameterDirection** valores usados pelo <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriedade o <xref:System.Data.OracleClient.OracleParameter> objeto são tipos de dados do .NET Framework, a menos que o valor de entrada é um tipo de dados Oracle (por exemplo, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Isso não se aplica a **REF CURSOR**, **BFILE**, ou **LOB** tipos de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
