---
title: "Geração SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7c0f0b8734de219208cba3caf0220d1e9436a3c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-generation"></a>Geração SQL
Quando você escreve um provedor para [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você deve converter árvores de comando de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] em SQL que um base de dados específico, pode compreender como Transact-SQL para SQL Server ou PL/SQL para Oracle. Nesta seção, você aprenderá como desenvolver um componente de geração SQL (para consultas SELECT) para um provedor de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] . Para obter informações sobre como inserir, atualizar e excluir consultas, consulte [modificação de geração de SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Para entender esta seção, você deve estar familiarizado com [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e o modelo de provedor ADO.NET. Você também deve entender árvores e <xref:System.Data.Common.CommandTrees.DbExpression>de comando.  
  
## <a name="the-role-of-the-sql-generation-module"></a>A função do módulo de geração SQL  
 O módulo de geração SQL de um provedor de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] converte uma determinada árvore de comando de consulta em uma única instrução SQL SELECT que tem como alvo um SQL: a base de dados compliant 1999. O SQL gerado deve ter como poucas consultas aninhadas possível. O módulo de geração do SQL não deve simplificar a árvore de comando de consulta de saída. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fará isso, por exemplo eliminando join e recolher nós consecutivos de filtro.  
  
 A classe de <xref:System.Data.Common.DbProviderServices> é o ponto de partida para acessar a camada de geração SQL para converter árvores de comando em <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [A forma das árvores de comando](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Gerando SQL das árvores de comando – Práticas recomendadas](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Geração de SQL no provedor exemplo](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um Provedor de Dados do Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
