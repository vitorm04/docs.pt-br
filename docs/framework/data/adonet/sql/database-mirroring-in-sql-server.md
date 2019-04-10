---
title: Espelhamento de banco de dados no SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 1445a95fc6360a7956048d2bae2d840f9c3f7a99
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325690"
---
# <a name="database-mirroring-in-sql-server"></a>Espelhamento de banco de dados no SQL Server
O espelhamento de banco de dados no SQL Server permite que você mantenha uma cópia, ou o espelho, de um banco de dados do SQL Server em um servidor em espera. O espelhamento garante que duas cópias separadas dos dados existam o tempo todo, fornecendo a alta disponibilidade e a redundância completa de dados. O provedor de dados .NET para o SQL Server fornece suporte implícito para espelhamento de banco de dados, de modo que o desenvolvedor não precisa realizar nenhuma ação ou gravar código quando tiver sido configurado para um banco de dados do SQL Server. Além disso, o objeto <xref:System.Data.SqlClient.SqlConnection> oferece suporte a um modo de conexão explícita que permite fornecer o nome de um servidor de parceiro de failover no <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 A seguinte sequência simplificada de eventos ocorre para um objeto <xref:System.Data.SqlClient.SqlConnection> cujo alvo são um banco de dados configurado para espelhamento:  
  
1. O aplicativo cliente conecta-se com sucesso ao banco de dados principal e o servidor envia de volta o nome do servidor parceiro, que é armazenado em cache no cliente.  
  
2. Se o servidor que contém o banco de dados principal falhar ou a conectividade for interrompida, a conexão e o estado da transação serão perdidos. O aplicativo cliente tenta restabelecer uma conexão com o banco de dados principal e falha.  
  
3. O aplicativo cliente em seguida tenta de modo transparente estabelecer uma conexão com o banco de dados espelho no servidor parceiro. Se tiver êxito, a conexão será redirecionada para o banco de dados espelho, que então se torna o novo banco de dados principal.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Especificando o parceiro de failover na cadeia de conexão  
 Se você fornece o nome de um servidor de parceiro de failover na cadeia de conexão, o cliente tentará de modo transparente uma conexão com o parceiro de failover se o banco de dados principal ficar indisponível quando o aplicativo cliente for conectado primeiro.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Se você omitir o nome do servidor de parceiro de failover e o banco de dados principal ficar indisponível quando o aplicativo cliente é conectado primeiro, um <xref:System.Data.SqlClient.SqlException> é gerado.  
  
 Quando um <xref:System.Data.SqlClient.SqlConnection> é aberto com êxito, o nome do parceiro de failover é retornado pelo servidor e substitui todos os valores fornecidos na cadeia de conexão.  
  
> [!NOTE]
>  Você deve especificar explicitamente o catálogo inicial ou o nome do banco de dados na cadeia de conexão para cenários de espelhamento de banco de dados. Se o cliente receber informações de failover em uma conexão que não tem um catálogo inicial ou um banco de dados explicitamente especificado, as informações de failover não serão armazenadas em cache e o aplicativo não tentará realizar o failover se o servidor principal falhar. Se uma cadeia de conexão tiver um valor para o parceiro de failover, mas nenhum valor para o catálogo inicial ou banco de dados, um `InvalidArgumentException` será gerado.  
  
## <a name="retrieving-the-current-server-name"></a>Recuperando o nome do servidor atual  
 No caso de um failover, você poderá recuperar o nome do servidor ao qual a conexão atual está realmente conectada usando a propriedade <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> de um objeto <xref:System.Data.SqlClient.SqlConnection>. O fragmento de código a seguir recupera o nome do servidor ativo, supondo que a variável de conexão referencie uma <xref:System.Data.SqlClient.SqlConnection> aberta.  
  
 Quando ocorre um evento de failover e a conexão é alternado para o servidor espelho, o **fonte de dados** propriedade é atualizada para refletir o nome do espelho.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Comportamento de espelhamento SqlClient  
 O cliente sempre tenta se conectar ao servidor principal atual. Se ele falhar, tentará o parceiro de failover. Se o banco de dados espelho já tiver sido alternado para a função principal no servidor de parceiro, a conexão será bem-sucedida e o novo mapeamento da entidade de segurança espelho será enviado ao cliente e armazenado em cache para o tempo de vida do <xref:System.AppDomain> de chamada. Ele não é armazenado no armazenamento persistente e não está disponível para conexões subsequentes em um local diferente **AppDomain** ou processo. No entanto, ele está disponível para conexões subsequentes dentro do mesmo **AppDomain**. Observe que outro **AppDomain** ou processo em execução na mesma ou em um computador diferente sempre tem o pool de conexões, e essas conexões não são redefinidas. Nesse caso, se o banco de dados primário ficar inativo, cada processo ou **AppDomain** falhar uma vez e o pool será desmarcado automaticamente.  
  
> [!NOTE]
>  O suporte a espelhamento no servidor é configurado em cada banco de dados. Se as operações de manipulação de dados forem executadas em outros bancos de dados não incluídos no conjunto de entidade de segurança/espelho, usando nomes com várias partes ou alterando o banco de dados atual, as alterações feitas a esses outros bancos de dados não serão propagadas no caso de falha. Nenhum erro é gerado quando os dados são modificados em um banco de dados que não está espelhado. O desenvolvedor deve avaliar o impacto possível dessas operações.  
  
## <a name="database-mirroring-resources"></a>Recursos de espelhamento de banco de dados  
 Para a documentação conceitual e informações sobre como configurar, implantar e administrar o espelhamento, consulte os seguintes recursos na documentação do SQL Server.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|[Espelhamento de banco de dados](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Descreve como configurar o espelhamento no SQL Server.|  
  
## <a name="see-also"></a>Consulte também

- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
