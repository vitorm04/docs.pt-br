---
title: Geração SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854358"
---
# <a name="sql-generation"></a>Geração SQL
Ao escrever um provedor para o Entity Framework, você deve converter Entity Framework árvores de comando no SQL que um banco de dados específico pode entender, como Transact-SQL para SQL Server ou PL/SQL para Oracle. Nesta seção, você aprenderá a desenvolver um componente de geração de SQL (para consultas SELECT) para um provedor de Entity Framework. Para obter informações sobre as consultas Insert, Update e Delete, consulte [modification SQL Generation](modification-sql-generation.md).  
  
 Para entender esta seção, você deve estar familiarizado com o Entity Framework e o modelo de provedor ADO.NET. Você também deve entender árvores e <xref:System.Data.Common.CommandTrees.DbExpression>de comando.  
  
## <a name="the-role-of-the-sql-generation-module"></a>A função do módulo de geração SQL  
 O módulo de geração de SQL de um provedor de Entity Framework converte uma determinada árvore de comando de consulta em uma única instrução SQL SELECT que tem como alvo um banco de dados compatível com SQL: 1999. O SQL gerado deve ter como poucas consultas aninhadas possível. O módulo de geração do SQL não deve simplificar a árvore de comando de consulta de saída. O Entity Framework fará isso, por exemplo, eliminando junções e recolhendo nós de filtro consecutivos.  
  
 A classe de <xref:System.Data.Common.DbProviderServices> é o ponto de partida para acessar a camada de geração SQL para converter árvores de comando em <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [A forma das árvores de comando](the-shape-of-the-command-trees.md)  
  
 [Gerando SQL das árvores de comando – Práticas recomendadas](generating-sql-from-command-trees-best-practices.md)  
  
 [Geração de SQL no provedor exemplo](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Consulte também

- [Escrevendo um Provedor de Dados do Entity Framework](writing-an-ef-data-provider.md)
