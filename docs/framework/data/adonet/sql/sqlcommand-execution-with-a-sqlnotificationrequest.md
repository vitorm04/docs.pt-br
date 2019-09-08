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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Execução de SqlCommand com um SqlNotificationRequest

Um <xref:System.Data.SqlClient.SqlCommand> pode ser configurado para gerar uma notificação quando os dados forem alterados após sua busca do servidor e o conjunto de resultados for diferente se a consulta tiver sido executada novamente. Isso é útil para cenários em que você deseja usar filas de notificação personalizadas no servidor ou quando não deseja manter objetos dinâmicos.

## <a name="creating-the-notification-request"></a>Criando a solicitação de notificação

Você pode usar um <xref:System.Data.Sql.SqlNotificationRequest> objeto para criar a solicitação de notificação ligando-a a `SqlCommand` um objeto. Depois que a solicitação for criada, você não precisará `SqlNotificationRequest` mais do objeto. Você pode consultar a fila para todas as notificações e responder adequadamente. As notificações podem ocorrer mesmo que o aplicativo seja desligado e subsequentemente reiniciado.

Quando o comando com a notificação associada é executado, qualquer alteração no gatilho do conjunto de resultados original envia uma mensagem para a fila de SQL Server que foi configurada na solicitação de notificação.

Como você sonda a fila de SQL Server e interpreta a mensagem é específica para seu aplicativo. O aplicativo é responsável por sondar a fila e reagir com base no conteúdo da mensagem.

> [!NOTE]
> Ao usar SQL Server solicitações de notificação <xref:System.Data.SqlClient.SqlDependency>com, crie seu próprio nome de fila em vez de usar o nome do serviço padrão.

Não há nenhum novo elemento de segurança do lado do <xref:System.Data.Sql.SqlNotificationRequest>cliente para o. Isso é basicamente um recurso de servidor e o servidor criou privilégios especiais que os usuários precisam ter para solicitar uma notificação.

### <a name="example"></a>Exemplo

O fragmento de código a seguir demonstra como criar <xref:System.Data.Sql.SqlNotificationRequest> um e associá-lo <xref:System.Data.SqlClient.SqlCommand>a um.

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

## <a name="see-also"></a>Consulte também

- [Notificações de consulta no SQL Server](query-notifications-in-sql-server.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
