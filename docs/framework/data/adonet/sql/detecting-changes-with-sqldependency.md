---
title: "Detectando alterações com SqlDependency"
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
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1d3fd662ace71d77a185cd996c05960d026ef691
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="detecting-changes-with-sqldependency"></a>Detectando alterações com SqlDependency
Um objeto <xref:System.Data.SqlClient.SqlDependency> pode ser associado a um <xref:System.Data.SqlClient.SqlCommand> para detectar quando resultados de consulta diferem daqueles recuperados originalmente. Você também pode atribuir um delegado para o evento `OnChange`, que será disparado quando os resultados forem alterados para um comando associado. Você deve associar o <xref:System.Data.SqlClient.SqlDependency> ao comando antes de executá-lo. A propriedade `HasChanges` do <xref:System.Data.SqlClient.SqlDependency> também pode ser usada para determinar se os resultados da consulta foram alterados desde a primeira recuperação dos dados.  
  
## <a name="security-considerations"></a>Considerações sobre segurança  
 A infraestrutura de dependência se baseia em um <xref:System.Data.SqlClient.SqlConnection> que é aberto quando <xref:System.Data.SqlClient.SqlDependency.Start%2A> é chamado para receber notificações de que os dados subjacentes foram alterados para determinado comando. A capacidade de um cliente iniciar a chamada para `SqlDependency.Start` é controlada pelo uso de <xref:System.Data.SqlClient.SqlClientPermission> e por atributos de segurança de acesso a código. Para obter mais informações, consulte [habilitar notificações de consulta](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) e [Code Access Security e ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Exemplo  
 As seguintes etapas ilustram como declarar uma dependência, executar um comando e receber uma notificação quando o conjunto de resultados é alterado:  
  
1.  Inicie uma conexão de `SqlDependency` ao servidor.  
  
2.  Crie objetos <xref:System.Data.SqlClient.SqlConnection> e <xref:System.Data.SqlClient.SqlCommand> para se conectar ao servidor e definir uma instrução Transact-SQL.  
  
3.  Crie um novo objeto `SqlDependency` ou use um existente, e associe-o ao objeto `SqlCommand`. Internamente, isso cria um objeto <xref:System.Data.Sql.SqlNotificationRequest> e associa-o ao objeto de comando, quando necessário. Esta solicitação de notificação contém um identificador interno que identifica exclusivamente este objeto `SqlDependency`. Também inicia o ouvinte de cliente quando ele ainda não está ativo.  
  
4.  Assine um manipulador de eventos para o evento `OnChange` do objeto `SqlDependency`.  
  
5.  Execute o comando usando quaisquer dos métodos `Execute` do objeto `SqlCommand`. Como o comando é associado ao objeto de notificação, o servidor reconhece que ele deve gerar uma notificação e as informações de consulta apontarão para a fila de dependências.  
  
6.  Interrompa a conexão de `SqlDependency` ao servidor.  
  
 Se qualquer usuário subsequentemente alterar os dados subjacentes, o Microsoft SQL Server detectará que existe uma notificação pendente para essa alteração, e postará uma notificação que será processada e encaminhada ao cliente através do `SqlConnection` subjacente que foi criado chamando `SqlDependency.Start`. O ouvinte de cliente recebe a mensagem de invalidação. O ouvinte de cliente localiza o objeto `SqlDependency` associado e dispara o evento `OnChange`.  
  
 O fragmento de código a seguir mostra o padrão de design que você deve usar para criar um aplicativo de exemplo.  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the refence in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Notificações de consulta no SQL Server](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
