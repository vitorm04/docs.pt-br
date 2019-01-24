---
title: SqlClient para Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: b121020c8779cfb3959425b1019eaf085b97d6cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505180"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient para Entity FrameworkTypes
O provedor de dados. NET Framework para o arquivo de manifesto do provedor SQL Server (SqlClient) inclui a lista de tipos primitivos de provedor, de facetas para cada tipo, de mapeamento entre os tipos primitivos e modelo conceitual de armazenamento, e regras da promoção e de conversão entre os tipos primitivos modelo conceitual e do armazenamento.  
  
 A tabela a seguir descreve os tipos do SQL Server 2008, [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], e [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] bancos de dados e como esses tipos são mapeados para conceitual tipos de modelo. Alguns novos tipos foram introduzidos em versões posteriores do SQL Server não são suportados nas versões anteriores do SQL Server. Esses tipos são observados na tabela abaixo.  
  
|Tipo de provedor<br /><br /> name|Tipo de provedor<br /><br /> atributos|`EDMSimpleType`<br /><br /> name|Facetas|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/D|`Edm.Boolean`|N/D|  
|`tinyint`|N/D|`Edm.Byte`|N/D|  
|`smallint`|N/D|`Edm.Int16`|N/D|  
|`int`|N/D|`Edm.Int32`|N/D|  
|`bigint`|N/D|`Edm.Int64`|N/D|  
|`float`|N/D|`Edm.Double`|N/D|  
|`real`|N/D|`Edm.Double`|N/D|  
|`decimal`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 38<br /><br /> -Padrão: 18<br /><br /> -Constante: False<br /><br /> Escala:<br /><br /> -Mínimo: 0<br /><br /> -Máximo: 38<br /><br /> -Padrão: 0<br /><br /> -Constante: False|  
|`numeric`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 38<br /><br /> -Padrão: 18<br /><br /> -Constante: False<br /><br /> Escala:<br /><br /> -Mínimo: 0<br /><br /> -Máximo: 38<br /><br /> -Padrão: 0<br /><br /> -Constante: False|  
|`smallmoney`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Padrão: 10<br /><br /> -Constante: verdadeiro<br /><br /> Escala:<br /><br /> -Padrão: 4<br /><br /> -Constante: verdadeiro|  
|`money`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Padrão: 19<br /><br /> -Constante: verdadeiro<br /><br /> Escala:<br /><br /> -Padrão: 4<br /><br /> -Constante: verdadeiro|  
|`binary`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> FixedLength:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro|  
|`varbinary`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`varbinary(max)`<br /><br /> Observação: Não há suporte para esse tipo no [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 214748364780<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`image`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`timestamp`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 8<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro|  
|`rowversion`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 8<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro|  
|`smalldatetime`|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 0<br /><br /> -Constante: verdadeiro|  
|`datetime`|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 3<br /><br /> -Constante: verdadeiro|  
|`date`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 0<br /><br /> -Constante: False|  
|`time`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.Time`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`datetime2`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`datetimeoffset`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTimeOffset`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`nvarchar`<br /><br /> Observação: Não há suporte para esse tipo no [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`varchar`<br /><br /> Observação: Não há suporte para esse tipo no [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`char`|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro|  
|`nchar`|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro|  
|`varchar`(`max`)|N/D|`Edm.String`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: verdadeiro<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`nvarchar`(`max`)|N/D|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: verdadeiro<br /><br /> Unicode:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`ntext`|Igual comparáveis: False<br /><br /> Ordem comparáveis: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: verdadeiro<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`text`|Igual comparáveis: False<br /><br /> Ordem comparáveis: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: verdadeiro<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
|`Unique`<br /><br /> `identifier`|Igual comparáveis: verdadeiro<br /><br /> Ordem comparáveis: verdadeiro|`Edm.Guid`|N/D|  
|`xml`|Igual comparáveis: False<br /><br /> Ordem comparáveis: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: verdadeiro<br /><br /> Unicode:<br /><br /> -Padrão: verdadeiro<br /><br /> -Constante: verdadeiro<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constante: verdadeiro|  
  
## <a name="see-also"></a>Consulte também
- [CSDL, SSDL, and MSL Specifications](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)
