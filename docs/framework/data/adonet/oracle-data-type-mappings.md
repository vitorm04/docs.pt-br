---
title: Mapeamentos de tipo de dados Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783427"
---
# <a name="oracle-data-type-mappings"></a>Mapeamentos de tipo de dados Oracle
A tabela a seguir lista os tipos de dados Oracle e seus mapeamentos para o <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Tipo de dados do Oracle|Tipo de dados do .NET Framework retornado por OracleDataReader.GetValue|Tipo de dados OracleClient retornado por OracleDataReader.GetOracleValue|Comentários|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o tipo de dados **Number** e é projetado para que <xref:System.Data.OracleClient.OracleDataReader> o retorne um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor de ponto flutuante. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTEGER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o tipo de dados **Number (38)** e é projetado para que <xref:System.Data.OracleClient.OracleDataReader> o retorne um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVALO DIA A SEGUNDO**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleLob>||  
|**AUTOMÁTICA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**NVARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**CURSOR DE REFERÊNCIA**|||O tipo de dados **cursor de referência** do Oracle não é <xref:System.Data.OracleClient.OracleDataReader> suportado pelo objeto.|  
|**ROWID**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE DATA/HORA COM FUSO HORÁRIO LOCAL**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**CARIMBO DE DATA/HORA COM FUSO HORÁRIO**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**INTEIRO SEM SINAL**|**Número**|<xref:System.Data.OracleClient.OracleNumber>|Esse tipo de dados é um alias para o tipo de dados **Number (38)** e é projetado para que <xref:System.Data.OracleClient.OracleDataReader> o retorne um **System. decimal** ou <xref:System.Data.OracleClient.OracleNumber> em vez de um valor inteiro sem sinal. O uso do tipo de dados do .NET Framework pode causar um estouro.|  
|**VARCHAR2**|**Cadeia de caracteres**|<xref:System.Data.OracleClient.OracleString>||  
  
 A tabela a seguir lista os tipos de dados do Oracle e os tipos de dados .NET Framework (**System. Data. DbType** e <xref:System.Data.OracleClient.OracleType>) a serem usados ao associá-los como parâmetros.  
  
|Tipo de dados do Oracle|Enumeração DbType a ser associada como um parâmetro|Enumeração OracleType a ser associada como um parâmetro|Comentários|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|O Oracle só permite a associação de um **bArquivo** como um parâmetro **bArquivo** . O .NET Provedor de Dados para Oracle não construirá um automaticamente para você se você tentar associar um valor não**bArquivo** , como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|O Oracle só permite a associação de um **blob** como um parâmetro de **blob** . O .NET Provedor de Dados para Oracle não construirá um automaticamente para você se você tentar associar um valor não-**blob** , como **byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|O Oracle só permite a vinculação de um **CLOB** como um parâmetro **CLOB** . O .NET Provedor de Dados para Oracle não construirá um automaticamente para você se você tentar associar um valor não**CLOB** , como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Único, duplo, decimal**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>determina o **System. Data. DbType** e <xref:System.Data.OracleClient.OracleType>o.|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, número**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>determina o **System. Data. DbType** e <xref:System.Data.OracleClient.OracleType>o.|  
|**INTERVALO DE ANO PARA MÊS**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**INTERVALO DIA A SEGUNDO**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|O Oracle só permite a vinculação de um **NClob** como um parâmetro **NClob** . O .NET Provedor de Dados para Oracle não construirá um automaticamente para você se você tentar associar um valor não**NClob** , como **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**AUTOMÁTICA**|**VarNumeric**|**Número**||  
|**NVARCHAR2**|**Cadeia de caracteres**|**NVarChar**||  
|**RAW**|**Binary**|**Recebem**||  
|**CURSOR DE REFERÊNCIA**||**Posição**|Para obter mais informações, consulte [cursores de referência do Oracle](oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**ROWID**||  
|**TIMESTAMP**|**DateTime**|**Carimbo de data/hora**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE DATA/HORA COM FUSO HORÁRIO LOCAL**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**CARIMBO DE DATA/HORA COM FUSO HORÁRIO**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> só está disponível com o uso do software cliente e servidor Oracle 9i.|  
|**INTEIRO SEM SINAL**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, UInt32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>determina o **System. Data. DbType** e <xref:System.Data.OracleClient.OracleType>o.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 Os **valores de** **parameterdirectity** InputOutput, **output**e **ReturnValue** usados pela Propriedadedoobjetosão.NETFrameworktiposdedados,amenosqueovalordeentradasejaumtipodedadosOracle(para<xref:System.Data.OracleClient.OracleParameter> <xref:System.Data.OracleClient.OracleParameter.Value%2A> exemplo, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Isso não se aplica aos tipos de dados **cursor de referência**, **bArquivo**ou **LOB** .  
  
## <a name="see-also"></a>Consulte também

- [Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
