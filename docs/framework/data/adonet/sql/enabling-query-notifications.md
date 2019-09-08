---
title: Habilitando notificações de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 9919bad113eb11a38ce137a2cbbf6c67bd5b21ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794077"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="3c9a8-102">Habilitando notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="3c9a8-102">Enabling Query Notifications</span></span>
<span data-ttu-id="3c9a8-103">Os aplicativos que consomem notificações de consulta têm um conjunto comum de requisitos.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="3c9a8-104">Sua fonte de dados deve ser configurada corretamente para dar suporte a notificações de consulta SQL e o usuário deve ter as permissões corretas de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="3c9a8-105">Para usar notificações de consulta, deve você:</span><span class="sxs-lookup"><span data-stu-id="3c9a8-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="3c9a8-106">Habilitar notificações de consulta para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="3c9a8-107">Verificar se a identificação do usuário usada para se conectar ao banco de dados tem as permissões necessárias.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="3c9a8-108">Use um objeto <xref:System.Data.SqlClient.SqlCommand> para executar uma instrução SELECT válida com um objeto de notificação associada, <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="3c9a8-109">Forneça o código para processar a notificação se os dados que são monitorados forem alterados.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="3c9a8-110">Requisitos de notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="3c9a8-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="3c9a8-111">As notificações de consulta têm suporte apenas para as instruções SELECT que atendem uma lista de requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="3c9a8-112">A tabela a seguir fornece links para a documentação sobre Service Broker e Notificações de Consulta nos Manuais Online do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="3c9a8-113">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3c9a8-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="3c9a8-114">[Criando uma consulta para notificação](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="3c9a8-115">[Considerações de segurança para Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="3c9a8-116">[Segurança e proteção (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="3c9a8-117">[Considerações de segurança para o Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="3c9a8-118">[Permissões de notificação de consulta](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="3c9a8-119">[Considerações internacionais para Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="3c9a8-120">[Considerações de design de solução (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="3c9a8-121">[InfoCenter do Service Broker Developer](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="3c9a8-122">[Guia do desenvolvedor (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3c9a8-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="3c9a8-123">Habilitando notificações de consulta para executar código de exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9a8-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="3c9a8-124">Para habilitar Service Broker no banco de dados **AdventureWorks** usando SQL Server Management Studio, execute a seguinte instrução TRANSACT-SQL:</span><span class="sxs-lookup"><span data-stu-id="3c9a8-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="3c9a8-125">Para que os exemplos de notificação de consulta sejam executados corretamente, as seguintes instruções Transact-SQL devem ser executados no servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="3c9a8-126">Permissões de notificações de consulta</span><span class="sxs-lookup"><span data-stu-id="3c9a8-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="3c9a8-127">Os usuários que executam comandos que solicitam notificação devem ter permissão de banco de dados SUBSCRIBE QUERY NOTIFICATIONS no servidor.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="3c9a8-128">O código do lado do cliente que é executado em uma situação de confiança parcial requer o <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="3c9a8-129">O código a seguir cria um objeto <xref:System.Data.SqlClient.SqlClientPermission>, definindo o <xref:System.Security.Permissions.PermissionState> como <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="3c9a8-130">O <xref:System.Security.CodeAccessPermission.Demand%2A> forçará um <xref:System.Security.SecurityException> em tempo de execução se todos os primeiros chamadores na pilha de chamadas não receberem a permissão.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="3c9a8-131">Escolhendo um objeto de notificação</span><span class="sxs-lookup"><span data-stu-id="3c9a8-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="3c9a8-132">A API de notificações de consulta fornece dois objetos para processar notificações: <xref:System.Data.SqlClient.SqlDependency> e <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="3c9a8-133">Em geral, a maioria dos aplicativos que não sejam ASP.NET devem usar o objeto <xref:System.Data.SqlClient.SqlDependency>.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="3c9a8-134">Os aplicativos ASP.NET devem usar o <xref:System.Web.Caching.SqlCacheDependency> de nível mais alto, que envolve <xref:System.Data.SqlClient.SqlDependency> e fornece uma estrutura para administrar os objetos de notificação e cache.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="3c9a8-135">Utilizando SqlDependency</span><span class="sxs-lookup"><span data-stu-id="3c9a8-135">Using SqlDependency</span></span>  
 <span data-ttu-id="3c9a8-136">Para usar <xref:System.Data.SqlClient.SqlDependency>, o Service Broker deve ser habilitado para o banco de dados do SQL Server que está sendo usado e os usuários devem ter permissões para receber notificações.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="3c9a8-137">Os objetos do Service Broker, como a fila de notificação, são predefinidos.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="3c9a8-138">Além disso, o <xref:System.Data.SqlClient.SqlDependency> automaticamente inicia um thread de trabalho para processar notificações quando forem publicadas na fila; ele também analisa a mensagem do Service Broker, expondo as informações como dados do argumento do evento.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="3c9a8-139">O <xref:System.Data.SqlClient.SqlDependency> deve ser inicializado chamando o método `Start` para estabelecer uma dependência para o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="3c9a8-140">Este é um método estático que precisa ser chamado apenas uma vez durante a inicialização do aplicativo para cada conexão de banco de dados necessária.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="3c9a8-141">O método `Stop` deve ser chamado no encerramento do aplicativo para cada conexão de dependência que foi feita.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="3c9a8-142">Usando o SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="3c9a8-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="3c9a8-143">Em contraste, o <xref:System.Data.Sql.SqlNotificationRequest> exige que você implemente a infraestrutura de escuta inteira por você mesmo.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="3c9a8-144">Além disso, todos os objetos de suporte do Service Broker como a fila, o serviço e os tipos de mensagem com suporte pela fila devem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="3c9a8-145">Essa abordagem manual será útil se seu aplicativo exigir mensagens especiais de notificação ou comportamentos de notificação, ou se seu aplicativo fizer parte de um aplicativo maior do Service Broker.</span><span class="sxs-lookup"><span data-stu-id="3c9a8-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9a8-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c9a8-146">See also</span></span>

- [<span data-ttu-id="3c9a8-147">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="3c9a8-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="3c9a8-148">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3c9a8-148">[ADO.NET Overview](../ado-net-overview.md)</span></span>
