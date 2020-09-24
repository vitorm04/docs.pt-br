---
title: Obtendo um DbProviderFactory
description: Saiba como obter um DbProviderFactory da classe DbProviderFactories para trabalhar com fontes de dados específicas no .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0bf95f1773c832a4666c1b33336f963b674052ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150733"
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="756a4-103">Obtendo um DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="756a4-103">Obtaining a DbProviderFactory</span></span>

<span data-ttu-id="756a4-104">O processo de obter <xref:System.Data.Common.DbProviderFactory> envolve passar informações sobre um provedor de dados para a classe <xref:System.Data.Common.DbProviderFactories>.</span><span class="sxs-lookup"><span data-stu-id="756a4-104">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="756a4-105">Com base nessas informações, o método <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> cria uma fábrica de provedor fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="756a4-105">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="756a4-106">Por exemplo, para criar <xref:System.Data.SqlClient.SqlClientFactory>, você pode passar para `GetFactory` uma cadeia de caracteres com o nome do provedor especificado como “System.Data.SqlClient”.</span><span class="sxs-lookup"><span data-stu-id="756a4-106">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="756a4-107">Outra sobrecarga de `GetFactory` utiliza <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="756a4-107">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="756a4-108">Uma vez que você criar a fábrica de provedor, poderá usar seus métodos para criar objetos adicionais.</span><span class="sxs-lookup"><span data-stu-id="756a4-108">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="756a4-109">Alguns dos métodos de `SqlClientFactory` incluem <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> e <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span><span class="sxs-lookup"><span data-stu-id="756a4-109">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="756a4-110">As classes <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory> e <xref:System.Data.OleDb.OleDbFactory> do .NET Framework também oferecem funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="756a4-110">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="756a4-111">Registrando DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="756a4-111">Registering DbProviderFactories</span></span>  

 <span data-ttu-id="756a4-112">Cada provedor de dados de .NET Framework que dá suporte a uma classe baseada em fábrica registra informações de configuração na seção **DbProviderFactories** do arquivo **machine.config** no computador local.</span><span class="sxs-lookup"><span data-stu-id="756a4-112">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="756a4-113">O fragmento do arquivo de configuração a seguir mostra a sintaxe e o formato para <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="756a4-113">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
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
  
 <span data-ttu-id="756a4-114">O atributo **invariável** identifica o provedor de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="756a4-114">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="756a4-115">Essa sintaxe de nomenclatura de três partes também é usada na criação de uma nova fábrica e para identificar o provedor em um arquivo de configuração de aplicativo, de forma que o nome do provedor, juntamente com a cadeia de conexão associada, possa ser recuperado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="756a4-115">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="756a4-116">Recuperando informações sobre provedor</span><span class="sxs-lookup"><span data-stu-id="756a4-116">Retrieving Provider Information</span></span>  

 <span data-ttu-id="756a4-117">Você pode recuperar informações sobre todos os provedores de dados instalados no computador local usando o método <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>.</span><span class="sxs-lookup"><span data-stu-id="756a4-117">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="756a4-118">Ele retorna um <xref:System.Data.DataTable> **DbProviderFactories** nomeado que contém as colunas descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="756a4-118">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="756a4-119">Ordinal de coluna</span><span class="sxs-lookup"><span data-stu-id="756a4-119">Column ordinal</span></span>|<span data-ttu-id="756a4-120">Nome da coluna</span><span class="sxs-lookup"><span data-stu-id="756a4-120">Column name</span></span>|<span data-ttu-id="756a4-121">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="756a4-121">Example output</span></span>|<span data-ttu-id="756a4-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="756a4-122">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="756a4-123">0</span><span class="sxs-lookup"><span data-stu-id="756a4-123">0</span></span>|<span data-ttu-id="756a4-124">**Nome**</span><span class="sxs-lookup"><span data-stu-id="756a4-124">**Name**</span></span>|<span data-ttu-id="756a4-125">Provedor de Dados SqlClient</span><span class="sxs-lookup"><span data-stu-id="756a4-125">SqlClient Data Provider</span></span>|<span data-ttu-id="756a4-126">Nome legível do provedor de dados</span><span class="sxs-lookup"><span data-stu-id="756a4-126">Readable name for the data provider</span></span>|  
|<span data-ttu-id="756a4-127">1</span><span class="sxs-lookup"><span data-stu-id="756a4-127">1</span></span>|<span data-ttu-id="756a4-128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="756a4-128">**Description**</span></span>|<span data-ttu-id="756a4-129">Provedor de Dados .Net Framework para SqlServer</span><span class="sxs-lookup"><span data-stu-id="756a4-129">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="756a4-130">Descrição legível do provedor de dados</span><span class="sxs-lookup"><span data-stu-id="756a4-130">Readable description of the data provider</span></span>|  
|<span data-ttu-id="756a4-131">2</span><span class="sxs-lookup"><span data-stu-id="756a4-131">2</span></span>|<span data-ttu-id="756a4-132">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="756a4-132">**InvariantName**</span></span>|<span data-ttu-id="756a4-133">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="756a4-133">System.Data.SqlClient</span></span>|<span data-ttu-id="756a4-134">Nome que pode ser usado programaticamente para se referir ao provedor de dados</span><span class="sxs-lookup"><span data-stu-id="756a4-134">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="756a4-135">3</span><span class="sxs-lookup"><span data-stu-id="756a4-135">3</span></span>|<span data-ttu-id="756a4-136">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="756a4-136">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="756a4-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version= 2.0.0.0, = neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="756a4-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="756a4-138">Nome totalmente qualificado da classe de fábrica, que contém informações suficientes para criar uma instância do objeto</span><span class="sxs-lookup"><span data-stu-id="756a4-138">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="756a4-139">Essa `DataTable` pode ser usada para permitir que um usuário selecione uma <xref:System.Data.DataRow> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="756a4-139">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="756a4-140">A `DataRow` selecionada pode então ser passada para o método <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> para criar um <xref:System.Data.Common.DbProviderFactory> fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="756a4-140">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="756a4-141">Uma <xref:System.Data.DataRow> selecionada pode ser passada para o método `GetFactory` para criar o objeto `DbProviderFactory` desejado.</span><span class="sxs-lookup"><span data-stu-id="756a4-141">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="756a4-142">Listando as classes de fábrica de provedor instaladas</span><span class="sxs-lookup"><span data-stu-id="756a4-142">Listing the Installed Provider Factory Classes</span></span>  

 <span data-ttu-id="756a4-143">Este exemplo demonstra como usar o método <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> para retornar uma <xref:System.Data.DataTable> que contém informações sobre os provedores instalados.</span><span class="sxs-lookup"><span data-stu-id="756a4-143">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="756a4-144">O código itera por cada linha na `DataTable`, exibindo informações para cada provedor instalado na janela do console.</span><span class="sxs-lookup"><span data-stu-id="756a4-144">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="756a4-145">Usando arquivos de configuração de aplicativo para armazenar informações da fábrica</span><span class="sxs-lookup"><span data-stu-id="756a4-145">Using Application Configuration Files to Store Factory Information</span></span>  

 <span data-ttu-id="756a4-146">O padrão de design usado para trabalhar com fábricas envolve o armazenamento de informações de cadeia de conexão e provedor em um arquivo de configuração de aplicativo, como **app.config** para um aplicativo do Windows e **web.config** para um aplicativo ASP.net.</span><span class="sxs-lookup"><span data-stu-id="756a4-146">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="756a4-147">O fragmento de arquivo de configuração a seguir demonstra como salvar duas cadeias de conexão nomeadas: “NorthwindSQL” para uma conexão com o banco de dados Northwind no SQL Server e “NorthwindAccess” para uma conexão com o banco de dados Northwind no Access/Jet.</span><span class="sxs-lookup"><span data-stu-id="756a4-147">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="756a4-148">O nome **invariável** é usado para o atributo **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="756a4-148">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="756a4-149">Recuperando uma cadeia de conexão por nome de provedor</span><span class="sxs-lookup"><span data-stu-id="756a4-149">Retrieving a Connection String by Provider Name</span></span>  

 <span data-ttu-id="756a4-150">Para criar uma fábrica de provedor, você deve fornecer uma cadeia de conexão e o nome do provedor.</span><span class="sxs-lookup"><span data-stu-id="756a4-150">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="756a4-151">Este exemplo demonstra como recuperar uma cadeia de conexão de um arquivo de configuração de aplicativo passando o nome do provedor no formato invariável "*System. Data. ProviderName*".</span><span class="sxs-lookup"><span data-stu-id="756a4-151">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="756a4-152">O código itera por <xref:System.Configuration.ConnectionStringSettingsCollection>.</span><span class="sxs-lookup"><span data-stu-id="756a4-152">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="756a4-153">Ele retorna <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> em caso de êxito; caso contrário, `null` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="756a4-153">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="756a4-154">Se houver várias entradas para um provedor, a primeira encontrada será retornada.</span><span class="sxs-lookup"><span data-stu-id="756a4-154">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="756a4-155">Para obter mais informações e exemplos de como recuperar cadeias de conexão de arquivos de configuração, consulte [cadeias de conexão e arquivos de configuração](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="756a4-155">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="756a4-156">Uma referência a `System.Configuration.dll` é necessária para que o código seja executado.</span><span class="sxs-lookup"><span data-stu-id="756a4-156">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="756a4-157">Criando DbProviderFactory e DbConnection</span><span class="sxs-lookup"><span data-stu-id="756a4-157">Creating the DbProviderFactory and DbConnection</span></span>  

 <span data-ttu-id="756a4-158">Este exemplo demonstra como criar um <xref:System.Data.Common.DbProviderFactory> objeto e <xref:System.Data.Common.DbConnection> passando-o o nome do provedor no formato "*System. Data. ProviderName*" e uma cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="756a4-158">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="756a4-159">Um objeto `DbConnection` é retornado em caso de êxito; e `null` (`Nothing` no Visual Basic) é retornado em caso de erro.</span><span class="sxs-lookup"><span data-stu-id="756a4-159">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="756a4-160">O código obtém `DbProviderFactory` chamando <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="756a4-160">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="756a4-161">Em seguida, o método <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> cria o objeto <xref:System.Data.Common.DbConnection>, e a propriedade <xref:System.Data.Common.DbConnection.ConnectionString%2A> é definida como a cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="756a4-161">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="756a4-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="756a4-162">See also</span></span>

- [<span data-ttu-id="756a4-163">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="756a4-163">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="756a4-164">Cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="756a4-164">Connection Strings</span></span>](connection-strings.md)
- <span data-ttu-id="756a4-165">[Usando as classes de configuração](/previous-versions/aspnet/ms228063(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="756a4-165">[Using the Configuration Classes](/previous-versions/aspnet/ms228063(v=vs.100))</span></span>
- [<span data-ttu-id="756a4-166">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="756a4-166">ADO.NET Overview</span></span>](ado-net-overview.md)
