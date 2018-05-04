---
title: Consumir um conjunto de dados de um serviço Web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: da3eca875df9b80f66241a2ecb72c5ba5c1df309
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>Consumir um conjunto de dados de um serviço Web XML
O <xref:System.Data.DataSet> foi projetado com um design desconectado, em parte para facilitar o transporte conveniente de dados pela Internet. O **DataSet** é "serializável" em que ele pode ser especificado como uma entrada ou saída de serviços Web XML sem qualquer codificação adicional necessário para transmitir o conteúdo do **conjunto de dados** de um serviço Web XML para um cliente e vice-versa. O **DataSet** é convertido implicitamente em um fluxo XML usando o formato DiffGram, enviados pela rede e, em seguida, reconstruídos do fluxo XML como um **DataSet** na extremidade de recebimento. Isso fornece um método muito simples e flexível para transmitir e retornando dados relacionais usando serviços Web XML. Para obter mais informações sobre o formato DiffGram, consulte [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).  
  
 O exemplo a seguir mostra como criar um serviço Web XML e um cliente que usam o **DataSet** para transportar dados relacionais (incluindo dados modificados) e resolver todas as atualizações de volta para a fonte de dados original.  
  
> [!NOTE]
>  É recomendável que você sempre considerar as implicações de segurança ao criar um serviço Web XML. Para obter informações sobre como proteger um serviço Web XML, consulte [Protegendo XML Web Services criado usando ASP.NET](https://msdn.microsoft.com/library/354b2ab1-2782-4542-b32a-dc560178b90c).  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>Para criar um serviço Web XML que retorna e consome um conjunto de dados  
  
1.  Crie o serviço Web XML.  
  
     No exemplo, um serviço Web XML é criado que retorna os dados, nesse caso, uma lista de clientes da **Northwind** banco de dados e recebe um **conjunto de dados** com as atualizações para os dados que o serviço Web XML resolve volta para a fonte de dados original.  
  
     O serviço Web XML expõe dois métodos: **GetCustomers**para retornar a lista de clientes, e **UpdateCustomers**para resolver as atualizações de volta para a fonte de dados. O serviço Web XML é armazenado em um arquivo no servidor Web chamado DataSetSample.asmx. O código a seguir descreve o conteúdo de DataSetSample.asmx.  
  
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
  
     Em um cenário típico, o **UpdateCustomers** método seria escrito para capturar as violações de simultaneidade otimista. Para simplificar, o exemplo não inclui isso. Para obter mais informações sobre simultaneidade otimista, consulte [simultaneidade otimista](../../../../../docs/framework/data/adonet/optimistic-concurrency.md).  
  
2.  Crie um proxy de serviço da Web em XML.  
  
     Os clientes do serviço Web XML exigem um proxy SOAP para consumir os métodos expostos. Você pode fazer com que o Visual Studio gerar esse proxy para você. Definindo uma referência Web para um serviço da Web existente no Visual Studio, todo o comportamento descrito nesta etapa ocorre de forma transparente. Se você deseja criar a classe de proxy por conta própria, continue com esta discussão. Na maioria das circunstâncias, no entanto, usando o Visual Studio para criar a classe de proxy para o aplicativo cliente é suficiente.  
  
     Um proxy pode ser criado usando a ferramenta Web Services Description Language. Por exemplo, se o serviço Web XML é exposto na URL http://myserver/data/DataSetSample.asmx, emitir um comando, como o seguinte para criar um proxy do Visual Basic .NET com um namespace de **WebData.DSSample** e armazená-lo no arquivo Sample.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Para criar um proxy c# sample.cs o arquivo, execute o comando a seguir.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     O proxy pode ser compilado como uma biblioteca e importado para o cliente do serviço Web XML. Para compilar o código de proxy do Visual Basic .NET armazenado em Sample como sample.dll, execute o comando a seguir.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Para compilar o código de proxy c# armazenado em sample.cs como sample.dll, execute o comando a seguir.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3.  Crie um cliente de serviço da Web em XML.  
  
     Se você quiser que o Visual Studio gerar a classe de proxy de serviço da Web para você, simplesmente criar o projeto de cliente e, na janela do Gerenciador de soluções, clique com botão direito no projeto, clique em **adicionar referência Web**e selecione o serviço Web do a lista de serviços Web disponíveis (Isso pode exigir fornecendo o endereço do ponto de extremidade de serviço da Web, se o serviço Web não está disponível dentro da solução atual ou no computador atual.) Se você cria o proxy do serviço Web XML por conta própria (conforme descrito na etapa anterior), você pode importá-lo no seu código de cliente e consumir os métodos do serviço da Web em XML. O código de exemplo a seguir importa a biblioteca de proxy, chamadas **GetCustomers** obter uma lista de clientes, adiciona um novo cliente e, em seguida, retorna um **DataSet** com as atualizações **UpdateCustomers** .  
  
     Observe que o exemplo passa o **DataSet** retornado por **DataSet. GetChanges** para **UpdateCustomers** porque somente as linhas modificadas precisam ser passados para  **UpdateCustomers**. **UpdateCustomers** retorna o resolvido **DataSet**, que você pode, em seguida, **mesclar** em existente **DataSet** para incorporar as alterações resolvidas e qualquer informações de erro de linha da atualização. O código a seguir supõe que você usou o Visual Studio para criar a referência da Web e que você renomeou a referência Web para DsSample no **adicionar referência Web** caixa de diálogo.  
  
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
  
     Se você optar por criar a classe de proxy por conta própria, você deve tomar as seguintes etapas adicionais. Para compilar o exemplo, forneça a biblioteca de proxy foi criada (sample.dll) e as bibliotecas .NET relacionadas. Para compilar a versão do Visual Basic .NET de exemplo, armazenado no client.vb arquivo, execute o comando a seguir.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Para compilar a versão c# do exemplo, armazenado em client.cs arquivo, execute o comando a seguir.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)  
 [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)  
 [Parâmetros DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Ferramenta do Web Services Description Language (Wsdl.exe)](https://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
