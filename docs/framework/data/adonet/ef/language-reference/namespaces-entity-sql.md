---
title: Namespaces (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: bef2fa96ce090a600155d68ecc3daea55b675840
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185517"
---
# <a name="namespaces-entity-sql"></a>Namespaces (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] apresenta namespaces para evitar conflitos de nome para identificadores globais como nomes de tipo, conjuntos de entidades, funções e assim por diante. O suporte a namespace em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é semelhante ao suporte a namespace no [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece dois formulários a cláusula USING: qualificado namespaces (onde um alias mais curto é fornecido para o namespace) e namespaces não qualificado, conforme ilustrado no exemplo a seguir:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Regras de resolução de nomes  
 Se um identificador não pode ser resolvido em escopos locais, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta localizar o nome em escopos globais (namespaces). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] primeiro tenta corresponder o identificador (prefixo) com um dos namespaces qualificadas. Se houver uma correspondência, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta resolver o restante do identificador no namespace especificado. Se nenhuma correspondência for encontrada, uma exceção é lançada.  
  
 Em seguida, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta procurar todos os namespaces de não-qualificados (especificados no prólogo) para o identificador. Se o identificador pode ser localizado em exatamente um namespace, esse local é retornado. Se mais de um namespace tiver uma correspondência para o identificador, uma exceção é lançada. Se nenhuma namespace pode ser identificado para o identificador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passa o nome no escopo externo seguir (o <xref:System.Data.Common.DbCommand> ou <xref:System.Data.Common.DbConnection> objeto), conforme ilustrado no exemplo a seguir:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Diferenças do .NET Framework  
 Em [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], você pode usar namespaces parcialmente qualificadas. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não permite isso.  
  
## <a name="adonet-usage"></a>Uso do ADO.NET  
 Consultas são expressos por meio de objetos ADO.NET <xref:System.Data.Common.DbCommand> . <xref:System.Data.Common.DbCommand> objetos podem ser compilados sobre <xref:System.Data.Common.DbConnection> objetos. Namespaces também podem ser especificadas como parte de objetos de <xref:System.Data.Common.DbCommand> e de <xref:System.Data.Common.DbConnection> . Se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é possível resolver um identificador dentro da consulta em si, os namespaces externos são sondadas (baseado em regras similares).  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Visão geral da Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
