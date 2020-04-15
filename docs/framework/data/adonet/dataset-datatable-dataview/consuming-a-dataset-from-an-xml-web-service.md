---
title: Consumir um DataSet de um serviço Web XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: d7328949e3eb4822b1a645bb5f0c1866f01ecb0a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389743"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a>Consumir um DataSet a partir de um serviço web XML

O <xref:System.Data.DataSet> foi arquitetado com um design desconectado, em parte para facilitar o conveniente transporte de dados pela Internet. O **DataSet** é "serializável" na medida em que pode ser especificado como uma entrada ou saída de serviços Da Web XML sem qualquer codificação adicional necessária para transmitir o conteúdo do **DataSet** de um serviço Web XML para um cliente e de volta. O **DataSet** é implicitamente convertido em um fluxo XML usando o formato DiffGram, enviado pela rede e, em seguida, reconstruído a partir do fluxo XML como um **DataSet** na extremidade receptora. Isso lhe dá um método muito simples e flexível para transmitir e retornar dados relacionais usando serviços Da Web XML. Para obter mais informações sobre o formato DiffGram, consulte [DiffGrams](diffgrams.md).  
  
 O exemplo a seguir mostra como criar um serviço web XML e um cliente que usam o **DataSet** para transportar dados relacionais (incluindo dados modificados) e resolver quaisquer atualizações de volta à fonte de dados original.  
  
> [!NOTE]
> Recomendamos que você sempre considere implicações de segurança ao criar um serviço Web XML. Para obter informações sobre como proteger um serviço Web XML, consulte [Protegendo os Serviços Web XML criados usando ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>Crie um serviço web XML
  
1. Crie o serviço Web XML.  
  
     No exemplo, é criado um serviço Web XML que retorna dados, neste caso uma lista de clientes do banco de dados **Northwind,** e recebe um **DataSet** com atualizações para os dados, que o serviço Web XML resolve de volta à fonte de dados original.  
  
     O serviço Web XML expõe dois métodos: **GetCustomers**, para retornar a lista de clientes e **UpdateCustomers**, para resolver atualizações de volta à fonte de dados. O serviço Web XML é armazenado em um arquivo no servidor web chamado DataSetSample.asmx. O código a seguir descreve o conteúdo de DataSetSample.asmx.  
  
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
  
     Em um cenário típico, o método **UpdateCustomers** seria escrito para capturar violações de concorrência otimistas. Para simplificar, o exemplo não inclui isso. Para obter mais informações sobre a concorrência otimista, consulte [A Concorrência Otimista](../optimistic-concurrency.md).  
  
2. Crie um proxy de serviço Web XML.  
  
     Os clientes do serviço Web XML exigem um proxy SOAP para consumir os métodos expostos. Você pode fazer com que o Visual Studio gere esse proxy para você. Ao definir uma referência web a um serviço web existente de dentro do Visual Studio, todo o comportamento descrito nesta etapa ocorre de forma transparente. Se você quiser criar a classe proxy você mesmo, continue com essa discussão. Na maioria das circunstâncias, no entanto, usar o Visual Studio para criar a classe proxy para o aplicativo cliente é suficiente.  
  
     Um proxy pode ser criado usando a Ferramenta de Linguagem de Descrição de Serviços da Web. Por exemplo, se o serviço Da Web `http://myserver/data/DataSetSample.asmx`XML estiver exposto na URL, emita um comando como o seguinte para criar um proxy Visual Basic .NET com um namespace do **WebData.DSSample** e armazená-lo na amostra de arquivo.vb.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Para criar um proxy C# no arquivo sample.cs, emita o seguinte comando.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     O proxy pode então ser compilado como uma biblioteca e importado para o cliente de serviço web XML. Para compilar o código proxy Visual Basic .NET armazenado em sample.vb como sample.dll, emita o seguinte comando.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Para compilar o código proxy C# armazenado em sample.cs como sample.dll, emita o seguinte comando.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Crie um cliente de serviço Web XML.  
  
     Se você quiser que o Visual Studio gere a classe proxy de serviço web para você, basta criar o projeto cliente e, na janela Solution Explorer, clicar com o botão direito do mouse no projeto e, em seguida, selecionar **Adicionar** > **referência de serviço**. Na caixa de diálogo **Adicionar referência de serviço,** selecione **Avançado**e selecione Adicionar referência **da Web**. Selecione o serviço Web na lista de serviços web disponíveis (isso pode exigir o fornecimento do endereço do ponto final do serviço Web se o serviço Web não estiver disponível na solução atual ou no computador atual). Se você criar o proxy de serviço Web XML você mesmo (como descrito na etapa anterior), você pode importá-lo para o seu código cliente e consumir os métodos de serviço da Web XML.

     O código de exemplo a seguir importa a biblioteca proxy, chama **GetCustomers** para obter uma lista de clientes, adiciona um novo cliente e, em seguida, retorna um **DataSet** com as atualizações para **Clientes atualizados**.  
  
     O exemplo passa o **DataSet** retornado por **DataSet.GetChanges** to **UpdateCustomers** porque apenas as linhas modificadas precisam ser passadas para **UpdateCustomers**. **UpdateCustomers** retorna o **Conjunto de Dados**resolvido, que você pode então **mesclar** no **Conjunto de Dados** existente para incorporar as alterações resolvidas e quaisquer informações de erro de linha da atualização. O código a seguir pressupõe que você usou o Visual Studio para criar a referência da Web e que você renomeou a referência da Web para DsSample na caixa de diálogo Adicionar referência da **Web.**  
  
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
  
     Se você decidir criar a classe proxy você mesmo, você deve tomar os seguintes passos extras. Para compilar a amostra, forneça a biblioteca proxy criada (sample.dll) e as bibliotecas .NET relacionadas. Para compilar a versão Visual Basic .NET da amostra, armazenada no arquivo client.vb, emita o seguinte comando.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Para compilar a versão C# da amostra, armazenada no arquivo client.cs, emita o seguinte comando.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Confira também

- [ADO.NET](../index.md)
- [DataSets, DataTables e DataViews](index.md)
- [DataTables](datatables.md)
- [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)
- [Atualizando fontes de dados com DataAdapters](../updating-data-sources-with-dataadapters.md)
- [Parâmetros DataAdapter](../dataadapter-parameters.md)
- [Ferramenta de linguagem de descrição de serviços da Web (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [Visão geral do ADO.NET](../ado-net-overview.md)
