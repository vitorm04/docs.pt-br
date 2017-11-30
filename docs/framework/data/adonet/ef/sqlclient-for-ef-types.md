---
title: SqlClient para Entity FrameworkTypes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c8a3a3e794941c2713af0e5b098bd7f8d783eb4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient para Entity FrameworkTypes
O provedor de dados. NET Framework para o arquivo de manifesto do provedor SQL Server (SqlClient) inclui a lista de tipos primitivos de provedor, de facetas para cada tipo, de mapeamento entre os tipos primitivos e modelo conceitual de armazenamento, e regras da promoção e de conversão entre os tipos primitivos modelo conceitual e do armazenamento.  
  
 A tabela a seguir descreve os tipos do SQL Server 2008, [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], e [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] tipos de modelos de bancos de dados e como esses tipos são mapeados para conceitual. Alguns novos tipos foram introduzidos em versões posteriores do SQL Server não são suportados nas versões anteriores do SQL Server. Esses tipos são observados na tabela abaixo.  
  
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
|`smallmoney`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Padrão: 10<br /><br /> -Constantes: True<br /><br /> Escala:<br /><br /> -Padrão: 4<br /><br /> -Constantes: True|  
|`money`|N/D|`Edm.Decimal`|Precisão:<br /><br /> -Padrão: 19<br /><br /> -Constantes: True<br /><br /> Escala:<br /><br /> -Padrão: 4<br /><br /> -Constantes: True|  
|`binary`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> FixedLength:<br /><br /> -Padrão: True<br /><br /> -Constantes: True|  
|`varbinary`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`varbinary(max)`<br /><br /> Observação: Esse tipo não é suportado em [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 214748364780<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`image`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`timestamp`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 8<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: True<br /><br /> -Constantes: True|  
|`rowversion`|N/D|`Edm.Binary`|MaxLength:<br /><br /> -Padrão: 8<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: True<br /><br /> -Constantes: True|  
|`smalldatetime`|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 0<br /><br /> -Constantes: True|  
|`datetime`|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 3<br /><br /> -Constantes: True|  
|`date`<br /><br /> Observação: Esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 0<br /><br /> -Constante: False|  
|`time`<br /><br /> Observação: Esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.Time`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`datetime2`<br /><br /> Observação: Esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTime`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`datetimeoffset`<br /><br /> Observação: Esse tipo não tem suporte no SQL Server 2005 e SQL Server 2000.|N/D|`Edm.DateTimeOffset`|Precisão:<br /><br /> -Padrão: 7<br /><br /> -Constante: False|  
|`nvarchar`<br /><br /> Observação: Esse tipo não é suportado em [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: True<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`varchar`<br /><br /> Observação: Esse tipo não é suportado em [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`char`|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 8000<br /><br /> -Padrão: 8000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: True<br /><br /> -Constantes: True|  
|`nchar`|N/D|`Edm.String`|MaxLength:<br /><br /> -Mínimo: 1<br /><br /> -Máximo: 4000<br /><br /> -Padrão: 4000<br /><br /> -Constante: False<br /><br /> Unicode:<br /><br /> -Padrão: True<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: True<br /><br /> -Constantes: True|  
|`varchar`(`max`)|N/D|`Edm.String`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constantes: True<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`nvarchar`(`max`)|N/D|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constantes: True<br /><br /> Unicode:<br /><br /> -Padrão: True<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`ntext`|Igual comparável: False<br /><br /> Comparável por ordenamento: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constantes: True<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`text`|Igual comparável: False<br /><br /> Comparável por ordenamento: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 2147483647<br /><br /> -Constantes: True<br /><br /> Unicode:<br /><br /> -Padrão: False<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
|`Unique`<br /><br /> `identifier`|Igual comparável: True<br /><br /> Comparável por ordenamento: True|`Edm.Guid`|N/D|  
|`xml`|Igual comparável: False<br /><br /> Comparável por ordenamento: False|`Edm.String`|MaxLength:<br /><br /> -Padrão: 1073741823<br /><br /> -Constantes: True<br /><br /> Unicode:<br /><br /> -Padrão: True<br /><br /> -Constantes: True<br /><br /> FixedLength:<br /><br /> -Padrão: False<br /><br /> -Constantes: True|  
  
## <a name="see-also"></a>Consulte também  
 [CSDL, SSDL, and MSL Specifications](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)
