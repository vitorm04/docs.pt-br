---
title: Execução de SqlCommand com um SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791537"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="14b3e-102">Execução de SqlCommand com um SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="14b3e-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="14b3e-103">Um <xref:System.Data.SqlClient.SqlCommand> pode ser configurado para gerar uma notificação quando os dados forem alterados após sua busca do servidor e o conjunto de resultados for diferente se a consulta tiver sido executada novamente.</span><span class="sxs-lookup"><span data-stu-id="14b3e-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="14b3e-104">Isso é útil para cenários em que você deseja usar filas de notificação personalizadas no servidor ou quando não deseja manter objetos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="14b3e-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="14b3e-105">Criando a solicitação de notificação</span><span class="sxs-lookup"><span data-stu-id="14b3e-105">Creating the Notification Request</span></span>

<span data-ttu-id="14b3e-106">Você pode usar um <xref:System.Data.Sql.SqlNotificationRequest> objeto para criar a solicitação de notificação ligando-a a `SqlCommand` um objeto.</span><span class="sxs-lookup"><span data-stu-id="14b3e-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="14b3e-107">Depois que a solicitação for criada, você não precisará `SqlNotificationRequest` mais do objeto.</span><span class="sxs-lookup"><span data-stu-id="14b3e-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="14b3e-108">Você pode consultar a fila para todas as notificações e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="14b3e-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="14b3e-109">As notificações podem ocorrer mesmo que o aplicativo seja desligado e subsequentemente reiniciado.</span><span class="sxs-lookup"><span data-stu-id="14b3e-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="14b3e-110">Quando o comando com a notificação associada é executado, qualquer alteração no gatilho do conjunto de resultados original envia uma mensagem para a fila de SQL Server que foi configurada na solicitação de notificação.</span><span class="sxs-lookup"><span data-stu-id="14b3e-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="14b3e-111">Como você sonda a fila de SQL Server e interpreta a mensagem é específica para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="14b3e-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="14b3e-112">O aplicativo é responsável por sondar a fila e reagir com base no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="14b3e-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="14b3e-113">Ao usar SQL Server solicitações de notificação <xref:System.Data.SqlClient.SqlDependency>com, crie seu próprio nome de fila em vez de usar o nome do serviço padrão.</span><span class="sxs-lookup"><span data-stu-id="14b3e-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="14b3e-114">Não há nenhum novo elemento de segurança do lado do <xref:System.Data.Sql.SqlNotificationRequest>cliente para o.</span><span class="sxs-lookup"><span data-stu-id="14b3e-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="14b3e-115">Isso é basicamente um recurso de servidor e o servidor criou privilégios especiais que os usuários precisam ter para solicitar uma notificação.</span><span class="sxs-lookup"><span data-stu-id="14b3e-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="14b3e-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14b3e-116">Example</span></span>

<span data-ttu-id="14b3e-117">O fragmento de código a seguir demonstra como criar <xref:System.Data.Sql.SqlNotificationRequest> um e associá-lo <xref:System.Data.SqlClient.SqlCommand>a um.</span><span class="sxs-lookup"><span data-stu-id="14b3e-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
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
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="14b3e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14b3e-118">See also</span></span>

- [<span data-ttu-id="14b3e-119">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="14b3e-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="14b3e-120">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="14b3e-120">[ADO.NET Overview](../ado-net-overview.md)</span></span>
