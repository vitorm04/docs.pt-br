---
title: Obtendo um DbProviderFactory
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
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 379ec77c5a291ff0fcfa535b808f8976bb416d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="obtaining-a-dbproviderfactory"></a>Obtendo um DbProviderFactory
O processo de obter <xref:System.Data.Common.DbProviderFactory> envolve passar informações sobre um provedor de dados para a classe <xref:System.Data.Common.DbProviderFactories>. Com base nessas informações, o método <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> cria uma fábrica de provedor fortemente tipada. Por exemplo, para criar <xref:System.Data.SqlClient.SqlClientFactory>, você pode passar para `GetFactory` uma cadeia de caracteres com o nome do provedor especificado como “System.Data.SqlClient”. Outra sobrecarga de `GetFactory` utiliza <xref:System.Data.DataRow>. Uma vez que você criar a fábrica de provedor, poderá usar seus métodos para criar objetos adicionais. Alguns dos métodos de `SqlClientFactory` incluem <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> e <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  As classes <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory> e <xref:System.Data.OleDb.OleDbFactory> do .NET Framework também oferecem funcionalidade semelhante.  
  
## <a name="registering-dbproviderfactories"></a>Registrando DbProviderFactories  
 Cada provedor de dados .NET Framework que oferece suporte a uma classe de fábrica registra informações de configuração de **DbProviderFactories** seção o **Machine. config** arquivo no computador local. O fragmento do arquivo de configuração a seguir mostra a sintaxe e o formato para <xref:System.Data.SqlClient>.  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 O **invariável** atributo identifica o provedor de dados subjacente. Essa sintaxe de nomenclatura de três partes também é usada na criação de uma nova fábrica e para identificar o provedor em um arquivo de configuração de aplicativo, de forma que o nome do provedor, juntamente com a cadeia de conexão associada, possa ser recuperado em tempo de execução.  
  
## <a name="retrieving-provider-information"></a>Recuperando informações sobre provedor  
 Você pode recuperar informações sobre todos os provedores de dados instalados no computador local usando o método <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>. Ele retorna um <xref:System.Data.DataTable> chamado **DbProviderFactories** que contém as colunas descritas na tabela a seguir.  
  
|Ordinal de coluna|Nome da coluna|Saída de exemplo|Descrição|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Nome**|Provedor de Dados SqlClient|Nome legível do provedor de dados|  
|1|**Descrição**|Provedor de Dados .Net Framework para SqlServer|Descrição legível do provedor de dados|  
|2|**InvariantName**|System.Data.SqlClient|Nome que pode ser usado programaticamente para se referir ao provedor de dados|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version= 2.0.0.0, = neutral, PublicKeyToken=b77a5c561934e089|Nome totalmente qualificado da classe de fábrica, que contém informações suficientes para criar uma instância do objeto|  
  
 Essa `DataTable` pode ser usada para permitir que um usuário selecione uma <xref:System.Data.DataRow> em tempo de execução. A `DataRow` selecionada pode então ser passada para o método <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> para criar um <xref:System.Data.Common.DbProviderFactory> fortemente tipado. Uma <xref:System.Data.DataRow> selecionada pode ser passada para o método `GetFactory` para criar o objeto `DbProviderFactory` desejado.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Listando as classes de fábrica de provedor instaladas  
 Este exemplo demonstra como usar o método <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> para retornar uma <xref:System.Data.DataTable> que contém informações sobre os provedores instalados. O código itera por cada linha na `DataTable`, exibindo informações para cada provedor instalado na janela do console.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Usando arquivos de configuração de aplicativo para armazenar informações da fábrica  
 O padrão de design usado para trabalhar com as fábricas envolve armazenar informações de cadeia de caracteres de provedor e conexão em um arquivo de configuração do aplicativo, como **App. config** para um aplicativo do Windows, e **Web. config**  para um aplicativo ASP.NET.  
  
 O fragmento de arquivo de configuração a seguir demonstra como salvar duas cadeias de conexão nomeadas: “NorthwindSQL” para uma conexão com o banco de dados Northwind no SQL Server e “NorthwindAccess” para uma conexão com o banco de dados Northwind no Access/Jet. O **invariável** nome é usado para o **providerName** atributo.  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Recuperando uma cadeia de conexão por nome de provedor  
 Para criar uma fábrica de provedor, você deve fornecer uma cadeia de conexão e o nome do provedor. Este exemplo demonstra como recuperar uma cadeia de caracteres de conexão de um arquivo de configuração do aplicativo, passando o nome do provedor no formato invariável "*System.Data.ProviderName*". O código itera por <xref:System.Configuration.ConnectionStringSettingsCollection>. Ele retorna <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> em caso de êxito; caso contrário, `null` (`Nothing` no Visual Basic). Se houver várias entradas para um provedor, a primeira encontrada será retornada. Para obter mais informações e exemplos de recuperar cadeias de caracteres de conexão de arquivos de configuração, consulte [cadeias de caracteres de Conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Uma referência a `System.Configuration.dll` é necessária para que o código seja executado.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Criando DbProviderFactory e DbConnection  
 Este exemplo demonstra como criar um <xref:System.Data.Common.DbProviderFactory> e <xref:System.Data.Common.DbConnection> objeto, passando-o nome do provedor no formato "*System.Data.ProviderName*" e uma cadeia de caracteres de conexão. Um objeto `DbConnection` é retornado em caso de êxito; e `null` (`Nothing` no Visual Basic) é retornado em caso de erro.  
  
 O código obtém `DbProviderFactory` chamando <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Em seguida, o método <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> cria o objeto <xref:System.Data.Common.DbConnection>, e a propriedade <xref:System.Data.Common.DbConnection.ConnectionString%2A> é definida como a cadeia de conexão.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Usando as Classes de configuração](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
