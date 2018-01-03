---
title: Anotando DataSets tipados
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
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4528393d3d9491d9c1f12a867eb093e75d028f3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="annotating-typed-datasets"></a>Anotando DataSets tipados
As anotações permitem que você modifique os nomes dos elementos em seu <xref:System.Data.DataSet> tipado sem modificar o esquema subjacente. Modificar os nomes dos elementos no esquema subjacente causaria tipado **DataSet** para se referir a objetos que não existe na fonte de dados, bem como perder uma referência para os objetos que existem na fonte de dados.  
  
 Usando anotações, você pode personalizar os nomes dos objetos no seu tipo **DataSet** com nomes mais significativos, tornando o código mais legível e seu tipo **DataSet** mais fácil para os clientes usarem, deixando esquema subjacente intacto. Por exemplo, o seguinte elemento de esquema para o **clientes** tabela do **Northwind** banco de dados pode resultar em uma **DataRow** nome do objeto do  **CustomersRow** e um <xref:System.Data.DataRowCollection> chamado **clientes**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Um **DataRowCollection** nome de **clientes** significativa no código do cliente, mas um **DataRow** nome de **CustomersRow** está incorreta porque é um único objeto. Além disso, em comum cenários, o objeto deve ser chamado sem a **linha** identificador e, em vez disso seria simplesmente chamado de um **cliente** objeto. A solução é anotar o esquema e identificar novos nomes para o **DataRow** e **DataRowCollection** objetos. Veja a seguir a versão anotada do esquema anterior.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Especificando um **typedName** valor **cliente** resultará em um **DataRow** nome do objeto do **cliente**. Especificando um **typedPlural** valor **clientes** preserva o **DataRowCollection** nome de **clientes**.  
  
 A tabela a seguir mostra as anotações disponíveis para uso.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**typedName**|Nome do objeto.|  
|**typedPlural**|Nome de uma coleção de objetos.|  
|**typedParent**|Nome do objeto quando chamado em uma relação de pai.|  
|**typedChildren**|Nome do método para retornar objetos de uma relação filho.|  
|**nullValue**|Valor se o valor subjacente for **DBNull**. Consulte a tabela a seguir para **nullValue** anotações. O padrão é **_throw**.|  
  
 A tabela a seguir mostra os valores que podem ser especificados para o **nullValue** anotação.  
  
|Valor nullValue|Descrição|  
|---------------------|-----------------|  
|*Valor de substituição*|Especifique um valor a ser retornado. O valor retornado deve corresponder ao tipo de elemento. Por exemplo, use `nullValue="0"` para retornar 0 para campos de inteiro nulos.|  
|**_throw**|Gera uma exceção. Esse é o padrão.|  
|**_null**|Retorna uma referência nula ou gera uma exceção se um tipo primitivo for localizado.|  
|**_empty**|Cadeias de caracteres, retornar **Empty**, caso contrário, retornará um objeto criado a partir de um construtor vazio. Se um tipo primitivo for encontrado, gera uma exceção.|  
  
 A tabela a seguir mostra os valores padrão para objetos em um tipo **DataSet** e as anotações disponíveis.  
  
|Objeto/método/evento|Padrão|Anotação|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** métodos|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Property**|PropertyName|typedName|  
|**Filho** acessador|GetChildTableNameRows|typedChildren|  
|**Pai** acessador|TableNameRow|typedParent|  
|**Conjunto de dados** eventos|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Para usar digitado **DataSet** anotações, você deve incluir o seguinte **xmlns** referência em seu esquema de linguagem XSD de definição de esquema XML. (Para criar um xsd de tabelas de banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com conjuntos de dados no Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Este é um esquema anotado de exemplo que expõe o **clientes** tabela do **Northwind** banco de dados com um parceiro para o **pedidos** tabela incluída.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 O exemplo de código a seguir usa uma fortemente tipada **DataSet** criado a partir do esquema de exemplo. Ele usa um <xref:System.Data.SqlClient.SqlDataAdapter> para preencher o **clientes** e outra tabela <xref:System.Data.SqlClient.SqlDataAdapter> para preencher o **pedidos** tabela. Fortemente tipada **DataSet** define o **DataRelations**.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomeromer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomeromer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
