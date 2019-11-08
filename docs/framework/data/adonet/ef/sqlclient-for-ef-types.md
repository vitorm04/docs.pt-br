---
title: SqlClient para a entidade FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: d132583bba2520d37693be6c4b085cfa514003e0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737852"
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
|`decimal`|N/D|`Edm.Decimal`|Preciso<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 38<br /><br /> -Padrão: 18<br /><br /> -Constante: false<br /><br /> Escalonáve<br /><br /> -Mínimo: 0<br /><br /> -Máximo: 38<br /><br /> -Padrão: 0<br /><br /> -Constante: false|  
|`numeric`|N/D|`Edm.Decimal`|Preciso<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 38<br /><br /> -Padrão: 18<br /><br /> -Constante: false<br /><br /> Escalonáve<br /><br /> -Mínimo: 0<br /><br /> -Máximo: 38<br /><br /> -Padrão: 0<br /><br /> -Constante: false|  
|`smallmoney`|N/D|`Edm.Decimal`|Preciso<br /><br /> -Padrão: 10<br /><br /> -Constante: true<br /><br /> Escalonáve<br /><br /> -Padrão: 4<br /><br /> -Constante: true|  
|`money`|N/D|`Edm.Decimal`|Preciso<br /><br /> -Padrão: 19<br /><br /> -Constante: true<br /><br /> Escalonáve<br /><br /> -Padrão: 4<br /><br /> -Constante: true|  
|`binary`|N/D|`Edm.Binary`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: false<br /><br /> Cadeia<br /><br /> -Padrão: true<br /><br /> -Constante: true|  
|`varbinary`|N/D|`Edm.Binary`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: false<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`varbinary(max)`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2000.|N/D|`Edm.Binary`|Determinado<br /><br /> -Padrão: 214748364780<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`image`|N/D|`Edm.Binary`|Determinado<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`timestamp`|N/D|`Edm.Binary`|Determinado<br /><br /> -Padrão: 8<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: true<br /><br /> -Constante: true|  
|`rowversion`|N/D|`Edm.Binary`|Determinado<br /><br /> -Padrão: 8<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: true<br /><br /> -Constante: true|  
|`smalldatetime`|N/D|`Edm.DateTime`|Preciso<br /><br /> -Padrão: 0<br /><br /> -Constante: true|  
|`datetime`|N/D|`Edm.DateTime`|Preciso<br /><br /> -Padrão: 3<br /><br /> -Constante: true|  
|`date`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Preciso<br /><br /> -Padrão: 0<br /><br /> -Constante: false|  
|`time`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.Time`|Preciso<br /><br /> -Padrão: 7<br /><br /> -Constante: false|  
|`datetime2`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Preciso<br /><br /> -Padrão: 7<br /><br /> -Constante: false|  
|`datetimeoffset`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTimeOffset`|Preciso<br /><br /> -Padrão: 7<br /><br /> -Constante: false|  
|`nvarchar`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2000.|N/D|`Edm.String`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: false<br /><br /> Unicode:<br /><br /> -Padrão: true<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`varchar`<br /><br /> Observação: esse tipo não tem suporte no SQL Server 2000.|N/D|`Edm.String`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: false<br /><br /> Unicode:<br /><br /> -Padrão: false<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`char`|N/D|`Edm.String`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: false<br /><br /> Unicode:<br /><br /> -Padrão: false<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: true<br /><br /> -Constante: true|  
|`nchar`|N/D|`Edm.String`|Determinado<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: false<br /><br /> Unicode:<br /><br /> -Padrão: true<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: true<br /><br /> -Constante: true|  
|`varchar`(`max`)|N/D|`Edm.String`|Determinado<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: true<br /><br /> Unicode:<br /><br /> -Padrão: false<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`nvarchar`(`max`)|N/D|`Edm.String`|Determinado<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: true<br /><br /> Unicode:<br /><br /> -Padrão: true<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`ntext`|Igual comparável: falso<br /><br /> Ordem comparável: falso|`Edm.String`|Determinado<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: true<br /><br /> Unicode:<br /><br /> -Padrão: false<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`text`|Igual comparável: falso<br /><br /> Ordem comparável: falso|`Edm.String`|Determinado<br /><br /> -Padrão: 2147483647<br /><br /> -Constante: true<br /><br /> Unicode:<br /><br /> -Padrão: false<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
|`Unique`<br /><br /> `identifier`|Igual comparável: verdadeiro<br /><br /> Ordem comparável: true|`Edm.Guid`|N/D|  
|`xml`|Igual comparável: falso<br /><br /> Ordem comparável: falso|`Edm.String`|Determinado<br /><br /> -Padrão: 1073741823<br /><br /> -Constante: true<br /><br /> Unicode:<br /><br /> -Padrão: true<br /><br /> -Constante: true<br /><br /> Cadeia<br /><br /> -Padrão: false<br /><br /> -Constante: true|  
  
## <a name="see-also"></a>Consulte também

- [CSDL, SSDL, and MSL Specifications](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) (Especificações CSDL, SSDL e MSL)
