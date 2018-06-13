---
title: 'Mitigação: período de bloqueio de pool'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e402ba9cb5de8e85ce6912e2e5b760ef340c2cf4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389948"
---
# <a name="mitigation-pool-blocking-period"></a>Mitigação: período de bloqueio de pool
O pool de conexão no período de bloqueio foi removido para conexões com bancos de dados SQL do Azure.  
  
## <a name="additional-description"></a>Descrição adicional  
 No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores, quando um aplicativo encontra uma falha de conexão transitória ao se conectar a um banco de dados, a tentativa de conexão não pode ser recuperada rapidamente, pois o pool de conexões armazena em cache o erro e o gera novamente por 5 segundos a 1 minuto. Para saber mais, confira [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md) (Pool de conexão do SQL Server (ADO.NET)). Esse comportamento é problemático para conexões com bancos de dados SQL do Azure que, muitas vezes, falham com erros transitórios que normalmente são recuperados em alguns segundos. O recurso de bloqueio do pool de conexões significa que o aplicativo não pode se conectar ao banco de dados por um período extenso, mesmo que o banco de dados esteja disponível. Esse comportamento é especialmente problemático para aplicativos Web que se conectam aos bancos de dados SQL do Azure e que precisam renderizar em poucos segundos.  
  
 A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], para solicitações de abertura da conexão com bancos de dados SQL do Azure conhecidos (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), os erros de abertura da conexão não são armazenados em cache. Para todas as outras tentativas de conexão, o período de bloqueio do pool de conexões continuará sendo imposto.  
  
## <a name="impact"></a>Impacto  
 Essa alteração permite que a tentativa de abertura da conexão seja repetida imediatamente para bancos de dados SQL do Azure, melhorando, assim, o desempenho dos aplicativos habilitados para a nuvem.  
  
## <a name="mitigation"></a>Redução  
 Para aplicativos que são afetados negativamente por essa alteração, o período de bloqueio do pool de conexões pode ser configurado pela definição da nova propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.  O valor da propriedade é membro da enumeração <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> que pode assumir um dos três valores:  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 É possível restaurar o comportamento anterior definindo a propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> como `PoolBlockingPeriod.AlwaysBlock`.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
