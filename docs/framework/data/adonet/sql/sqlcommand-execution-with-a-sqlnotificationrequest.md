---
title: "Execução de SqlCommand com um SqlNotificationRequest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 509c25f5c6d1108b76028af5cfd8f2a090c92137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="055fb-102">Execução de SqlCommand com um SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="055fb-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="055fb-103">Um <xref:System.Data.SqlClient.SqlCommand> pode ser configurado para gerar uma notificação quando as alterações de dados depois que ele foi buscado do servidor e o conjunto de resultados deve ser diferente se a consulta foi executada novamente.</span><span class="sxs-lookup"><span data-stu-id="055fb-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="055fb-104">Isso é útil para situações em que você deseja usar filas de notificação personalizada no servidor ou quando você não desejar manter objetos vivos.</span><span class="sxs-lookup"><span data-stu-id="055fb-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="055fb-105">Criando a solicitação de notificação</span><span class="sxs-lookup"><span data-stu-id="055fb-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="055fb-106">Você pode usar um <xref:System.Data.Sql.SqlNotificationRequest> objeto para criar a solicitação de notificação, associando-a um `SqlCommand` objeto.</span><span class="sxs-lookup"><span data-stu-id="055fb-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="055fb-107">Depois que a solicitação for criada, você não precisa mais o `SqlNotificationRequest` objeto.</span><span class="sxs-lookup"><span data-stu-id="055fb-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="055fb-108">Você pode consultar a fila de notificações e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="055fb-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="055fb-109">As notificações podem ocorrer mesmo que o aplicativo está desligado e reiniciado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="055fb-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="055fb-110">Quando o comando de notificação associado é executado, quaisquer alterações para o resultado original definir gatilho enviando uma mensagem para a fila do SQL Server que foi configurada na solicitação de notificação.</span><span class="sxs-lookup"><span data-stu-id="055fb-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="055fb-111">Como sondar a fila do SQL Server e interpretar a mensagem é específico para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="055fb-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="055fb-112">O aplicativo é responsável pela sondagem da fila e reagir com base no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="055fb-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="055fb-113">Ao usar solicitações de notificação do SQL Server com <xref:System.Data.SqlClient.SqlDependency>, crie seu próprio nome de fila em vez de usar o nome do serviço padrão.</span><span class="sxs-lookup"><span data-stu-id="055fb-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="055fb-114">Não há nenhum novos elementos de segurança do cliente para <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="055fb-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="055fb-115">Isso é basicamente um recurso de servidor e o servidor criado privilégios especiais que os usuários devem ter para solicitar uma notificação.</span><span class="sxs-lookup"><span data-stu-id="055fb-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="055fb-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="055fb-116">Example</span></span>  
 <span data-ttu-id="055fb-117">O fragmento de código a seguir demonstra como criar um <xref:System.Data.Sql.SqlNotificationRequest> e associá-la a um <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="055fb-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a><span data-ttu-id="055fb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="055fb-118">See Also</span></span>  
 [<span data-ttu-id="055fb-119">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="055fb-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 <span data-ttu-id="055fb-120">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="055fb-120">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
