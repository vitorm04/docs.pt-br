---
title: Provedores de dados .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 529b7094ad36861cacc4009ea8faf152f056c20e
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066214"
---
# <a name="net-framework-data-providers"></a>Provedores de dados .NET Framework
Um provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é usado para se conectar a um banco de dados, executar comandos e recuperar resultados. Os resultados são processados diretamente, colocados no <xref:System.Data.DataSet> para serem expostos ao usuário conforme o necessário, combinados com os dados de várias fontes ou colocados remotamente entre camadas. Os provedores de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são leves, criando uma camada mínima entre a fonte de dados e o código, aumentando o desempenho sem sacrificar a funcionalidade.  
  
 A tabela a seguir lista os provedores de dados que estão incluídos no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]|Descrição|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para o SQL Server|Fornece acesso a dados para o Microsoft SQL Server. Usa o namespace <xref:System.Data.SqlClient>.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para OLE DB|Para fontes de dados expostas usando o OLE DB. Usa o namespace <xref:System.Data.OleDb>.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para ODBC|Para fontes de dados expostas usando ODBC. Usa o namespace <xref:System.Data.Odbc>.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para Oracle|Para fontes de dados Oracle. O provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle oferece suporte a um cliente de software Oracle versão 8.1.7 e posterior, e usa o namespace <xref:System.Data.OracleClient>.|  
|Provedor EntityClient|Fornece acesso a dados para aplicativos de Modelo de Dados de Entidade (EDM). Usa o namespace <xref:System.Data.EntityClient>.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para o SQL Server Compact 4.0.|Fornece acesso a dados para o Microsoft SQL Server Compact 4.0. Usa o [System.Data.SqlServerCe](https://msdn.microsoft.com/library/system.data.sqlserverce.aspx) namespace.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Os objetos principais de provedores de dados .NET Framework  
 A tabela a seguir descreve os quatro objetos principais que compõem um provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|Objeto|Descrição|  
|------------|-----------------|  
|`Connection`|Estabelece uma conexão com uma fonte de dados específica. A classe base para todos os objetos de `Connection` é a classe <xref:System.Data.Common.DbConnection>.|  
|`Command`|Executa um comando em uma fonte de dados. Expõe `Parameters` e pode ser executado no escopo de uma `Transaction` de `Connection`. A classe base para todos os objetos de `Command` é a classe <xref:System.Data.Common.DbCommand>.|  
|`DataReader`|Ler um fluxo de dados apenas de encaminhamento e somente leitura de uma fonte de dados. A classe base para todos os objetos de `DataReader` é a classe <xref:System.Data.Common.DbDataReader>.|  
|`DataAdapter`|Preenche um `DataSet` e resolve atualizações com a fonte de dados. A classe base para todos os objetos de `DataAdapter` é a classe <xref:System.Data.Common.DbDataAdapter>.|  
  
 Além das classes principais listadas na tabela anteriormente neste documento, um provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] também contém as classes listadas na tabela a seguir.  
  
|Objeto|Descrição|  
|------------|-----------------|  
|`Transaction`|Insere comandos nas transações na fonte de dados. A classe base para todos os objetos de `Transaction` é a classe <xref:System.Data.Common.DbTransaction>. O ADO.NET também fornece suporte para transações usando classes no namespace <xref:System.Transactions>.|  
|`CommandBuilder`|Um objeto auxiliar que gera automaticamente propriedades de comando de um `DataAdapter` ou deriva informações de parâmetro de um procedimento armazenado e preenche a coleção `Parameters` de um objeto `Command`. A classe base para todos os objetos de `CommandBuilder` é a classe <xref:System.Data.Common.DbCommandBuilder>.|  
|`ConnectionStringBuilder`|Um objeto auxiliar que fornece uma maneira simples de criar e gerenciar o conteúdo de cadeias de conexão usadas por objetos de `Connection`. A classe base para todos os objetos de `ConnectionStringBuilder` é a classe <xref:System.Data.Common.DbConnectionStringBuilder>.|  
|`Parameter`|Define os parâmetros de valores de entrada, saída e retorno para comandos e procedimentos armazenados. A classe base para todos os objetos de `Parameter` é a classe <xref:System.Data.Common.DbParameter>.|  
|`Exception`|Retornado quando um erro é encontrado na fonte de dados. Para um erro localizado no cliente, os provedores de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] geram uma exceção do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. A classe base para todos os objetos de `Exception` é a classe <xref:System.Data.Common.DbException>.|  
|`Error`|Expõe as informações de um aviso ou erro retornado por uma fonte de dados.|  
|`ClientPermission`|Fornecido para os atributos de segurança de acesso a código do provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. A classe base para todos os objetos de `ClientPermission` é a classe <xref:System.Data.Common.DBDataPermission>.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET framework Data Provider para SQL Server (SqlClient)  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados para o SQL Server (SqlClient) usa seu próprio protocolo para se comunicar com o SQL Server. Ele é leve e executa bem porque é otimizado para acessar um SQL Server diretamente sem adicionar uma camada OLE DB ou ODBC Open Database Connectivity (). A ilustração a seguir compara os [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB. O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB comunica-se com uma fonte de dados do OLE DB por meio do componente de serviço do OLE DB, que fornece serviços do pool de conexões e de transação, e do provedor OLE DB para a fonte de dados.  
  
> [!NOTE]
>  O provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC tem uma arquitetura semelhante ao Provedor de Dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB; por exemplo, ele chama em um componente de serviço de ODBC.  
  
 ![Provedores de dados](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Comparação do Provedor de dados .NET Framework para SQL Server e o Provedor de dados .NET Framework para OLE DB  
  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados para classes do SQL Server estão localizados no <xref:System.Data.SqlClient> namespace.  
  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server dá suporte a transações locais e distribuídas. Para transações distribuídas, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server, por padrão, automaticamente inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services ou <xref:System.Transactions>. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 O exemplo de código a seguir mostra como incluir o namespace `System.Data.SqlClient` em seus aplicativos.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Provedor de dados .NET Framework para OLE DB  
 O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB (OleDb) usa o OLE DB nativo por meio da interoperabilidade de COM para habilitar o acesso a dados. O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para o OLE DB oferece suporte a transações locais e distribuídas. Para transações distribuídas, o Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para o OLE DB, por padrão, automaticamente inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 A tabela a seguir mostra os provedores que foram testados com o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Driver|Provider|  
|------------|--------------|  
|SQLOLEDB|Provedor Microsoft OLE DB para SQL Server|  
|MSDAORA|Provedor do Microsoft OLE DB para Oracle|  
|Microsoft.Jet.OLEDB.4.0|Provedor do OLE DB para Microsoft Jet|  
  
> [!NOTE]
>  Usar um banco de dados Access (Jet) como uma fonte de dados para aplicativos com vários threads, como aplicativos do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], não é recomendado. Se você tiver que usar Jet como uma fonte de dados para um aplicativo do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], observe que os aplicativos do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] que estão se conectando a um banco de dados Access podem encontrar problemas de conexão.  
  
 O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB não oferece suporte a interfaces da versão 2.5 do OLE DB. Os Provedores do OLE DB que exigem suporte para interfaces do OLE DB 2.5 não funcionarão corretamente com o Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB. Isso inclui o provedor do Microsoft OLE DB para Exchange e o provedor do Microsoft OLE DB para publicação na Internet.  
  
 O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB não funciona com o provedor do OLE DB para ODBC (MSDASQL). Para acessar uma fonte de dados ODBC usando o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], use o Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC.  
  
 As classes do Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para OLE DB estão localizadas no namespace <xref:System.Data.OleDb>. O exemplo de código a seguir mostra como incluir o namespace `System.Data.OleDb` em seus aplicativos.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>Provedor de dados .NET Framework para ODBC  
 O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC usa o ODBC Driver Manager (DM) nativo para habilitar o acesso a dados. O provedor de dados do ODBC oferece suporte a transações locais e distribuídas. Para transações distribuídas, o Provedor de dados do ODBC, por padrão, automaticamente inscreve-se em uma transação e obtém detalhes de transação do Windows Component Services. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 A tabela a seguir mostra os drivers ODBC testados com o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Driver|  
|------------|  
|SQL Server|  
|Microsoft ODBC para Oracle|  
|Driver do Microsoft Access (*.mdb)|  
  
 As classes do Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC estão localizadas no namespace <xref:System.Data.Odbc>.  
  
 O exemplo de código a seguir mostra como incluir o namespace `System.Data.Odbc` em seus aplicativos.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para ODBC exige MDAC 2.6 ou posterior, e o MDAC 2.8 SP1 é recomendado. Você pode baixar o MDAC 2.8 SP1 do [Data Access and Storage Developer Center](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Provedor de Dados do .NET Framework para Oracle  
 O provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle (OracleClient) permite o acesso a dados a fontes de dados do Oracle por meio do software de conectividade de cliente da Oracle. O provedor de dados oferece suporte a um software cliente do Oracle versão 8.1.7 ou posterior. O provedor de dados oferece suporte a transações locais e distribuídas. Para obter mais informações, consulte [transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 O Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle exige o software cliente da Oracle (versão 8.1.7 ou posterior) no sistema antes que você possa se conectar a uma fonte de dados do Oracle.  
  
 As classes do Provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para Oracle estão localizadas no namespace <xref:System.Data.OracleClient> e estão contidas no assembly `System.Data.OracleClient.dll`. Você deve fazer referência a `System.Data.dll` e a `System.Data.OracleClient.dll` ao criar um aplicativo que usa o provedor de dados.  
  
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
 Dependendo do design e da fonte de dados para seu aplicativo, sua escolha do provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pode melhorar o desempenho, os recursos e a integridade do aplicativo. A tabela a seguir descreve as vantagens e as limitações de cada provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|Provider|Observações|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para o SQL Server|Recomendado para aplicativos de camada intermediária que usam o Microsoft SQL Server.<br /><br /> Recomendado para aplicativos de camada única que usam o Microsoft Database Engine (MSDE) ou SQL Server.<br /><br /> Recomendado sobre o uso do provedor OLE DB para SQL Server (SQLOLEDB) com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para OLE DB|Para o SQL Server, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server é recomendado em vez desse provedor.<br /><br /> Recomendado para aplicativos de camada única que usam os bancos de dados Microsoft Access. O uso de um banco de dados Access para um aplicativo de camada intermediária não é recomendado.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para ODBC|Recomendado para aplicativos de camada única e intermediária que usam fontes de dados ODBC.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provedor de dados para Oracle|Recomendado para aplicativos de camada única e intermediária que usam fontes de dados Oracle.|  
  
## <a name="entityclient-provider"></a>Provedor EntityClient  
 O provedor EntityClient é usado para acessar dados com base no EDM (Modelo de Dados de Entidade). Diferentemente de outros provedores de dados .NET Framework, ele não interage diretamente com uma fonte de dados. Em vez disso, ele usa o Entity SQL para se comunicar com o provedor de dados subjacente. Para obter mais informações, consulte [EntityClient e Entity SQL](https://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
## <a name="see-also"></a>Consulte também
- [ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)
- [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
