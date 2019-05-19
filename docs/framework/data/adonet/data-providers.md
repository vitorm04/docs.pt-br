---
title: Provedores de dados .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: d343f7be3e26575ee9a1e9ccae9f17314db10ac5
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882115"
---
# <a name="net-framework-data-providers"></a>Provedores de dados .NET Framework
Um provedor de dados .NET Framework é usado para se conectar a um banco de dados, execução de comandos e recuperar resultados. Os resultados são processados diretamente, colocados no <xref:System.Data.DataSet> para serem expostos ao usuário conforme o necessário, combinados com os dados de várias fontes ou colocados remotamente entre camadas. Provedores de dados .NET framework são leves, criando uma camada mínima entre a fonte de dados e código, aumentando o desempenho sem sacrificar a funcionalidade.  
  
 A tabela a seguir lista os provedores de dados que estão incluídos no .NET Framework.  
  
|Provedor de dados .NET Framework|Descrição|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET framework Data Provider para SQL Server|Fornece acesso a dados para o Microsoft SQL Server. Usa o namespace <xref:System.Data.SqlClient>.|  
|Provedor de dados .NET Framework para OLE DB|Para fontes de dados expostas usando o OLE DB. Usa o namespace <xref:System.Data.OleDb>.|  
|Provedor de dados .NET Framework para ODBC|Para fontes de dados expostas usando ODBC. Usa o namespace <xref:System.Data.Odbc>.|  
|Provedor de Dados do .NET Framework para Oracle|Para fontes de dados Oracle. O .NET Framework Data Provider for Oracle dá suporte ao software cliente Oracle versão 8.1.7 e versões posteriores e usa o <xref:System.Data.OracleClient> namespace.|  
|Provedor EntityClient|Fornece acesso a dados para aplicativos de Modelo de Dados de Entidade (EDM). Usa o namespace <xref:System.Data.EntityClient>.|  
|.NET framework Data Provider para SQL Server Compact 4.0.|Fornece acesso a dados para o Microsoft SQL Server Compact 4.0. Usa o [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) namespace.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Os objetos principais de provedores de dados .NET Framework  
 A tabela a seguir descreve os quatro objetos principais que compõem um provedor de dados .NET Framework.  
  
|Objeto|Descrição|  
|------------|-----------------|  
|`Connection`|Estabelece uma conexão com uma fonte de dados específica. A classe base para todos os objetos de `Connection` é a classe <xref:System.Data.Common.DbConnection>.|  
|`Command`|Executa um comando em uma fonte de dados. Expõe `Parameters` e pode ser executado no escopo de uma `Transaction` de `Connection`. A classe base para todos os objetos de `Command` é a classe <xref:System.Data.Common.DbCommand>.|  
|`DataReader`|Ler um fluxo de dados apenas de encaminhamento e somente leitura de uma fonte de dados. A classe base para todos os objetos de `DataReader` é a classe <xref:System.Data.Common.DbDataReader>.|  
|`DataAdapter`|Preenche um `DataSet` e resolve atualizações com a fonte de dados. A classe base para todos os objetos de `DataAdapter` é a classe <xref:System.Data.Common.DbDataAdapter>.|  
  
 Além das classes principais listadas na tabela no início deste documento, um provedor de dados .NET Framework também contém as classes listadas na tabela a seguir.  
  
|Objeto|Descrição|  
|------------|-----------------|  
|`Transaction`|Insere comandos nas transações na fonte de dados. A classe base para todos os objetos de `Transaction` é a classe <xref:System.Data.Common.DbTransaction>. O ADO.NET também fornece suporte para transações usando classes no namespace <xref:System.Transactions>.|  
|`CommandBuilder`|Um objeto auxiliar que gera automaticamente propriedades de comando de um `DataAdapter` ou deriva informações de parâmetro de um procedimento armazenado e preenche a coleção `Parameters` de um objeto `Command`. A classe base para todos os objetos de `CommandBuilder` é a classe <xref:System.Data.Common.DbCommandBuilder>.|  
|`ConnectionStringBuilder`|Um objeto auxiliar que fornece uma maneira simples de criar e gerenciar o conteúdo de cadeias de conexão usadas por objetos de `Connection`. A classe base para todos os objetos de `ConnectionStringBuilder` é a classe <xref:System.Data.Common.DbConnectionStringBuilder>.|  
|`Parameter`|Define os parâmetros de valores de entrada, saída e retorno para comandos e procedimentos armazenados. A classe base para todos os objetos de `Parameter` é a classe <xref:System.Data.Common.DbParameter>.|  
|`Exception`|Retornado quando um erro é encontrado na fonte de dados. Um erro for encontrado no cliente, os provedores de dados .NET Framework lançar uma exceção do .NET Framework. A classe base para todos os objetos de `Exception` é a classe <xref:System.Data.Common.DbException>.|  
|`Error`|Expõe as informações de um aviso ou erro retornado por uma fonte de dados.|  
|`ClientPermission`|Fornecido para atributos de segurança de acesso de código do .NET Framework data provider. A classe base para todos os objetos de `ClientPermission` é a classe <xref:System.Data.Common.DBDataPermission>.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET framework Data Provider para SQL Server (SqlClient)  
 O .NET Framework Data Provider para SQL Server (SqlClient) usa seu próprio protocolo para se comunicar com o SQL Server. Ele é leve e executa bem porque é otimizado para acessar um SQL Server diretamente sem adicionar uma camada OLE DB ou ODBC Open Database Connectivity (). A ilustração a seguir contrasta o .NET Framework Data Provider para SQL Server com o .NET Framework Data Provider para OLE DB. O .NET Framework Data Provider para OLE DB comunica-se a uma fonte de dados OLE DB por meio do componente de serviço do OLE DB, que fornece pooling de conexão e os serviços de transação e o provedor OLE DB para a fonte de dados.  
  
> [!NOTE]
>  O .NET Framework Data Provider para ODBC tem uma arquitetura semelhante para o .NET Framework Data Provider para OLE DB; Por exemplo, ele chama um componente de serviço do ODBC.  
  
 ![Provedores de dados](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Comparação do Provedor de dados .NET Framework para SQL Server e o Provedor de dados .NET Framework para OLE DB  
  
 O .NET Framework Data Provider para classes do SQL Server estão localizados no <xref:System.Data.SqlClient> namespace.  
  
 O .NET Framework Data Provider para SQL Server dá suporte a transações locais e distribuídas. Para transações distribuídas, o .NET Framework Data Provider para SQL Server, por padrão, é o automaticamente a inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services ou <xref:System.Transactions>. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 O exemplo de código a seguir mostra como incluir o namespace `System.Data.SqlClient` em seus aplicativos.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Provedor de dados .NET Framework para OLE DB  
 O .NET Framework Data Provider para OLE DB (OleDb) usa OLE DB nativo por meio da interoperabilidade COM para habilitar o acesso a dados. O .NET Framework Data Provider para OLE DB dá suporte a transações locais e distribuídas. Para transações distribuídas, o .NET Framework Data Provider para OLE DB, por padrão, automaticamente inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 A tabela a seguir mostra os provedores que foram testados com o ADO.NET.  
  
|Driver|Provider|  
|------------|--------------|  
|SQLOLEDB|Provedor Microsoft OLE DB para SQL Server|  
|MSDAORA|Provedor do Microsoft OLE DB para Oracle|  
|Microsoft.Jet.OLEDB.4.0|Provedor do OLE DB para Microsoft Jet|  
  
> [!NOTE]
>  Não é recomendável usar um banco de dados do Access (Jet) como uma fonte de dados para aplicativos multithread, como aplicativos do ASP.NET. Se você precisar usar Jet como uma fonte de dados para um aplicativo ASP.NET, perceba que os aplicativos ASP.NET se conectar a um banco de dados do Access podem encontrar problemas de conexão.  
  
 O .NET Framework Data Provider para OLE DB não oferece suporte a interfaces do OLE DB versão 2.5. Provedores do OLE DB que exigem suporte para interfaces do OLE DB 2.5 não funcionará corretamente com o .NET Framework Data Provider para OLE DB. Isso inclui o provedor do Microsoft OLE DB para Exchange e o provedor do Microsoft OLE DB para publicação na Internet.  
  
 O .NET Framework Data Provider para OLE DB não funciona com o provedor OLE DB para ODBC (MSDASQL). Para acessar uma fonte de dados ODBC usando o ADO.NET, use o .NET Framework Data Provider para ODBC.  
  
 Provedor de dados do .NET framework para OLE DB classes estão localizados no <xref:System.Data.OleDb> namespace. O exemplo de código a seguir mostra como incluir o namespace `System.Data.OleDb` em seus aplicativos.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>Provedor de dados .NET Framework para ODBC  
 O .NET Framework Data Provider para ODBC (Odbc) usa o ODBC Driver Manager (DM) nativo para habilitar o acesso a dados. O provedor de dados do ODBC oferece suporte a transações locais e distribuídas. Para transações distribuídas, o Provedor de dados do ODBC, por padrão, automaticamente inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 A tabela a seguir mostra os drivers ODBC testados com o ADO.NET.  
  
|Driver|  
|------------|  
|SQL Server|  
|Microsoft ODBC para Oracle|  
|Driver do Microsoft Access (*.mdb)|  
  
 Provedor de dados do .NET framework para classes ODBC estão localizados no <xref:System.Data.Odbc> namespace.  
  
 O exemplo de código a seguir mostra como incluir o namespace `System.Data.Odbc` em seus aplicativos.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  O .NET Framework Data Provider para ODBC exige MDAC 2.6 ou posterior, e o MDAC 2.8 SP1 é recomendado. Você pode baixar o MDAC 2.8 SP1 do [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Provedor de Dados do .NET Framework para Oracle  
 O .NET Framework Data Provider for Oracle (OracleClient) permite o acesso de dados para fontes de dados Oracle por meio do software de conectividade de cliente Oracle. O provedor de dados oferece suporte a um software cliente do Oracle versão 8.1.7 ou posterior. O provedor de dados oferece suporte a transações locais e distribuídas. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 O .NET Framework Data Provider for Oracle requer o software cliente do Oracle (versão 8.1.7 ou posterior) no sistema antes que você pode se conectar a uma fonte de dados Oracle.  
  
 Provedor de dados do .NET framework para classes de Oracle estão localizados na <xref:System.Data.OracleClient> namespace e estão contidas no `System.Data.OracleClient.dll` assembly. Você deve fazer referência a `System.Data.dll` e a `System.Data.OracleClient.dll` ao criar um aplicativo que usa o provedor de dados.  
  
 O exemplo de código a seguir mostra como incluir o namespace `System.Data.OracleClient` em seus aplicativos.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Escolhendo um Provedor de dados .NET Framework  
 Dependendo da fonte de dados e design para o seu aplicativo, sua opção de provedor de dados .NET Framework pode melhorar o desempenho, capacidade e integridade do seu aplicativo. A tabela a seguir descreve as vantagens e limitações de cada provedor de dados .NET Framework.  
  
|Provider|Observações|  
|--------------|-----------|  
|.NET framework Data Provider para SQL Server|Recomendado para aplicativos de camada intermediária que usam o Microsoft SQL Server.<br /><br /> Recomendado para aplicativos de camada única que usam o Microsoft Database Engine (MSDE) ou SQL Server.<br /><br /> Recomendado durante o uso do provedor OLE DB para SQL Server (SQLOLEDB) com o .NET Framework Data Provider para OLE DB.|  
|Provedor de dados .NET Framework para OLE DB|Para SQL Server, o .NET Framework Data Provider para SQL Server é recomendado em vez desse provedor.<br /><br /> Recomendado para aplicativos de camada única que usam os bancos de dados Microsoft Access. O uso de um banco de dados Access para um aplicativo de camada intermediária não é recomendado.|  
|Provedor de dados .NET Framework para ODBC|Recomendado para aplicativos de camada única e intermediária que usam fontes de dados ODBC.|  
|Provedor de Dados do .NET Framework para Oracle|Recomendado para aplicativos de camada única e intermediária que usam fontes de dados Oracle.|  
  
## <a name="entityclient-provider"></a>Provedor EntityClient  
 O provedor EntityClient é usado para acessar dados com base no EDM (Modelo de Dados de Entidade). Diferentemente de outros provedores de dados .NET Framework, ele não interage diretamente com uma fonte de dados. Em vez disso, ele usa o Entity SQL para se comunicar com o provedor de dados subjacente. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)
- [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
