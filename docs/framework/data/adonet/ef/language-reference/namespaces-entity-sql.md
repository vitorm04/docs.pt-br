---
title: Namespaces (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7bcd7a72df8afbd598a15ccd9a259ed11b5b9ef7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583817"
---
# <a name="namespaces-entity-sql"></a>Namespaces (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] apresenta namespaces para evitar conflitos de nome para identificadores globais como nomes de tipo, conjuntos de entidades, funções, e assim por diante. O suporte a namespace em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é semelhante ao suporte do namespace do .NET Framework.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornece dois formulários que a cláusula group UTILIZAÇÃO: namespaces qualificadas (onde um alias mais curtas são fornecidas para o namespace), e namespaces não qualificado, como ilustrado no exemplo a seguir:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Regras de resolução de nomes  
 Se um identificador não pode ser resolvido em escopos locais, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta localizar o nome em escopos globais (namespaces). [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta corresponder primeiro o identificador (prefixo) com uma namespaces qualificadas. Se houver uma correspondência, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta resolver o restante do identificador no namespace especificado. Se nenhuma correspondência for encontrada, uma exceção é lançada.  
  
 Em seguida, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta procurar todos os namespaces de não-qualificados (especificados no prólogo) para o identificador. Se o identificador pode ser localizado em exatamente um namespace, esse local é retornado. Se mais de um namespace tiver uma correspondência para o identificador, uma exceção é lançada. Se nenhuma namespace pode ser identificado para o identificador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passa o nome no escopo externo seguir (o <xref:System.Data.Common.DbCommand> ou <xref:System.Data.Common.DbConnection> objeto), conforme ilustrado no exemplo a seguir:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Diferenças do .NET Framework  
 No .NET Framework, você pode usar namespaces parcialmente qualificados. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não permite isso.  
  
## <a name="adonet-usage"></a>Uso do ADO.NET  
 Consultas são expressos por meio de objetos ADO.NET <xref:System.Data.Common.DbCommand> . os objetos de<xref:System.Data.Common.DbCommand> podem ser compilados sobre objetos de <xref:System.Data.Common.DbConnection> . Namespaces também podem ser especificadas como parte de objetos de <xref:System.Data.Common.DbCommand> e de <xref:System.Data.Common.DbConnection> . Se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] não é possível resolver um identificador dentro da consulta em si, os namespaces externos são sondadas (baseado em regras similares).  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
