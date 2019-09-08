---
title: Detectando alterações com SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 3719188064388b00c756dd037d4a475ca6debd13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782426"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="9552a-102">Detectando alterações com SqlDependency</span><span class="sxs-lookup"><span data-stu-id="9552a-102">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="9552a-103">Um objeto <xref:System.Data.SqlClient.SqlDependency> pode ser associado a um <xref:System.Data.SqlClient.SqlCommand> para detectar quando resultados de consulta diferem daqueles recuperados originalmente.</span><span class="sxs-lookup"><span data-stu-id="9552a-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="9552a-104">Você também pode atribuir um delegado para o evento `OnChange`, que será disparado quando os resultados forem alterados para um comando associado.</span><span class="sxs-lookup"><span data-stu-id="9552a-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="9552a-105">Você deve associar o <xref:System.Data.SqlClient.SqlDependency> ao comando antes de executá-lo.</span><span class="sxs-lookup"><span data-stu-id="9552a-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="9552a-106">A propriedade `HasChanges` do <xref:System.Data.SqlClient.SqlDependency> também pode ser usada para determinar se os resultados da consulta foram alterados desde a primeira recuperação dos dados.</span><span class="sxs-lookup"><span data-stu-id="9552a-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="9552a-107">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="9552a-107">Security Considerations</span></span>

<span data-ttu-id="9552a-108">A infraestrutura de dependência se baseia em um <xref:System.Data.SqlClient.SqlConnection> que é aberto quando <xref:System.Data.SqlClient.SqlDependency.Start%2A> é chamado para receber notificações de que os dados subjacentes foram alterados para determinado comando.</span><span class="sxs-lookup"><span data-stu-id="9552a-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="9552a-109">A capacidade de um cliente iniciar a chamada para `SqlDependency.Start` é controlada pelo uso de <xref:System.Data.SqlClient.SqlClientPermission> e por atributos de segurança de acesso a código.</span><span class="sxs-lookup"><span data-stu-id="9552a-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="9552a-110">Para obter mais informações, consulte [habilitando notificações de consulta](enabling-query-notifications.md) e [segurança de acesso de código e ADO.net](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="9552a-110">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="9552a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9552a-111">Example</span></span>

<span data-ttu-id="9552a-112">As seguintes etapas ilustram como declarar uma dependência, executar um comando e receber uma notificação quando o conjunto de resultados é alterado:</span><span class="sxs-lookup"><span data-stu-id="9552a-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="9552a-113">Inicie uma conexão de `SqlDependency` ao servidor.</span><span class="sxs-lookup"><span data-stu-id="9552a-113">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="9552a-114">Crie objetos <xref:System.Data.SqlClient.SqlConnection> e <xref:System.Data.SqlClient.SqlCommand> para se conectar ao servidor e definir uma instrução Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="9552a-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="9552a-115">Crie um novo objeto `SqlDependency` ou use um existente, e associe-o ao objeto `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="9552a-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="9552a-116">Internamente, isso cria um objeto <xref:System.Data.Sql.SqlNotificationRequest> e associa-o ao objeto de comando, quando necessário.</span><span class="sxs-lookup"><span data-stu-id="9552a-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="9552a-117">Esta solicitação de notificação contém um identificador interno que identifica exclusivamente este objeto `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="9552a-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="9552a-118">Também inicia o ouvinte de cliente quando ele ainda não está ativo.</span><span class="sxs-lookup"><span data-stu-id="9552a-118">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="9552a-119">Assine um manipulador de eventos para o evento `OnChange` do objeto `SqlDependency`.</span><span class="sxs-lookup"><span data-stu-id="9552a-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="9552a-120">Execute o comando usando quaisquer dos métodos `Execute` do objeto `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="9552a-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="9552a-121">Como o comando é associado ao objeto de notificação, o servidor reconhece que ele deve gerar uma notificação e as informações de consulta apontarão para a fila de dependências.</span><span class="sxs-lookup"><span data-stu-id="9552a-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="9552a-122">Interrompa a conexão de `SqlDependency` ao servidor.</span><span class="sxs-lookup"><span data-stu-id="9552a-122">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="9552a-123">Se qualquer usuário subsequentemente alterar os dados subjacentes, o Microsoft SQL Server detectará que existe uma notificação pendente para essa alteração, e postará uma notificação que será processada e encaminhada ao cliente através do `SqlConnection` subjacente que foi criado chamando `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="9552a-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="9552a-124">O ouvinte de cliente recebe a mensagem de invalidação.</span><span class="sxs-lookup"><span data-stu-id="9552a-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="9552a-125">O ouvinte de cliente localiza o objeto `SqlDependency` associado e dispara o evento `OnChange`.</span><span class="sxs-lookup"><span data-stu-id="9552a-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="9552a-126">O fragmento de código a seguir mostra o padrão de design que você deve usar para criar um aplicativo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9552a-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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
        ' Maintain the refernce in a class member.
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
        // Maintain the reference in a class member.

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

## <a name="see-also"></a><span data-ttu-id="9552a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9552a-127">See also</span></span>

- [<span data-ttu-id="9552a-128">Notificações de consulta no SQL Server</span><span class="sxs-lookup"><span data-stu-id="9552a-128">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="9552a-129">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9552a-129">[ADO.NET Overview](../ado-net-overview.md)</span></span>
