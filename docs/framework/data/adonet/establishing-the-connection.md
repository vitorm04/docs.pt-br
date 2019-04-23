---
title: Estabelecendo a conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 7f8cca02e673339e892c16e0de99e20accdfd404
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142331"
---
# <a name="establishing-the-connection"></a>Estabelecendo a conexão
Para se conectar ao Microsoft SQL Server, use o objeto <xref:System.Data.SqlClient.SqlConnection> do provedor de dados .NET Framework para SQL Server. Para se conectar a uma fonte de dados OLE DB, use o objeto <xref:System.Data.OleDb.OleDbConnection> do provedor de dados .NET Framework para OLE DB. Para se conectar a uma fonte de dados ODBC, use o objeto <xref:System.Data.Odbc.OdbcConnection> do provedor de dados .NET Framework para ODBC. Para se conectar a uma fonte de dados Oracle, use o objeto <xref:System.Data.OracleClient.OracleConnection> do provedor de dados .NET Framework para Oracle. Para armazenar com segurança e recuperação de cadeias de conexão, consulte [protegendo informações de Conexão](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Fechando conexões  
 É recomendável sempre fechar a conexão quando você terminar de usá-la para que a conexão possa ser retornada ao pool. O bloco `Using` no Visual Basic ou C# automaticamente descarta a conexão quando o código sai do bloco, mesmo no caso de uma exceção sem tratamento. Ver [usando a instrução](~/docs/csharp/language-reference/keywords/using-statement.md) e [instrução Using](~/docs/visual-basic/language-reference/statements/using-statement.md) para obter mais informações.  
  
 Você também pode usar os métodos `Close` ou `Dispose` do objeto de conexão para o provedor que você está usando. As conexões que não são fechadas explicitamente não podem ser adicionadas nem retornadas ao pool. Por exemplo, uma conexão que sai de escopo, mas que não foi fechada explicitamente será retornada somente para o pool de conexões se o tamanho do máximo tiver sido atingido e a conexão ainda estiver válida. Para obter mais informações, consulte [Pooling de Conexão do Oracle, ODBC e OLE DB](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Não chame `Close` ou `Dispose` em um **Conexão**, um **DataReader**, ou qualquer outro objeto gerenciado no `Finalize` método de sua classe. Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente. Se a classe não tiver nenhum recurso não gerenciado, não inclua um método `Finalize` em sua definição de classe. Para obter mais informações, consulte [coleta de lixo](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Eventos de logon e logout não serão gerados no servidor quando uma conexão for procurada de ou retornada para o pool de conexões, porque a conexão não é fechada realmente quando é retornada para o pool de conexões. Para obter mais informações, confira [Pooling de conexão do SQL Server (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Conectando-se ao SQL Server  
 O provedor de dados .NET Framework para SQL Server dá suporte a um formato de cadeia de conexão semelhante ao formato de cadeia de conexão OLE DB (ADO). Para obter nomes e valores válidos de formato de cadeia de caracteres, consulte a propriedade <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> do objeto <xref:System.Data.SqlClient.SqlConnection>. Você também pode usar a classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão sintaticamente válidas em tempo de execução. Para obter mais informações, confira [Construtores de cadeias de conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 O exemplo de código a seguir demonstra como criar e abrir uma conexão para um banco de dados do SQL Server.  
  
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
  
### <a name="integrated-security-and-aspnet"></a>Segurança integrada e o ASP.NET  
 A segurança integrada do SQL Server (também conhecida como conexões confiáveis) ajuda a fornecer a proteção ao se conectar com o SQL Server porque ele não expõe uma identificação de usuário e uma senha na cadeia de conexão e é o método recomendado para autenticar uma conexão. A segurança integrada usa a identidade de segurança atual, ou símbolo, do processo em execução. Para aplicativos desktop, isso é geralmente a identidade do usuário conectado no momento.  
  
 A identidade de segurança para aplicativos ASP.NET pode ser definida para uma das várias opções diferentes. Para entender melhor a identidade de segurança que um aplicativo ASP.NET usa ao se conectar ao SQL Server, consulte [personificação do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [autenticação do ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), e [como: Segurança integrada de acessar o SQL Server usando o Windows](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Conectando-se a uma fonte de dados do OLE DB  
 O .NET Framework Data Provider para OLE DB fornece conectividade a fontes de dados expostas usando OLE DB (por meio de SQLOLEDB, o provedor OLE DB para SQL Server), usando o **OleDbConnection** objeto.  
  
 Para o Provedor de Dados .NET Framework para OLE DB, o formato da cadeia de conexão é idêntico ao formato de cadeia de conexão usada no ADO, com as seguintes exceções:  
  
-   O **provedor** palavra-chave é necessária.  
  
-   O **URL**, **provedor remoto**, e **servidor remoto** palavras-chave não têm suporte.  
  
 Para obter mais informações sobre cadeias de conexão do OLE DB, consulte o tópico <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>. Você também pode usar <xref:System.Data.OleDb.OleDbConnectionStringBuilder> para criar cadeias de conexão em tempo de execução.  
  
> [!NOTE]
>  O **OleDbConnection** objeto não oferece suporte à configuração ou recuperação de propriedades dinâmicas específicas para um provedor OLE DB. Somente as propriedades que podem ser passadas na cadeia de conexão para o provedor OLE DB têm suporte.  
  
 O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados OLE DB.  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a>Não use arquivos UDL (Universal Data Link)  
 É possível fornecer informações de conexão para um **OleDbConnection** em um arquivo de Universal Data Link (UDL); no entanto você deve evitar fazer isso. Os arquivos UDL não são criptografados e expõem as informações da cadeia de conexão em texto não criptografado. Como um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo, ele não poderá ser protegido usando o .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Conectando-se a uma fonte de dados do ODBC  
 O .NET Framework Data Provider para ODBC fornece conectividade a fontes de dados expostas usando ODBC usando o **OdbcConnection** objeto.  
  
 Para o provedor de dados .NET Framework para ODBC, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão ODBC. Você também pode fornecer um nome (DSN) da fonte de dados ODBC. Para obter mais detalhes sobre o **OdbcConnection** , consulte o <xref:System.Data.Odbc.OdbcConnection>.  
  
 O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados ODBC.  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a>Conectando-se a uma fonte de dados do Oracle  
 O provedor de dados do .NET Framework para Oracle fornece conectividade a fontes de dados Oracle usando o **OracleConnection** objeto.  
  
 Para o provedor de dados .NET Framework para Oracle, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão do provedor OLE DB para Oracle (MSDAORA). Para obter mais detalhes sobre o **OracleConnection**, consulte o <xref:System.Data.OracleClient.OracleConnection>.  
  
 O exemplo de código a seguir demonstra como criar e abrir uma conexão para uma fonte de dados Oracle.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)
- [Conexão do Oracle, ODBC e OLE DB Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
