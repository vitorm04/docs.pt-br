---
title: 'Modelo de dados de entidade: Tipos de dados primitivos'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: 2c2e1056c43f974ec38407372a8f447e52b4a630
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54748006"
---
# <a name="entity-data-model-primitive-data-types"></a>Modelo de dados de entidade: Tipos de dados primitivos
Modelo de dados de entidade (EDM) suporta um conjunto de tipos de dados primitivo abstrato (como cadeia de caracteres, Boolean, Int32 e assim por diante) que são usadas para definir [propriedades](../../../../docs/framework/data/adonet/property.md) em um modelo conceitual. Esses tipos de dados primitivos são proxies para os tipos de dados primitivos reais que são suportados no armazenamento ou no ambiente de hospedagem, como um base de dados SQL Server ou Common Language Runtime (CLR). EDM não define a semântica das operações ou das conversões sobre tipos de dados primitivos; essa semântica é definida pelo armazenamento ou pelo ambiente de hospedagem. Normalmente, os tipos de dados primitivos em EDM são mapeados para os tipos de dados primitivos no armazenamento ou no ambiente de hospedagem. Para obter informações sobre como o Entity Framework mapeia tipos primitivos em EDM aos tipos de dados do SQL Server, consulte [SqlClient para Entity FrameworkTypes](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  EDM não suporta coleções de tipos de dados primitivos.  
  
 Para obter informações sobre os tipos de dados estruturados em EDM, consulte [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) e [tipo complexo](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Tipos de dados primitivos suportados em Modelo de Dados de Entidade  
 A tabela abaixo lista os tipos de dados primitivos suportados por EDM. A tabela também lista os [facetas](../../../../docs/framework/data/adonet/facet.md) que pode ser aplicado a cada tipo de dados primitivo.  
  
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
|Int16|Contém um valor inteiro com sinal de 16 bits.|Precisão, anulável, opção|  
|Int32|Contém um valor inteiro com sinal de 32 bits.|Precisão, anulável, opção|  
|Int64|Contém um valor inteiro com sinal de 64 bits.|Precisão, anulável, opção|  
|SByte|Contém um valor inteiro de 8 bits com sinal.|Precisão, anulável, opção|  
|Cadeia de Caracteres|Contém dados de caractere.|Unicode, FixedLength, MaxLength, ordenação, precisão, anulável, opção|  
|Hora|Contém uma hora.|Precisão, anulável, opção|  
  
## <a name="see-also"></a>Consulte também
- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
