---
title: Estabelecendo a conexão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 4606ecb370b7e85cf5ebd92754471f5253321251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149655"
---
# <a name="establishing-the-connection"></a>Estabelecendo a conexão
Para se conectar ao Microsoft SQL Server, use o objeto <xref:System.Data.SqlClient.SqlConnection> do provedor de dados .NET Framework para SQL Server. Para se conectar a uma fonte de dados OLE DB, use o objeto <xref:System.Data.OleDb.OleDbConnection> do provedor de dados .NET Framework para OLE DB. Para se conectar a uma fonte de dados ODBC, use o objeto <xref:System.Data.Odbc.OdbcConnection> do provedor de dados .NET Framework para ODBC. Para se conectar a uma fonte de dados Oracle, use o objeto <xref:System.Data.OracleClient.OracleConnection> do provedor de dados .NET Framework para Oracle. Para armazenar e recuperar com segurança as seqüências de conexão, consulte [Protegendo as informações de conexão](protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Fechando conexões  
 É recomendável sempre fechar a conexão quando você terminar de usá-la para que a conexão possa ser retornada ao pool. O bloco `Using` no Visual Basic ou C# automaticamente descarta a conexão quando o código sai do bloco, mesmo no caso de uma exceção sem tratamento. Consulte [o uso da Declaração](../../../csharp/language-reference/keywords/using-statement.md) e da [Declaração](../../../visual-basic/language-reference/statements/using-statement.md) para obter mais informações.  
  
 Você também pode usar os métodos `Close` ou `Dispose` do objeto de conexão para o provedor que você está usando. As conexões que não são fechadas explicitamente não podem ser adicionadas nem retornadas ao pool. Por exemplo, uma conexão que sai de escopo, mas que não foi fechada explicitamente será retornada somente para o pool de conexões se o tamanho do máximo tiver sido atingido e a conexão ainda estiver válida. Para obter mais informações, consulte [OLE DB, ODBC e Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Não ligue `Close` `Dispose` ou ligue para uma **conexão,** um **DataReader**ou qualquer outro objeto gerenciado no `Finalize` método de sua classe. Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente. Se a classe não tiver nenhum recurso não gerenciado, não inclua um método `Finalize` em sua definição de classe. Para obter mais informações, consulte [Coleta de Lixo](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Eventos de logon e logout não serão gerados no servidor quando uma conexão for procurada de ou retornada para o pool de conexões, porque a conexão não é fechada realmente quando é retornada para o pool de conexões. Para obter mais informações, consulte [Pool de Conexões do SQL Server (ADO.NET)](sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>Conectar-se ao SQL Server  
 O provedor de dados .NET Framework para SQL Server dá suporte a um formato de cadeia de conexão semelhante ao formato de cadeia de conexão OLE DB (ADO). Para obter nomes e valores válidos de formato de cadeia de caracteres, consulte a propriedade <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> do objeto <xref:System.Data.SqlClient.SqlConnection>. Você também pode usar a classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> para criar cadeias de conexão sintaticamente válidas em tempo de execução. Para obter mais informações, confira [Construtores de cadeias de conexão](connection-string-builders.md).  
  
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
  
 A identidade de segurança para aplicativos ASP.NET pode ser definida para uma das várias opções diferentes. Para entender melhor a identidade de segurança que um aplicativo ASP.NET usa ao se conectar ao SQL Server, consulte [ASP.NET impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))e [Como: Acessar o Servidor SQL usando o Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Conectando-se a uma fonte de dados do OLE DB  
 O .NET Framework Data Provider for OLE DB fornece conectividade a fontes de dados expostas usando o OLE DB (através do SQLOLEDB, o Provedor OLE DB para SQL Server), usando o objeto **OleDbConnection.**  
  
 Para o Provedor de Dados .NET Framework para OLE DB, o formato da cadeia de conexão é idêntico ao formato de cadeia de conexão usada no ADO, com as seguintes exceções:  
  
- A **palavra-chave Provedor** é necessária.  
  
- As palavras-chave **URL,** **Remote Provider**e **Remote Server** não são suportadas.  
  
 Para obter mais informações sobre cadeias de conexão do OLE DB, consulte o tópico <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>. Você também pode usar <xref:System.Data.OleDb.OleDbConnectionStringBuilder> para criar cadeias de conexão em tempo de execução.  
  
> [!NOTE]
> O objeto **OleDbConnection** não suporta a configuração ou a recuperação de propriedades dinâmicas específicas de um provedor OLE DB. Somente as propriedades que podem ser passadas na cadeia de conexão para o provedor OLE DB têm suporte.  
  
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
 É possível fornecer informações de conexão para um **OleDbConnection** em um arquivo UDL (Universal Data Link, link de dados universal); no entanto, você deve evitar fazê-lo. Os arquivos UDL não são criptografados e expõem as informações da cadeia de conexão em texto não criptografado. Como um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo, ele não poderá ser protegido usando o .NET Framework.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Conectando-se a uma fonte de dados do ODBC  
 O .NET Framework Data Provider for ODBC fornece conectividade a fontes de dados expostas usando o ODBC usando o objeto **OdbcConnection.**  
  
 Para o provedor de dados .NET Framework para ODBC, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão ODBC. Você também pode fornecer um nome (DSN) da fonte de dados ODBC. Para obter mais detalhes sobre o <xref:System.Data.Odbc.OdbcConnection> **OdbcConnection,** consulte o .  
  
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
 O .NET Framework Data Provider for Oracle fornece conectividade a fontes de dados Oracle usando o objeto **OracleConnection.**  
  
 Para o provedor de dados .NET Framework para Oracle, o formato de cadeia de conexão é criado para corresponder o máximo possível ao formato de cadeia de conexão do provedor OLE DB para Oracle (MSDAORA). Para obter mais detalhes sobre <xref:System.Data.OracleClient.OracleConnection>o **OracleConnection,** consulte o .  
  
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
  
## <a name="see-also"></a>Confira também

- [Conectando a uma Fonte de Dados](connecting-to-a-data-source.md)
- [Cadeias de conexão](connection-strings.md)
- [Conexão do Oracle, ODBC e OLE DB Pooling](ole-db-odbc-and-oracle-connection-pooling.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
