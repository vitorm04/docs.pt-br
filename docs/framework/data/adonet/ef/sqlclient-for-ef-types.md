---
title: SqlClient para a entidade FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248374"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient para a entidade FrameworkTypes
O provedor de dados. NET Framework para o arquivo de manifesto do provedor SQL Server (SqlClient) inclui a lista de tipos primitivos de provedor, de facetas para cada tipo, de mapeamento entre os tipos primitivos e modelo conceitual de armazenamento, e regras da promoção e de conversão entre os tipos primitivos modelo conceitual e do armazenamento.  
  
 A tabela a seguir descreve os tipos de SQL Server 2008, SQL Server 2005 e SQL Server bancos de dados do 2000 e como esses tipos são mapeados para tipos de modelo conceitual. Alguns novos tipos foram introduzidos em versões posteriores do SQL Server não são suportados nas versões anteriores do SQL Server. Esses tipos são observados na tabela abaixo.  
  
|Tipo de provedor<br /><br /> name|Tipo de provedor<br /><br /> atributos|`EDMSimpleType`<br /><br /> name|Facetas|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/D|`Edm.Boolean`|N/D|  
|`tinyint`|N/D|`Edm.Byte`|N/D|  
|`smallint`|N/D|`Edm.Int16`|N/D|  
|`int`|N/D|`Edm.Int32`|N/D|  
|`bigint`|N/D|`Edm.Int64`|N/D|  
|`float`|N/D|`Edm.Double`|N/D|  
|`real`|N/D|`Edm.Double`|N/D|  
|`decimal`|N/D|`Edm.Decimal`|Preciso<br /><br /> Máximo 1<br /><br /> Maior 38<br /><br /> Os 18<br /><br /> Amortiza False<br /><br /> Escalonáve<br /><br /> Máximo 0<br /><br /> Maior 38<br /><br /> Os 0<br /><br /> Amortiza False|  
|`numeric`|N/D|`Edm.Decimal`|Preciso<br /><br /> Máximo 1<br /><br /> Maior 38<br /><br /> Os 18<br /><br /> Amortiza False<br /><br /> Escalonáve<br /><br /> Máximo 0<br /><br /> Maior 38<br /><br /> Os 0<br /><br /> Amortiza False|  
|`smallmoney`|N/D|`Edm.Decimal`|Preciso<br /><br /> Os 10<br /><br /> Amortiza verdadeiro<br /><br /> Escalonáve<br /><br /> Os 4<br /><br /> Amortiza verdadeiro|  
|`money`|N/D|`Edm.Decimal`|Preciso<br /><br /> Os 19<br /><br /> Amortiza verdadeiro<br /><br /> Escalonáve<br /><br /> Os 4<br /><br /> Amortiza verdadeiro|  
|`binary`|N/D|`Edm.Binary`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 8000<br /><br /> Os 8000<br /><br /> Amortiza False<br /><br /> FixedLength:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro|  
|`varbinary`|N/D|`Edm.Binary`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 8000<br /><br /> Os 8000<br /><br /> Amortiza False<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`varbinary(max)`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2000.|N/D|`Edm.Binary`|Determinado<br /><br /> Os 214748364780<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`image`|N/D|`Edm.Binary`|Determinado<br /><br /> Os 2147483647<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`timestamp`|N/D|`Edm.Binary`|Determinado<br /><br /> Os 8<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro|  
|`rowversion`|N/D|`Edm.Binary`|Determinado<br /><br /> Os 8<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro|  
|`smalldatetime`|N/D|`Edm.DateTime`|Preciso<br /><br /> Os 0<br /><br /> Amortiza verdadeiro|  
|`datetime`|N/D|`Edm.DateTime`|Preciso<br /><br /> Os 3<br /><br /> Amortiza verdadeiro|  
|`date`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Preciso<br /><br /> Os 0<br /><br /> Amortiza False|  
|`time`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.Time`|Preciso<br /><br /> Os 7<br /><br /> Amortiza False|  
|`datetime2`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Preciso<br /><br /> Os 7<br /><br /> Amortiza False|  
|`datetimeoffset`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTimeOffset`|Preciso<br /><br /> Os 7<br /><br /> Amortiza False|  
|`nvarchar`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2000.|N/D|`Edm.String`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 4000<br /><br /> Os 4000<br /><br /> Amortiza False<br /><br /> Unicode:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`varchar`<br /><br /> Observação: Não há suporte para esse tipo no SQL Server 2000.|N/D|`Edm.String`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 8000<br /><br /> Os 8000<br /><br /> Amortiza False<br /><br /> Unicode:<br /><br /> Os False<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`char`|N/D|`Edm.String`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 8000<br /><br /> Os 8000<br /><br /> Amortiza False<br /><br /> Unicode:<br /><br /> Os False<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro|  
|`nchar`|N/D|`Edm.String`|Determinado<br /><br /> Máximo 1<br /><br /> Maior 4000<br /><br /> Os 4000<br /><br /> Amortiza False<br /><br /> Unicode:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro|  
|`varchar`(`max`)|N/D|`Edm.String`|Determinado<br /><br /> Os 2147483647<br /><br /> Amortiza verdadeiro<br /><br /> Unicode:<br /><br /> Os False<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`nvarchar`(`max`)|N/D|`Edm.String`|Determinado<br /><br /> Os 1073741823<br /><br /> Amortiza verdadeiro<br /><br /> Unicode:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`ntext`|Igual comparável: False<br /><br /> Ordem comparável: False|`Edm.String`|Determinado<br /><br /> Os 1073741823<br /><br /> Amortiza verdadeiro<br /><br /> Unicode:<br /><br /> Os False<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`text`|Igual comparável: False<br /><br /> Ordem comparável: False|`Edm.String`|Determinado<br /><br /> Os 2147483647<br /><br /> Amortiza verdadeiro<br /><br /> Unicode:<br /><br /> Os False<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
|`Unique`<br /><br /> `identifier`|Igual comparável: verdadeiro<br /><br /> Ordem comparável: verdadeiro|`Edm.Guid`|N/D|  
|`xml`|Igual comparável: False<br /><br /> Ordem comparável: False|`Edm.String`|Determinado<br /><br /> Os 1073741823<br /><br /> Amortiza verdadeiro<br /><br /> Unicode:<br /><br /> Os verdadeiro<br /><br /> Amortiza verdadeiro<br /><br /> FixedLength:<br /><br /> Os False<br /><br /> Amortiza verdadeiro|  
  
## <a name="see-also"></a>Consulte também

- [CSDL, SSDL, and MSL Specifications](./language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)
