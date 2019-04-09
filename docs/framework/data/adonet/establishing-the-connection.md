---
title: Estabelecendo a conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 7f8cca02e673339e892c16e0de99e20accdfd404
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142331"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="5813a-102">Estabelecendo a conexão</span><span class="sxs-lookup"><span data-stu-id="5813a-102">Establishing the Connection</span></span>
<span data-ttu-id="5813a-103">Para se conectar ao Microsoft SQL Server, use o objeto <xref:System.Data.SqlClient.SqlConnection> do provedor de dados .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5813a-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="5813a-104">Para se conectar a uma fonte de dados OLE DB, use o objeto <xref:System.Data.OleDb.OleDbConnection> do provedor de dados .NET Framework para OLE DB.</span><span class="sxs-lookup"><span data-stu-id="5813a-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="5813a-105">Para se conectar a uma fonte de dados ODBC, use o objeto <xref:System.Data.Odbc.OdbcConnection> do provedor de dados .NET Framework para ODBC.</span><span class="sxs-lookup"><span data-stu-id="5813a-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="5813a-106">Para se conectar a uma fonte de dados Oracle, use o objeto <xref:System.Data.OracleClient.OracleConnection> do provedor de dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="5813a-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="5813a-107">Para armazenar com segurança e recuperação de cadeias de conexão, consulte [protegendo informações de Conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="5813a-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="5813a-108">Fechando conexões</span><span class="sxs-lookup"><span data-stu-id="5813a-108">Closing Connections</span></span>  
 <span data-ttu-id="5813a-109">É recomendável sempre fechar a conexão quando você terminar de usá-la para que a conexão possa ser retornada ao pool.</span><span class="sxs-lookup"><span data-stu-id="5813a-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="5813a-110">O bloco `Using` no Visual Basic ou C# automaticamente descarta a conexão quando o código sai do bloco, mesmo no caso de uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="5813a-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="5813a-111">Ver [usando a instrução](~/docs/csharp/language-reference/keywords/using-statement.md) e [instrução Using](~/docs/visual-basic/language-reference/statements/using-statement.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5813a-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="5813a-112">Você também pode usar os métodos `Close` ou `Dispose` do objeto de conexão para o provedor que você está usando.</span><span class="sxs-lookup"><span data-stu-id="5813a-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="5813a-113">As conexões que não são fechadas explicitamente não podem ser adicionadas nem retornadas ao pool.</span><span class="sxs-lookup"><span data-stu-id="5813a-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="5813a-114">Por exemplo, uma conexão que sai de escopo, mas que não foi fechada explicitamente será retornada somente para o pool de conexões se o tamanho do máximo tiver sido atingido e a conexão ainda estiver válida.</span><span class="sxs-lookup"><span data-stu-id="5813a-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="5813a-115">Para obter mais informações, consulte [Pooling de Conexão do Oracle, ODBC e OLE DB](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="5813a-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5813a-116">Não chame `Close` ou `Dispose` em um **Conexão**, um **DataReader**, ou qualquer outro objeto gerenciado no `Finalize` método de sua classe.</span><span class="sxs-lookup"><span data-stu-id="5813a-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="5813a-117">Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente.</span><span class="sxs-lookup"><span data-stu-id="5813a-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="5813a-118">Se a classe não tiver nenhum recurso não gerenciado, não inclua um método `Finalize` em sua definição de classe.</span><span class="sxs-lookup"><span data-stu-id="5813a-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="5813a-119">Para obter mais informações, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="5813a-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5813a-120">Eventos de logon e logout não serão gerados no servidor quando uma conexão for procurada de ou retornada para o pool de conexões, porque a conexão não é fechada realmente quando é retornada para o pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="5813a-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="5813a-121">Para obter mais informações, confira [Pooling de conexão do SQL Server (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="5813a-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="5813a-122">Conectando-se ao SQL Server</span><span class="sxs-lookup"><span data-stu-id="5813a-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="5813a-123">O provedor de dados .NET Framework para SQL Server dá suporte a um formato de cadeia de conexão semelhante ao formato de cadeia de conexão OLE DB (ADO).</span><span class="sxs-lookup"><span data-stu-id="5813a-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="5813a-124">Para obter nomes e valores válidos de formato de cadeia de caracteres, consulte a propriedade <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> do objeto <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="5813a-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="5813a-125">Você também pode usar a classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão sintaticamente válidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5813a-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="5813a-126">Para obter mais informações, confira [Construtores de cadeias de conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="5813a-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="5813a-127">O exemplo de código a seguir demonstra como criar e abrir uma conexão para um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5813a-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="5813a-128">Segurança integrada e o ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5813a-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="5813a-129">A segurança integrada do SQL Server (também conhecida como conexões confiáveis) ajuda a fornecer a proteção ao se conectar com o SQL Server porque ele não expõe uma identificação de usuário e uma senha na cadeia de conexão e é o método recomendado para autenticar uma conexão.</span><span class="sxs-lookup"><span data-stu-id="5813a-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="5813a-130">A segurança integrada usa a identidade de segurança atual, ou símbolo, do processo em execução.</span><span class="sxs-lookup"><span data-stu-id="5813a-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="5813a-131">Para aplicativos desktop, isso é geralmente a identidade do usuário conectado no momento.</span><span class="sxs-lookup"><span data-stu-id="5813a-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="5813a-132">A identidade de segurança para aplicativos ASP.NET pode ser definida para uma das várias opções diferentes.</span><span class="sxs-lookup"><span data-stu-id="5813a-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="5813a-133">Para entender melhor a identidade de segurança que um aplicativo ASP.NET usa ao se conectar ao SQL Server, consulte [personificação do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [autenticação do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), e [como: Segurança integrada de acessar o SQL Server usando o Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5813a-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="5813a-134">Conectando-se a uma fonte de dados do OLE DB</span><span class="sxs-lookup"><span data-stu-id="5813a-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="5813a-135">O .NET Framework Data Provider para OLE DB fornece conectividade a fontes de dados expostas usando OLE DB (por meio de SQLOLEDB, o provedor OLE DB para SQL Server), usando o **OleDbConnection** objeto.</span><span class="sxs-lookup"><span data-stu-id="5813a-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="5813a-136">Para o Provedor de Dados .NET Framework para OLE DB, o formato da cadeia de conexão é idêntico ao formato de cadeia de conexão usada no ADO, com as seguintes exceções:</span><span class="sxs-lookup"><span data-stu-id="5813a-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="5813a-137">O **provedor** palavra-chave é necessária.</span><span class="sxs-lookup"><span data-stu-id="5813a-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="5813a-138">O **URL**, **provedor remoto**, e **servidor remoto** palavras-chave não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5813a-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="5813a-139">Para obter mais informações sobre cadeias de conexão do OLE DB, consulte o tópico <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5813a-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="5813a-140">Você também pode usar <xref:System.Data.OleDb.OleDbConnectionStringBuilder> para criar cadeias de conexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5813a-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5813a-141">O **OleDbConnection** objeto não oferece suporte à configuração ou recuperação de propriedades dinâmicas específicas para um provedor OLE DB.</span><span class="sxs-lookup"><span data-stu-id="5813a-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="5813a-142">Somente as propriedades que podem ser passadas na cadeia de conexão para o provedor OLE DB têm suporte.</span><span class="sxs-lookup"><span data-stu-id="5813a-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="5813a-143">O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados OLE DB.</span><span class="sxs-lookup"><span data-stu-id="5813a-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="5813a-144">Não use arquivos UDL (Universal Data Link)</span><span class="sxs-lookup"><span data-stu-id="5813a-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="5813a-145">É possível fornecer informações de conexão para um **OleDbConnection** em um arquivo de Universal Data Link (UDL); no entanto você deve evitar fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5813a-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="5813a-146">Os arquivos UDL não são criptografados e expõem as informações da cadeia de conexão em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="5813a-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="5813a-147">Como um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo, ele não poderá ser protegido usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5813a-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="5813a-148">Conectando-se a uma fonte de dados do ODBC</span><span class="sxs-lookup"><span data-stu-id="5813a-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="5813a-149">O .NET Framework Data Provider para ODBC fornece conectividade a fontes de dados expostas usando ODBC usando o **OdbcConnection** objeto.</span><span class="sxs-lookup"><span data-stu-id="5813a-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="5813a-150">Para o provedor de dados .NET Framework para ODBC, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão ODBC.</span><span class="sxs-lookup"><span data-stu-id="5813a-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="5813a-151">Você também pode fornecer um nome (DSN) da fonte de dados ODBC.</span><span class="sxs-lookup"><span data-stu-id="5813a-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="5813a-152">Para obter mais detalhes sobre o **OdbcConnection** , consulte o <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="5813a-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="5813a-153">O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados ODBC.</span><span class="sxs-lookup"><span data-stu-id="5813a-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="5813a-154">Conectando-se a uma fonte de dados do Oracle</span><span class="sxs-lookup"><span data-stu-id="5813a-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="5813a-155">O provedor de dados do .NET Framework para Oracle fornece conectividade a fontes de dados Oracle usando o **OracleConnection** objeto.</span><span class="sxs-lookup"><span data-stu-id="5813a-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="5813a-156">Para o provedor de dados .NET Framework para Oracle, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão do provedor OLE DB para Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="5813a-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="5813a-157">Para obter mais detalhes sobre o **OracleConnection**, consulte o <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="5813a-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="5813a-158">O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados Oracle.</span><span class="sxs-lookup"><span data-stu-id="5813a-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="5813a-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5813a-159">See also</span></span>

- [<span data-ttu-id="5813a-160">Conectando a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="5813a-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="5813a-161">Cadeias de caracteres de conexão</span><span class="sxs-lookup"><span data-stu-id="5813a-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="5813a-162">OLE DB, ODBC e pool de conexões Oracle</span><span class="sxs-lookup"><span data-stu-id="5813a-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="5813a-163">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="5813a-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
