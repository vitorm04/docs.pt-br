---
title: Habilitando notificações de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 693e67b4d369eb69b8e0a9dded6decb2d3928459
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554873"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="19805-102">Habilitando notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="19805-102">Enabling Query Notifications</span></span>
<span data-ttu-id="19805-103">Os aplicativos que consomem notificações de consulta têm um conjunto comum de requisitos.</span><span class="sxs-lookup"><span data-stu-id="19805-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="19805-104">Sua fonte de dados deve ser configurada corretamente para dar suporte a notificações de consulta SQL e o usuário deve ter as permissões corretas de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="19805-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="19805-105">Para usar as notificações de consulta, você deve:</span><span class="sxs-lookup"><span data-stu-id="19805-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="19805-106">Habilitar as notificações de consulta para seu banco de dados.</span><span class="sxs-lookup"><span data-stu-id="19805-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="19805-107">Verificar se a ID de usuário usada para se conectar ao banco de dados tem as permissões necessárias.</span><span class="sxs-lookup"><span data-stu-id="19805-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="19805-108">Usar um objeto <xref:System.Data.SqlClient.SqlCommand> para executar uma instrução SELECT válida com um objeto de notificação associado – seja <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="19805-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="19805-109">Fornecer o código para processar a notificação se os dados que estão sendo monitorados forem alterados.</span><span class="sxs-lookup"><span data-stu-id="19805-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="19805-110">Requisitos de notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="19805-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="19805-111">As notificações de consulta são compatíveis apenas com instruções SELECT que atendem a uma lista de requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="19805-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="19805-112">A tabela a seguir fornece links para a documentação do Service Broker e das notificações de consulta nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19805-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="19805-113">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="19805-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="19805-114">[Criando uma consulta para notificação](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-114">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="19805-115">[Considerações de segurança para Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="19805-115">[Security Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="19805-116">[Segurança e proteção (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-116">[Security and Protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="19805-117">[Considerações de segurança para serviços de notificação](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="19805-117">[Security Considerations for Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="19805-118">[Permissões de notificação de consulta](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-118">[Query Notification Permissions](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="19805-119">[Considerações internacionais para Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="19805-119">[International Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="19805-120">[Considerações sobre design de solução (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-120">[Solution Design Considerations (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="19805-121">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-121">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="19805-122">[Guia do desenvolvedor (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="19805-122">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="19805-123">Habilitando notificações de consulta para executar código de exemplo</span><span class="sxs-lookup"><span data-stu-id="19805-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="19805-124">Para habilitar o Service Broker no banco de dados **AdventureWorks** usando o SQL Server Management Studio, execute a seguinte instrução Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="19805-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="19805-125">Para que os exemplos de notificação de consulta sejam executados corretamente, as instruções Transact-SQL a seguir devem ser executadas no servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="19805-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="19805-126">Permissões de notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="19805-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="19805-127">Os usuários que executam comandos solicitando notificação devem ter a permissão de banco de dados SUBSCRIBE QUERY NOTIFICATIONS no servidor.</span><span class="sxs-lookup"><span data-stu-id="19805-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="19805-128">O código do lado do cliente que é executado em uma situação de confiança parcial requer o <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="19805-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="19805-129">O código a seguir cria um objeto <xref:System.Data.SqlClient.SqlClientPermission>, configurando o <xref:System.Security.Permissions.PermissionState> como <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="19805-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="19805-130">O <xref:System.Security.CodeAccessPermission.Demand%2A> forçará um <xref:System.Security.SecurityException> em tempo de execução se todos os chamadores mais acima na pilha de chamadas não tiverem recebido a permissão.</span><span class="sxs-lookup"><span data-stu-id="19805-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="19805-131">Escolhendo um objeto de notificação</span><span class="sxs-lookup"><span data-stu-id="19805-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="19805-132">A API de notificações de consulta fornece dois objetos para processar notificações: <xref:System.Data.SqlClient.SqlDependency> e <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="19805-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="19805-133">Em geral, a maioria dos aplicativos que não sejam ASP.NET devem usar o objeto <xref:System.Data.SqlClient.SqlDependency>.</span><span class="sxs-lookup"><span data-stu-id="19805-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="19805-134">Os aplicativos ASP.NET devem usar o <xref:System.Web.Caching.SqlCacheDependency> de nível mais alto, que envolve <xref:System.Data.SqlClient.SqlDependency> e fornece uma estrutura para administrar os objetos de notificação e cache.</span><span class="sxs-lookup"><span data-stu-id="19805-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="19805-135">Como usar SqlDependency</span><span class="sxs-lookup"><span data-stu-id="19805-135">Using SqlDependency</span></span>  
 <span data-ttu-id="19805-136">Para usar <xref:System.Data.SqlClient.SqlDependency>, o Service Broker deverá ser habilitado para o Banco de Dados do SQL Server usado e os usuários devem ter permissões para receber notificações.</span><span class="sxs-lookup"><span data-stu-id="19805-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="19805-137">Os objetos do Service Broker, como a fila de notificação, são predefinidos.</span><span class="sxs-lookup"><span data-stu-id="19805-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="19805-138">Além disso, o <xref:System.Data.SqlClient.SqlDependency> inicia automaticamente um thread de trabalho para processar as notificações à medida que elas são postadas na fila. Ele também analisa a mensagem do Service Broker, expondo as informações como dados de argumento do evento.</span><span class="sxs-lookup"><span data-stu-id="19805-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="19805-139">O <xref:System.Data.SqlClient.SqlDependency> deve ser inicializado chamando o método `Start` para estabelecer uma dependência com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="19805-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="19805-140">Esse é um método estático que precisa ser chamado apenas uma vez durante a inicialização do aplicativo para cada conexão de banco de dados necessária.</span><span class="sxs-lookup"><span data-stu-id="19805-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="19805-141">O método `Stop` deve ser chamado na terminação do aplicativo para cada conexão de dependência que foi feita.</span><span class="sxs-lookup"><span data-stu-id="19805-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="19805-142">Como usar SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="19805-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="19805-143">Por outro lado, o <xref:System.Data.Sql.SqlNotificationRequest> exige que você implemente toda a infraestrutura de escuta por conta própria.</span><span class="sxs-lookup"><span data-stu-id="19805-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="19805-144">Além disso, todos os objetos do Service Broker de suporte, como os tipos de fila, serviço e mensagem compatíveis com a fila, devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="19805-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="19805-145">Essa abordagem manual será útil se o aplicativo exigir mensagens de notificação especiais ou comportamentos de notificação ou se o aplicativo fizer parte de um aplicativo de Service Broker maior.</span><span class="sxs-lookup"><span data-stu-id="19805-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19805-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="19805-146">See also</span></span>

- [<span data-ttu-id="19805-147">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="19805-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="19805-148">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19805-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
