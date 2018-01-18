---
title: 'Modelo de Dados de Entidade: Tipos de dados primitivos'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f25c94582ade23b645942a13829a5aa559e3e4f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-primitive-data-types"></a>Modelo de Dados de Entidade: Tipos de dados primitivos
O modelo de dados de entidade (EDM) oferece suporte a um conjunto de tipos de dados primitivo abstrato (como cadeia de caracteres, Boolean, Int32 e assim por diante) que são usadas para definir [propriedades](../../../../docs/framework/data/adonet/property.md) em um modelo conceitual. Esses tipos de dados primitivos são proxies para os tipos de dados primitivos reais que são suportados no armazenamento ou no ambiente de hospedagem, como um base de dados SQL Server ou Common Language Runtime (CLR). EDM não define a semântica das operações ou das conversões sobre tipos de dados primitivos; essa semântica é definida pelo armazenamento ou pelo ambiente de hospedagem. Normalmente, os tipos de dados primitivos em EDM são mapeados para os tipos de dados primitivos no armazenamento ou no ambiente de hospedagem. Para obter informações sobre como o Entity Framework mapeia tipos primitivos de EDM para tipos de dados do SQL Server, consulte [SqlClient para Entity FrameworkTypes](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  EDM não suporta coleções de tipos de dados primitivos.  
  
 Para obter informações sobre os tipos de dados estruturados no EDM, consulte [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) e [tipo complexo](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Tipos de dados primitivos suportados em Modelo de Dados de Entidade  
 A tabela abaixo lista os tipos de dados primitivos suportados por EDM. A tabela também lista o [facetas](../../../../docs/framework/data/adonet/facet.md) que podem ser aplicadas a cada tipo de dados primitivo.  
  
|Tipo de dados primitivo|Descrição|Facetas aplicáveis|  
|-------------------------|-----------------|-----------------------|  
|Binário|Contém dados binários.|MaxLength, FixedLength, anulável, opção|  
|Boolean|Contém o valor `true` ou `false`.|Anulável, opção|  
|Byte|Contém um valor inteiro de 8 bits sem sinal.|Precisão, anulável, opção|  
|DateTime|Representa uma data e hora.|Precisão, anulável, opção|  
|DateTimeOffset|Contém uma data e hora como um deslocamento em minutos GMT.|Precisão, anulável, opção|  
|Decimal|Contém um valor numérico com precisão e escala fixa.|Precisão, anulável, opção|  
|Duplo|Contém um número de ponto flutuante com precisão de 15 dígitos.|Precisão, anulável, opção|  
|Float|Contém um número de ponto flutuante com precisão de sete dígitos.|Precisão, anulável, opção|  
|Guid|Contém um identificador exclusivo de 16 bytes.|Precisão, anulável, opção|  
|Int16|Contém um valor inteiro de 16 bits com sinal.|Precisão, anulável, opção|  
|Int32|Contém um valor inteiro assinado de 32 bits.|Precisão, anulável, opção|  
|Int64|Contém um valor inteiro assinado de 64 bits.|Precisão, anulável, opção|  
|SByte|Contém um valor inteiro de 8 bits com sinal.|Precisão, anulável, opção|  
|Cadeia de Caracteres|Contém dados de caractere.|Unicode, FixedLength, MaxLength, agrupamento, precisão, anulável, opção|  
|Hora|Contém uma hora.|Precisão, anulável, opção|  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
