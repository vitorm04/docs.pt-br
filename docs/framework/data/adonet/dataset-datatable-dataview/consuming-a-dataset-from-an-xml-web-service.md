---
title: Consumir um DataSet de um serviço Web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: 5f28179b43cb0af2d75e9e5b13783bc7287c8886
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784775"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a><span data-ttu-id="719de-102">Consumir um DataSet de um serviço Web XML</span><span class="sxs-lookup"><span data-stu-id="719de-102">Consuming a DataSet from an XML Web Service</span></span>
<span data-ttu-id="719de-103">O <xref:System.Data.DataSet> foi arquitetado com um design desconectado, em parte, para facilitar o transporte conveniente de dados pela Internet.</span><span class="sxs-lookup"><span data-stu-id="719de-103">The <xref:System.Data.DataSet> was architected with a disconnected design, in part to facilitate the convenient transport of data over the Internet.</span></span> <span data-ttu-id="719de-104">O **conjunto** de dados é "serializável", pois pode ser especificado como uma entrada ou saída de Web Services XML sem qualquer codificação adicional necessária para transmitir o conteúdo do **conjunto** de dados de um serviço Web XML para um cliente e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="719de-104">The **DataSet** is "serializable" in that it can be specified as an input to or output from XML Web services without any additional coding required to stream the contents of the **DataSet** from an XML Web service to a client and back.</span></span> <span data-ttu-id="719de-105">O **conjunto** de linha de os é implicitamente convertido em um fluxo XML usando o formato DiffGram, enviado pela rede e, em seguida, reconstruído a partir do fluxo XML como um **conjunto** de uma base de recebimentos.</span><span class="sxs-lookup"><span data-stu-id="719de-105">The **DataSet** is implicitly converted to an XML stream using the DiffGram format, sent over the network, and then reconstructed from the XML stream as a **DataSet** on the receiving end.</span></span> <span data-ttu-id="719de-106">Isso fornece um método muito simples e flexível para transmissão e retorno de dados relacionais usando Web Services XML.</span><span class="sxs-lookup"><span data-stu-id="719de-106">This gives you a very simple and flexible method for transmitting and returning relational data using XML Web services.</span></span> <span data-ttu-id="719de-107">Para obter mais informações sobre o formato DiffGram, consulte [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="719de-107">For more information about the DiffGram format, see [DiffGrams](diffgrams.md).</span></span>  
  
 <span data-ttu-id="719de-108">O exemplo a seguir mostra como criar um serviço Web XML e um cliente que usam o **conjunto** de dados para transportar (incluindo dados modificados) e resolver quaisquer atualizações de volta para a fonte de dados original.</span><span class="sxs-lookup"><span data-stu-id="719de-108">The following example shows how to create an XML Web service and client that use the **DataSet** to transport relational data (including modified data) and resolve any updates back to the original data source.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="719de-109">É recomendável que você sempre considere as implicações de segurança ao criar um serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="719de-109">We recommend that you always consider security implications when creating an XML Web service.</span></span> <span data-ttu-id="719de-110">Para obter informações sobre como proteger um serviço Web XML, consulte [protegendo Web Services XML criados usando ASP.net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="719de-110">For information on securing an XML Web service, see [Securing XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).</span></span>  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a><span data-ttu-id="719de-111">Para criar um serviço Web XML que retorna e consome um DataSet</span><span class="sxs-lookup"><span data-stu-id="719de-111">To create an XML Web service that returns and consumes a DataSet</span></span>  
  
1. <span data-ttu-id="719de-112">Crie o serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="719de-112">Create the XML Web service.</span></span>  
  
     <span data-ttu-id="719de-113">No exemplo, é criado um serviço Web XML que retorna dados, neste caso, uma lista de clientes do banco de dados **Northwind** e recebe um conjunto de um **DataSet** com atualizações para os dados, que o serviço Web XML resolve de volta para a fonte de dado original.</span><span class="sxs-lookup"><span data-stu-id="719de-113">In the example, an XML Web service is created that returns data, in this case a list of customers from the **Northwind** database, and receives a **DataSet** with updates to the data, which the XML Web service resolves back to the original data source.</span></span>  
  
     <span data-ttu-id="719de-114">O Web Service XML expõe dois métodos: **GetCustomers**, para retornar a lista de Customers e **UpdateCustomers**, para resolver atualizações de volta para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="719de-114">The XML Web service exposes two methods: **GetCustomers**, to return the list of customers, and **UpdateCustomers**, to resolve updates back to the data source.</span></span> <span data-ttu-id="719de-115">O serviço Web XML é armazenado em um arquivo no servidor Web chamado DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="719de-115">The XML Web service is stored in a file on the Web server called DataSetSample.asmx.</span></span> <span data-ttu-id="719de-116">O código a seguir descreve o conteúdo de DataSetSample. asmx.</span><span class="sxs-lookup"><span data-stu-id="719de-116">The following code outlines the contents of DataSetSample.asmx.</span></span>  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     <span data-ttu-id="719de-117">Em um cenário típico, o método **UpdateCustomers** seria escrito para capturar violações de simultaneidade otimistas.</span><span class="sxs-lookup"><span data-stu-id="719de-117">In a typical scenario, the **UpdateCustomers** method would be written to catch optimistic concurrency violations.</span></span> <span data-ttu-id="719de-118">Para simplificar, o exemplo não inclui isso.</span><span class="sxs-lookup"><span data-stu-id="719de-118">For simplicity, the example does not include this.</span></span> <span data-ttu-id="719de-119">Para obter mais informações sobre simultaneidade otimista, consulte [simultaneidade otimista](../optimistic-concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="719de-119">For more information about optimistic concurrency, see [Optimistic Concurrency](../optimistic-concurrency.md).</span></span>  
  
2. <span data-ttu-id="719de-120">Crie um proxy de serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="719de-120">Create an XML Web service proxy.</span></span>  
  
     <span data-ttu-id="719de-121">Os clientes do serviço Web XML exigem um proxy SOAP para consumir os métodos expostos.</span><span class="sxs-lookup"><span data-stu-id="719de-121">Clients of the XML Web service require a SOAP proxy in order to consume the exposed methods.</span></span> <span data-ttu-id="719de-122">Você pode fazer com que o Visual Studio gere esse proxy para você.</span><span class="sxs-lookup"><span data-stu-id="719de-122">You can have Visual Studio generate this proxy for you.</span></span> <span data-ttu-id="719de-123">Ao definir uma referência Web para um serviço Web existente de dentro do Visual Studio, todo o comportamento descrito nesta etapa ocorre de forma transparente.</span><span class="sxs-lookup"><span data-stu-id="719de-123">By setting a Web reference to an existing Web service from within Visual Studio, all the behavior described in this step occurs transparently.</span></span> <span data-ttu-id="719de-124">Se você quiser criar a classe proxy por conta própria, continue com esta discussão.</span><span class="sxs-lookup"><span data-stu-id="719de-124">If you want to create the proxy class yourself, continue with this discussion.</span></span> <span data-ttu-id="719de-125">No entanto, na maioria das circunstâncias, o uso do Visual Studio para criar a classe de proxy para o aplicativo cliente é suficiente.</span><span class="sxs-lookup"><span data-stu-id="719de-125">In most circumstances, however, using Visual Studio to create the proxy class for the client application is sufficient.</span></span>  
  
     <span data-ttu-id="719de-126">Um proxy pode ser criado usando a ferramenta de linguagem de descrição de serviços Web.</span><span class="sxs-lookup"><span data-stu-id="719de-126">A proxy can be created using the Web Services Description Language Tool.</span></span> <span data-ttu-id="719de-127">Por exemplo, se o serviço Web XML for exposto na URL `http://myserver/data/DataSetSample.asmx`, emita um comando como o seguinte para criar um Visual Basic proxy .NET com um namespace de **WebData. DSSample** e armazená-lo no arquivo Sample. vb.</span><span class="sxs-lookup"><span data-stu-id="719de-127">For example, if the XML Web service is exposed at the URL `http://myserver/data/DataSetSample.asmx`, issue a command such as the following to create a Visual Basic .NET proxy with a namespace of **WebData.DSSample** and store it in the file sample.vb.</span></span>  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="719de-128">Para criar um C# proxy no arquivo Sample.cs, emita o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-128">To create a C# proxy in the file sample.cs, issue the following command.</span></span>  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     <span data-ttu-id="719de-129">O proxy pode então ser compilado como uma biblioteca e importado para o cliente do serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="719de-129">The proxy can then be compiled as a library and imported into the XML Web service client.</span></span> <span data-ttu-id="719de-130">Para compilar o Visual Basic código de proxy .NET armazenado em Sample. vb como Sample. dll, emita o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-130">To compile the Visual Basic .NET proxy code stored in sample.vb as sample.dll, issue the following command.</span></span>  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     <span data-ttu-id="719de-131">Para compilar o C# código de proxy armazenado em Sample.cs como Sample. dll, emita o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-131">To compile the C# proxy code stored in sample.cs as sample.dll, issue the following command.</span></span>  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. <span data-ttu-id="719de-132">Criar um cliente de serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="719de-132">Create an XML Web service client.</span></span>  
  
     <span data-ttu-id="719de-133">Se você quiser que o Visual Studio gere a classe proxy do serviço Web para você, simplesmente crie o projeto cliente e, na janela Gerenciador de Soluções, clique com o botão direito do mouse no projeto, clique em **Adicionar referência Web**e selecione o serviço Web na lista de Web disponíveis serviços (isso pode exigir o fornecimento do endereço do ponto de extremidade do serviço Web, se o serviço Web não estiver disponível na solução atual ou no computador atual). Se você mesmo criar o proxy do Web Service XML (conforme descrito na etapa anterior), você poderá importá-lo para o código do cliente e consumir os métodos do Web Service XML.</span><span class="sxs-lookup"><span data-stu-id="719de-133">If you want to have Visual Studio generate the Web service proxy class for you, simply create the client project, and, in the Solution Explorer window, right-click the project, click **Add Web Reference**, and select the Web service from the list of available Web services (this may require supplying the address of the Web service endpoint, if the Web service isn't available within the current solution, or on the current computer.) If you create the XML Web service proxy yourself (as described in the previous step), you can import it into your client code and consume the XML Web service methods.</span></span> <span data-ttu-id="719de-134">O código de exemplo a seguir importa a biblioteca de proxy, chama **GetCustomers** para obter uma lista de clientes, adiciona um novo Customer e, em seguida, retorna um **DataSet** com as atualizações para **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="719de-134">The following sample code imports the proxy library, calls **GetCustomers** to get a list of customers, adds a new customer, and then returns a **DataSet** with the updates to **UpdateCustomers**.</span></span>  
  
     <span data-ttu-id="719de-135">Observe que o exemplo passa o **conjunto** de registros retornado por **DataSet. GetChanges** para **UpdateCustomers** porque apenas as linhas modificadas precisam ser passadas para **UpdateCustomers**.</span><span class="sxs-lookup"><span data-stu-id="719de-135">Notice that the example passes the **DataSet** returned by **DataSet.GetChanges** to **UpdateCustomers** because only modified rows need to be passed to **UpdateCustomers**.</span></span> <span data-ttu-id="719de-136">**UpdateCustomers** retorna o **conjunto**de dados resolvido, que você pode **mesclar** no **conjunto** de dados existente para incorporar as alterações resolvidas e as informações de erro de linha da atualização.</span><span class="sxs-lookup"><span data-stu-id="719de-136">**UpdateCustomers** returns the resolved **DataSet**, which you can then **Merge** into the existing **DataSet** to incorporate the resolved changes and any row error information from the update.</span></span> <span data-ttu-id="719de-137">O código a seguir pressupõe que você usou o Visual Studio para criar a referência Web e que você renomeou a referência Web para DsSample na caixa de diálogo **Adicionar referência Web** .</span><span class="sxs-lookup"><span data-stu-id="719de-137">The following code assumes that you have used Visual Studio to create the Web reference, and that you have renamed the Web reference to DsSample in the **Add Web Reference** dialog box.</span></span>  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     <span data-ttu-id="719de-138">Se você decidir criar a classe proxy por conta própria, deverá executar as etapas adicionais a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-138">If you decide to create the proxy class yourself, you must take the following extra steps.</span></span> <span data-ttu-id="719de-139">Para compilar o exemplo, forneça a biblioteca de proxy que foi criada (Sample. dll) e as bibliotecas do .NET relacionadas.</span><span class="sxs-lookup"><span data-stu-id="719de-139">To compile the sample, supply the proxy library that was created (sample.dll) and the related .NET libraries.</span></span> <span data-ttu-id="719de-140">Para compilar a versão Visual Basic .NET do exemplo, armazenado no arquivo client. vb, emita o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-140">To compile the Visual Basic .NET version of the sample, stored in the file client.vb, issue the following command.</span></span>  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     <span data-ttu-id="719de-141">Para compilar a C# versão do exemplo, armazenado no arquivo client.cs, emita o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="719de-141">To compile the C# version of the sample, stored in the file client.cs, issue the following command.</span></span>  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="719de-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="719de-142">See also</span></span>

- [<span data-ttu-id="719de-143">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="719de-143">ADO.NET</span></span>](../index.md)
- <span data-ttu-id="719de-144">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="719de-144">[DataSets, DataTables, and DataViews](index.md)</span></span>
- [<span data-ttu-id="719de-145">DataTables</span><span class="sxs-lookup"><span data-stu-id="719de-145">DataTables</span></span>](datatables.md)
- <span data-ttu-id="719de-146">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)</span><span class="sxs-lookup"><span data-stu-id="719de-146">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md)</span></span>
- <span data-ttu-id="719de-147">[Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="719de-147">[Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md)</span></span>
- [<span data-ttu-id="719de-148">Parâmetros DataAdapter</span><span class="sxs-lookup"><span data-stu-id="719de-148">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- <span data-ttu-id="719de-149">[Ferramenta de linguagem de descrição de serviços Web (WSDL. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="719de-149">[Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))</span></span>
- <span data-ttu-id="719de-150">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="719de-150">[ADO.NET Overview](../ado-net-overview.md)</span></span>
