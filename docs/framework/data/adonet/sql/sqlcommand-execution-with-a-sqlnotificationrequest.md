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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Execução de SqlCommand com um SqlNotificationRequest
Um <xref:System.Data.SqlClient.SqlCommand> pode ser configurado para gerar uma notificação quando as alterações de dados depois que ele foi buscado do servidor e o conjunto de resultados deve ser diferente se a consulta foi executada novamente. Isso é útil para situações em que você deseja usar filas de notificação personalizada no servidor ou quando você não desejar manter objetos vivos.  
  
## <a name="creating-the-notification-request"></a>Criando a solicitação de notificação  
 Você pode usar um <xref:System.Data.Sql.SqlNotificationRequest> objeto para criar a solicitação de notificação, associando-a um `SqlCommand` objeto. Depois que a solicitação for criada, você não precisa mais o `SqlNotificationRequest` objeto. Você pode consultar a fila de notificações e responder adequadamente. As notificações podem ocorrer mesmo que o aplicativo está desligado e reiniciado posteriormente.  
  
 Quando o comando de notificação associado é executado, quaisquer alterações para o resultado original definir gatilho enviando uma mensagem para a fila do SQL Server que foi configurada na solicitação de notificação.  
  
 Como sondar a fila do SQL Server e interpretar a mensagem é específico para seu aplicativo. O aplicativo é responsável pela sondagem da fila e reagir com base no conteúdo da mensagem.  
  
> [!NOTE]
>  Ao usar solicitações de notificação do SQL Server com <xref:System.Data.SqlClient.SqlDependency>, crie seu próprio nome de fila em vez de usar o nome do serviço padrão.  
  
 Não há nenhum novos elementos de segurança do cliente para <xref:System.Data.Sql.SqlNotificationRequest>. Isso é basicamente um recurso de servidor e o servidor criado privilégios especiais que os usuários devem ter para solicitar uma notificação.  
  
### <a name="example"></a>Exemplo  
 O fragmento de código a seguir demonstra como criar um <xref:System.Data.Sql.SqlNotificationRequest> e associá-la a um <xref:System.Data.SqlClient.SqlCommand>.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
