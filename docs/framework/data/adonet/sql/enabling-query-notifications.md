---
title: Habilitando notificações de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 4cda3ce3bcae7741df66496c87ba6654e0bbfe6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-query-notifications"></a>Habilitando notificações de consulta
Os aplicativos que consomem notificações de consulta têm um conjunto comum de requisitos. Sua fonte de dados deve ser configurada corretamente para dar suporte a notificações de consulta SQL e o usuário deve ter as permissões corretas de cliente e servidor.  
  
 Para usar notificações de consulta, deve você:  
  
-   Habilitar notificações de consulta para o banco de dados.  
  
-   Verificar se a identificação do usuário usada para se conectar ao banco de dados tem as permissões necessárias.  
  
-   Use um objeto <xref:System.Data.SqlClient.SqlCommand> para executar uma instrução SELECT válida com um objeto de notificação associada, <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.  
  
-   Forneça o código para processar a notificação se os dados que são monitorados forem alterados.  
  
## <a name="query-notifications-requirements"></a>Requisitos de notificações de consulta  
 As notificações de consulta têm suporte apenas para as instruções SELECT que atendem uma lista de requisitos específicos. A tabela a seguir fornece links para a documentação sobre Service Broker e Notificações de Consulta nos Manuais Online do SQL Server.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
-   [Criando uma consulta para notificação](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Considerações de segurança para o Service Broker](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [Segurança e proteção (Service Broker)](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [Considerações de segurança para serviços de notificações](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [Permissões de notificação de consulta](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [Considerações internacionais para o Service Broker](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [Considerações de Design de solução (Service Broker)](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [InfoCenter do desenvolvedor do Service Broker](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Guia do desenvolvedor (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Habilitando notificações de consulta para executar código de exemplo  
 Para habilitar o Service Broker no **AdventureWorks** banco de dados usando o SQL Server Management Studio, execute a seguinte instrução Transact-SQL:  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Para que os exemplos de notificação de consulta sejam executados corretamente, as seguintes instruções Transact-SQL devem ser executados no servidor de banco de dados.  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Permissões de notificações de consulta  
 Os usuários que executam comandos que solicitam notificação devem ter permissão de banco de dados SUBSCRIBE QUERY NOTIFICATIONS no servidor.  
  
 O código do lado do cliente que é executado em uma situação de confiança parcial requer o <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 O código a seguir cria um objeto <xref:System.Data.SqlClient.SqlClientPermission>, definindo o <xref:System.Security.Permissions.PermissionState> como <xref:System.Security.Permissions.PermissionState.Unrestricted>. O <xref:System.Security.CodeAccessPermission.Demand%2A> forçará um <xref:System.Security.SecurityException> em tempo de execução se todos os primeiros chamadores na pilha de chamadas não receberem a permissão.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Escolhendo um objeto de notificação  
 A API de notificações de consulta fornece dois objetos para processar notificações: <xref:System.Data.SqlClient.SqlDependency> e <xref:System.Data.Sql.SqlNotificationRequest>. Em geral, a maioria dos aplicativos que não sejam ASP.NET devem usar o objeto <xref:System.Data.SqlClient.SqlDependency>. Os aplicativos ASP.NET devem usar o <xref:System.Web.Caching.SqlCacheDependency> de nível mais alto, que envolve <xref:System.Data.SqlClient.SqlDependency> e fornece uma estrutura para administrar os objetos de notificação e cache.  
  
### <a name="using-sqldependency"></a>Utilizando SqlDependency  
 Para usar <xref:System.Data.SqlClient.SqlDependency>, o Service Broker deve ser habilitado para o banco de dados do SQL Server que está sendo usado e os usuários devem ter permissões para receber notificações. Os objetos do Service Broker, como a fila de notificação, são predefinidos.  
  
 Além disso, o <xref:System.Data.SqlClient.SqlDependency> automaticamente inicia um thread de trabalho para processar notificações quando forem publicadas na fila; ele também analisa a mensagem do Service Broker, expondo as informações como dados do argumento do evento. O <xref:System.Data.SqlClient.SqlDependency> deve ser inicializado chamando o método `Start` para estabelecer uma dependência para o banco de dados. Este é um método estático que precisa ser chamado apenas uma vez durante a inicialização do aplicativo para cada conexão de banco de dados necessária. O método `Stop` deve ser chamado no encerramento do aplicativo para cada conexão de dependência que foi feita.  
  
### <a name="using-sqlnotificationrequest"></a>Usando o SqlNotificationRequest  
 Em contraste, o <xref:System.Data.Sql.SqlNotificationRequest> exige que você implemente a infraestrutura de escuta inteira por você mesmo. Além disso, todos os objetos de suporte do Service Broker como a fila, o serviço e os tipos de mensagem com suporte pela fila devem ser definidos. Essa abordagem manual será útil se seu aplicativo exigir mensagens especiais de notificação ou comportamentos de notificação, ou se seu aplicativo fizer parte de um aplicativo maior do Service Broker.  
  
## <a name="see-also"></a>Consulte também  
 [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
