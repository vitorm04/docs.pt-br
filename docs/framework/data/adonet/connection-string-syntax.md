---
title: Sintaxe da cadeia de conexão
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4ec2b8a0a478f59ca66f8699e7846004a3a409cf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583609"
---
# <a name="connection-string-syntax"></a>Sintaxe da cadeia de conexão
Cada provedor de dados .NET Framework tem um objeto de `Connection` que herda de <xref:System.Data.Common.DbConnection> bem como de uma propriedade <xref:System.Data.Common.DbConnection.ConnectionString%2A> específica do provedor. A sintaxe específica da cadeia de conexão para cada provedor está documentada em sua propriedade `ConnectionString`. A tabela a seguir lista os quatro provedores de dados que estão incluídos no .NET Framework.  
  
|Provedor de dados .NET Framework|Descrição|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Fornece acesso a dados para o Microsoft SQL Server. Para obter mais informações sobre a sintaxe da cadeia de conexão, consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|Fornece acesso a dados para as fontes de dados expostas usando OLE DB. Para obter mais informações sobre a sintaxe da cadeia de conexão, consulte <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|Fornece acesso a dados para as fontes de dados expostas usando ODBC. Para obter mais informações sobre a sintaxe da cadeia de conexão, consulte <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Fornece acesso a dados para Oracle versão 8.1.7 ou posterior. Para obter mais informações sobre a sintaxe da cadeia de conexão, consulte <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Construtores de cadeia de conexão  
 O ADO.NET 2.0 introduziu os seguintes construtores de cadeia de conexão para provedores de dados .NET Framework.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Os construtores de cadeia de conexão permitem que você construa cadeias de conexão sintaticamente válidas em tempo de execução, para que você não tenha que manualmente concatenar os valores de cadeia de conexão no seu código. Para obter mais informações, confira [Construtores de cadeias de conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).  

## <a name="windows-authentication"></a>Autenticação do Windows  
 É recomendável usar a autenticação do Windows (também conhecido como *a segurança integrada*) para se conectar a fontes de dados que dão suporte a ele. A sintaxe empregada na cadeia de conexão varia de acordo com o provedor. A tabela a seguir mostra a sintaxe de Autenticação do Windows usada com os provedores de dados .NET Framework.  
  
|Provider|Sintaxe|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  O `Integrated Security=true` gera uma exceção quando usado com o provedor `OleDb`.  
  
## <a name="sqlclient-connection-strings"></a>Cadeias de conexão do SqlClient  
A sintaxe para uma cadeia de conexão <xref:System.Data.SqlClient.SqlConnection> está documentada na propriedade <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>. Você pode usar a propriedade <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> para obter ou definir uma cadeia de conexão para um banco de dados do SQL Server. Se você precisar de conexão a uma versão anterior do SQL Server, você deve usar o provedor de dados .NET Framework para OleDb (<xref:System.Data.OleDb>). A maioria das palavras-chave de cadeia de conexão também mapeiam para as propriedades no <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
>  A configuração padrão para o `Persist Security Info` palavra-chave é `false`. Configurá-lo como `true` ou `yes` permite informações confidenciais de segurança, incluindo a identificação de usuário e a senha, para serem obtidas da conexão depois que ela tiver sido aberta. Manter `Persist Security Info` definido como `false` para garantir que uma fonte não confiável não tem acesso às informações de cadeia de caracteres de conexão confidenciais.  

### <a name="windows-authentication-with-sqlclient"></a>Autenticação do Windows com o SqlClient 
 Cada uma das seguintes formas de sintaxe usa a autenticação do Windows para conectar-se para o **AdventureWorks** banco de dados em um servidor local.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>Autenticação do SQL Server com o SqlClient   
 A Autenticação do Windows é preferencial para se conectar ao SQL Server. No entanto, se a Autenticação do SQL Server for necessária, use a seguinte sintaxe para especificar um nome de usuário e uma senha. Nesse exemplo, os asteriscos são usados para representar um nome de usuário e uma senha válidos.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Quando você se conectar ao banco de dados SQL ou ao Azure SQL Data Warehouse e fornecer um logon no formato `user@servername`, certifique-se de que o `servername` valor no logon corresponde ao valor fornecido para `Server=`.

> [!NOTE]
>  A autenticação do Windows tem precedência sobre logons do SQL Server. Se você especificar Integrated Security=true assim como um nome de usuário e uma senha, o nome de usuário e a senha serão ignorados e a autenticação do Windows será usada.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Conectar-se a uma instância nomeada do SQL Server
Para se conectar a uma instância nomeada do SQL Server, use o *nome do servidor name\instance.* sintaxe.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Você também pode definir a propriedade <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> de `SqlConnectionStringBuilder` para o nome da instância ao criar uma cadeia de conexão. A propriedade <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> de um objeto <xref:System.Data.SqlClient.SqlConnection> é somente leitura.  
  
### <a name="type-system-version-changes"></a>Alterações de versão do sistema de tipos  
 O `Type System Version` palavra-chave em um <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> Especifica a representação do lado do cliente de tipos do SQL Server. Consulte <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> para obter mais informações sobre a palavra-chave `Type System Version`.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Conectando e anexando a instâncias de usuário do SQL Server Express  
 As instâncias de usuário são um recurso no SQL Server Express. Elas permitem que um usuário que esteja executando uma conta local do Windows com menos privilégios anexe e execute um banco de dados do SQL Server sem exigir privilégios administrativos. Uma instância de usuário é executada com as credenciais do Windows do usuário, não como um serviço.  
  
 Para obter mais informações sobre como trabalhar com instâncias de usuário, consulte [instâncias do SQL Server Express usuário](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>Usando TrustServerCertificate  
 O `TrustServerCertificate` palavra-chave é válida somente ao se conectar a uma instância do SQL Server com um certificado válido. Quando `TrustServerCertificate` estiver definido como `true`, a camada de transporte usará SSL para criptografar o canal e não precisar passar pela verificação da cadeia do certificado para validar a confiança.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Se `TrustServerCertificate` estiver definido como `true` e a criptografia estiver ativada, o nível de criptografia especificado no servidor será usado mesmo que `Encrypt` esteja definido como `false` na cadeia de conexão. A conexão falhará se isso for feito de outra maneira.  
  
### <a name="enabling-encryption"></a>Ativando a criptografia  
 Para habilitar a criptografia quando um certificado não tiver sido provisionado no servidor, o **Forçar criptografia de protocolo** e o **confiar em certificado do servidor** opções devem ser definidas no SQL Server Configuration Manager. Nesse caso, a criptografia usará um certificado do servidor autoassinado sem validação se nenhum certificado verificável tiver sido provisionado no servidor.  
  
 As configurações do aplicativo não podem reduzir o nível de segurança configurado no SQL Server, mas podem opcionalmente reforçá-lo. Um aplicativo pode solicitar a criptografia definindo a `TrustServerCertificate` e `Encrypt` palavras-chave para `true`, garantindo que a criptografia ocorra mesmo quando um certificado de servidor não tiver sido provisionado e **Forçar criptografia de protocolo**  não foi configurado para o cliente. No entanto, se `TrustServerCertificate` não estiver ativado na configuração do cliente, um certificado do servidor provisionado ainda será necessário.  
  
 A tabela a seguir descreve todos os casos.  
  
|Configuração do cliente de Forçar Criptografia de Protocolo|Configuração do cliente de Certificado do Servidor de Confiança|Criptografar/Usar criptografia para a cadeia de conexão/atributo de dados|Cadeia de conexão/atributo do Certificado do Servidor de Confiança|Resultado|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Não|N/D|Não (padrão)|Ignorado|Não ocorre criptografia.|  
|Não|N/D|Sim|Não (padrão)|A criptografia ocorrerá somente se houver um certificado de servidor verificável; caso contrário, a tentativa de conexão falhará.|  
|Não|N/D|Sim|Sim|Criptografia sempre ocorre, mas pode usar um certificado de servidor autoassinado.|  
|Sim|Não|Ignorado|Ignorado|A criptografia ocorre somente se houver um certificado de servidor verificável; Caso contrário, a tentativa de conexão falhará.|  
|Sim|Sim|Não (padrão)|Ignorado|Criptografia sempre ocorre, mas pode usar um certificado de servidor autoassinado.|  
|Sim|Sim|Sim|Não (padrão)|A criptografia ocorre somente se houver um certificado de servidor verificável; Caso contrário, a tentativa de conexão falhará.|  
|Sim|Sim|Sim|Sim|Criptografia sempre ocorre, mas pode usar um certificado de servidor autoassinado.|  
  
 Para obter mais informações, consulte [usando criptografia sem validação](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>Cadeias de conexão do OleDb  
 A propriedade <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> de um <xref:System.Data.OleDb.OleDbConnection> permite que você obtenha ou defina uma cadeia de conexão para uma fonte de dados do OLE DB, como o Microsoft Access. Você também pode criar uma cadeia de conexão `OleDb` em tempo de execução usando a classe <xref:System.Data.OleDb.OleDbConnectionStringBuilder>.  
  
### <a name="oledb-connection-string-syntax"></a>Sintaxe da cadeia de conexão OleDb  
 Você deve especificar um nome de provedor para uma cadeia de conexão <xref:System.Data.OleDb.OleDbConnection>. A seguinte cadeia de conexão conecta-se a um banco de dados do Microsoft Access usando o provedor Jet. Observe que as palavras-chave `User ID` e `Password` serão opcionais se o banco de dados for inseguro (o padrão).  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Se o banco de dados Jet estiver protegido usando a segurança de nível de usuário, você deverá fornecer o local do arquivo de informações do grupo de trabalho (.mdw). O arquivo de informações do grupo de trabalho é usado para validar as credenciais apresentadas na cadeia de conexão.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  É possível fornecer informações de conexão para um **OleDbConnection** em um arquivo de Universal Data Link (UDL); no entanto você deve evitar fazer isso. Os arquivos UDL não são criptografados e expõem as informações da cadeia de conexão em texto não criptografado. Como um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo, ele não poderá ser protegido usando o .NET Framework. Arquivos UDL não têm suporte para **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Usando DataDirectory para conectar-se ao Access/Jet  
 `DataDirectory` não é exclusivo para `SqlClient`. Ele também pode ser usado com os provedores de dados <xref:System.Data.OleDb> e <xref:System.Data.Odbc> do .NET. A cadeia de caracteres de exemplo <xref:System.Data.OleDb.OleDbConnection> a seguir demonstra a sintaxe necessária para se conectar ao Northwind.mdb localizado na pasta app_data do aplicativo. O banco de dados do sistema (System.mdw) também é armazenado nesse local.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Especificar o local do banco de dados do sistema na cadeia de conexão não será necessário se o banco de dados Access/Jet for inseguro. A segurança é desativada por padrão, com todos os usuários que se conectam como o usuário Admin interno com uma senha em branco. Mesmo quando a segurança em nível de usuário estiver implementada corretamente, um banco de dados Jet permanecerá vulnerável ao ataque. Portanto, armazenar informações confidenciais em um banco de dados Access/Jet não é recomendado devido à fraqueza inerente de seu esquema de segurança baseado em arquivo.  
  
### <a name="connecting-to-excel"></a>Conectando ao Excel  
 O provedor Microsoft Jet é usado para conectar-se a uma pasta de trabalho do Excel. Na cadeia de conexão a seguir, a palavra-chave de `Extended Properties` define as propriedades que são específicas do Excel. "HDR = Yes;" indica que a primeira linha contém nomes de coluna, não dados, e "IMEX=1 = 1;" informa o driver para ler sempre colunas de dados "misturadas" como texto.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Observe que o caractere de aspas duplas necessário para as `Extended Properties` também deve estar entre aspas duplas.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Sintaxe da cadeia de conexão do provedor de forma de dados  
 Use as palavras-chave `Provider` e `Data Provider` ao usar o provedor Microsoft Data Shape. O exemplo a seguir usa o provedor Shape para se conectar a uma instância local do SQL Server.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Cadeias de conexão do Odbc  
 A propriedade <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> de um <xref:System.Data.Odbc.OdbcConnection> permite obter ou definir uma cadeia de conexão para uma fonte de dados do OLE DB. As cadeias de conexão de Odbc também têm suporte pelo <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 A cadeia de conexão a seguir usa o Microsoft Text Driver.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Usando DataDirectory para conectar-se ao Visual FoxPro  
 O exemplo a seguir da cadeia de conexão <xref:System.Data.Odbc.OdbcConnection> demonstra o uso do `DataDirectory` para se conectar a um arquivo do Microsoft Visual FoxPro.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Cadeias de conexão do Oracle  
 A propriedade <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> de um <xref:System.Data.OracleClient.OracleConnection> permite obter ou definir uma cadeia de conexão para uma fonte de dados do OLE DB. As cadeias de conexão de Oracle também têm suporte pelo <xref:System.Data.OracleClient.OracleConnectionStringBuilder>.  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 Para obter mais informações sobre a sintaxe da cadeia de conexão ODBC, consulte <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Consulte também

- [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)
- [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
