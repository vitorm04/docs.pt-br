---
title: Execução de SqlCommand com um SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 90ec7653f7de931bd8127263643b5467998325b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364457"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Execução de SqlCommand com um SqlNotificationRequest

Um <xref:System.Data.SqlClient.SqlCommand> pode ser configurado para gerar uma notificação quando os dados forem alterados depois que ela foi buscada do servidor e o conjunto de resultados seriam diferente se a consulta foi executada novamente. Isso é útil para cenários em que você deseja usar filas de notificação personalizada no servidor ou quando você não deseja manter objetos ativos.

## <a name="creating-the-notification-request"></a>Criando a solicitação de notificação

Você pode usar um <xref:System.Data.Sql.SqlNotificationRequest> objeto para criar a solicitação de notificação, associando-o para um `SqlCommand` objeto. Depois que a solicitação é criada, você não precisa mais o `SqlNotificationRequest` objeto. Você pode consultar a fila para todas as notificações e responder adequadamente. Notificações podem ocorrer mesmo que o aplicativo é desligado e reiniciado posteriormente.

Quando o comando com a notificação associada é executado, todas as alterações para o resultado original definir gatilho enviando uma mensagem para a fila do SQL Server que foi configurada na solicitação de notificação.

Como você sondar a fila do SQL Server e interpretar a mensagem é específico para seu aplicativo. O aplicativo é responsável por sondar a fila e reagir com base no conteúdo da mensagem.

> [!NOTE]
> Ao usar solicitações de notificação do SQL Server com <xref:System.Data.SqlClient.SqlDependency>, crie seu próprio nome de fila em vez de usar o nome do serviço padrão.

Não há nenhum novos elementos de segurança do cliente para <xref:System.Data.Sql.SqlNotificationRequest>. Isso é principalmente um recurso de servidor e o servidor criado privilégios especiais que os usuários devem ter para solicitar uma notificação.

### <a name="example"></a>Exemplo

O fragmento de código a seguir demonstra como criar uma <xref:System.Data.Sql.SqlNotificationRequest> e associá-la com um <xref:System.Data.SqlClient.SqlCommand>.

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

- [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
