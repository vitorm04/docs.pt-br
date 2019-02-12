---
title: Habilitando notificações de consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 2a711ad4779b8c932436ce1886b1a93dda849a94
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093951"
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
  
 **Documentação do SQL Server**  
  
-   [Criando uma consulta para notificação](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
-   [Considerações de segurança para o Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
-   [Segurança e proteção (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
-   [Considerações de segurança para serviços de notificações](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
-   [Permissões de notificação de consulta](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
-   [Considerações internacionais para Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
-   [Considerações de Design de solução (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
-   [InfoCenter do desenvolvedor do Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
-   [Guia do desenvolvedor (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Habilitando notificações de consulta para executar código de exemplo  
 Para habilitar o Service Broker na **AdventureWorks** banco de dados usando o SQL Server Management Studio, execute a seguinte instrução Transact-SQL:  
  
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
- [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
