---
title: Escrevendo um provedor de dados do Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 254207b9c3f5edd55fff867b784d71359f6c94c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627936"
---
# <a name="writing-an-entity-framework-data-provider"></a>Escrevendo um provedor de dados do Entity Framework
Esta seção discute como escrever um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provedor para dar suporte a uma fonte de dados diferente do SQL Server. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclui um provedor que dá suporte ao SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Introdução ao modelo de provedor de Entity Framework  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é independente de banco de dados e você pode escrever um provedor usando o modelo do provedor do ADO.NET para se conectar a um conjunto de várias fontes de dados.  
  
 O provedor de dados do Entity Framework (compilado usando o modelo do provedor de dados do ADO.NET) executa as seguintes funções:  
  
-   Mapeia tipos primitivos de EDM (Modelo de Dados de Entidade) para os tipos de provedor.  
  
-   Expõe funções específicas do provedor.  
  
-   Gera comandos específicos de provedor para um determinado DbQueryCommandTree para dar suporte a consultas do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Gera comandos de atualização específicos do provedor para um determinado DbModificationCommandTree para dar suporte a atualizações por meio do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Expõe arquivos de mapeamento para a definição do esquema de armazenamento, para dar suporte à geração de um modelo baseado em um banco de dados.  
  
-   Expõe metadados (tabelas e exibições, por exemplo) por meio de um modelo conceitual.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Amostra  
 Consulte a [provedor de exemplo do Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) para obter um exemplo de um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provedor que dá suporte a uma fonte de dados diferente do SQL Server.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Geração de SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Geração de SQL de modificação](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Especificação do manifesto do provedor](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Consulte também
- [Trabalhando com Provedores de Dados](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
