---
title: 'Mitigação: período de bloqueio de pool'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 42eaddeb2714a8c294f45d24eb7e6d9cf216fecc
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="a1b68-102">Mitigação: período de bloqueio de pool</span><span class="sxs-lookup"><span data-stu-id="a1b68-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="a1b68-103">O pool de conexão no período de bloqueio foi removido para conexões com bancos de dados SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="a1b68-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="a1b68-104">Descrição adicional</span><span class="sxs-lookup"><span data-stu-id="a1b68-104">Additional description</span></span>  
 <span data-ttu-id="a1b68-105">No [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e versões anteriores, quando um aplicativo encontra uma falha de conexão transitória ao se conectar a um banco de dados, a tentativa de conexão não pode ser recuperada rapidamente, pois o pool de conexões armazena em cache o erro e o gera novamente por 5 segundos a 1 minuto. Para saber mais, confira [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md) (Pool de conexão do SQL Server (ADO.NET)).</span><span class="sxs-lookup"><span data-stu-id="a1b68-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="a1b68-106">Esse comportamento é problemático para conexões com bancos de dados SQL do Azure que, muitas vezes, falham com erros transitórios que normalmente são recuperados em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="a1b68-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="a1b68-107">O recurso de bloqueio do pool de conexões significa que o aplicativo não pode se conectar ao banco de dados por um período extenso, mesmo que o banco de dados esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="a1b68-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="a1b68-108">Esse comportamento é especialmente problemático para aplicativos Web que se conectam aos bancos de dados SQL do Azure e que precisam renderizar em poucos segundos.</span><span class="sxs-lookup"><span data-stu-id="a1b68-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="a1b68-109">A partir do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], para solicitações de abertura da conexão com bancos de dados SQL do Azure conhecidos (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), os erros de abertura da conexão não são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="a1b68-109">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], for connection open requests to known Azure SQL databases (*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="a1b68-110">Para todas as outras tentativas de conexão, o período de bloqueio do pool de conexões continuará sendo imposto.</span><span class="sxs-lookup"><span data-stu-id="a1b68-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a1b68-111">Impacto</span><span class="sxs-lookup"><span data-stu-id="a1b68-111">Impact</span></span>  
 <span data-ttu-id="a1b68-112">Essa alteração permite que a tentativa de abertura da conexão seja repetida imediatamente para bancos de dados SQL do Azure, melhorando, assim, o desempenho dos aplicativos habilitados para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="a1b68-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a1b68-113">Redução</span><span class="sxs-lookup"><span data-stu-id="a1b68-113">Mitigation</span></span>  
 <span data-ttu-id="a1b68-114">Para aplicativos que são afetados negativamente por essa alteração, o período de bloqueio do pool de conexões pode ser configurado pela definição da nova propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1b68-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property.</span></span>  <span data-ttu-id="a1b68-115">O valor da propriedade é membro da enumeração <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> que pode assumir um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="a1b68-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 <span data-ttu-id="a1b68-116">É possível restaurar o comportamento anterior definindo a propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> como `PoolBlockingPeriod.AlwaysBlock`.</span><span class="sxs-lookup"><span data-stu-id="a1b68-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to `PoolBlockingPeriod.AlwaysBlock`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b68-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1b68-117">See Also</span></span>  
 [<span data-ttu-id="a1b68-118">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a1b68-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
