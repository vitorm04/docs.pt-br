---
title: Anotando DataSets tipados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151514"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="84004-102">Anotando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="84004-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="84004-103">As anotações permitem que você modifique os nomes dos elementos em seu <xref:System.Data.DataSet> tipado sem modificar o esquema subjacente.</span><span class="sxs-lookup"><span data-stu-id="84004-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="84004-104">Modificar os nomes dos elementos em seu esquema subjacente faria com que o **Conjunto de Dados** digitado se referisse a objetos que não existem na fonte de dados, bem como perderia uma referência aos objetos que existem na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="84004-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="84004-105">Usando anotações, você pode personalizar os nomes de objetos em seu **DataSet** digitado com nomes mais significativos, tornando o código mais legível e seu **DataSet** digitado mais fácil para os clientes usarem, deixando o esquema subjacente intacto.</span><span class="sxs-lookup"><span data-stu-id="84004-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="84004-106">Por exemplo, o seguinte elemento de esquema para a tabela **Clientes** do banco de dados <xref:System.Data.DataRowCollection> **Northwind** resultaria em um nome de objeto **DataRow** do **CustomersRow** e um chamado **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="84004-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="84004-107">Um nome **DataRowCollection** dos **Clientes** é significativo no código do cliente, mas um nome **DataRow** do **CustomersRow** é enganoso porque é um único objeto.</span><span class="sxs-lookup"><span data-stu-id="84004-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="84004-108">Além disso, em cenários comuns, o objeto seria referido sem o identificador **Row** e, em vez disso, seria simplesmente referido como um objeto **Cliente.**</span><span class="sxs-lookup"><span data-stu-id="84004-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="84004-109">A solução é anotar o esquema e identificar novos nomes para os objetos **DataRow** e **DataRowCollection.**</span><span class="sxs-lookup"><span data-stu-id="84004-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="84004-110">Veja a seguir a versão anotada do esquema anterior.</span><span class="sxs-lookup"><span data-stu-id="84004-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="84004-111">A especificação de um valor **de nome digitado** do **Cliente** resultará em um nome de objeto **DataRow** do **Cliente**.</span><span class="sxs-lookup"><span data-stu-id="84004-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="84004-112">Especificar um valor **digitadoPlural** dos **Clientes** preserva o nome **DataRowCollection** dos **Clientes**.</span><span class="sxs-lookup"><span data-stu-id="84004-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="84004-113">A tabela a seguir mostra as anotações disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="84004-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="84004-114">Anotação</span><span class="sxs-lookup"><span data-stu-id="84004-114">Annotation</span></span>|<span data-ttu-id="84004-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="84004-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="84004-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="84004-116">**typedName**</span></span>|<span data-ttu-id="84004-117">Nome do objeto.</span><span class="sxs-lookup"><span data-stu-id="84004-117">Name of the object.</span></span>|  
|<span data-ttu-id="84004-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="84004-118">**typedPlural**</span></span>|<span data-ttu-id="84004-119">Nome de uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="84004-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="84004-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="84004-120">**typedParent**</span></span>|<span data-ttu-id="84004-121">Nome do objeto quando chamado em uma relação de pai.</span><span class="sxs-lookup"><span data-stu-id="84004-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="84004-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="84004-122">**typedChildren**</span></span>|<span data-ttu-id="84004-123">Nome do método para retornar objetos de uma relação filho.</span><span class="sxs-lookup"><span data-stu-id="84004-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="84004-124">**Nullvalue**</span><span class="sxs-lookup"><span data-stu-id="84004-124">**nullValue**</span></span>|<span data-ttu-id="84004-125">Valor se o valor subjacente for **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="84004-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="84004-126">Veja a tabela a seguir para **anularAs** anotações de valor.</span><span class="sxs-lookup"><span data-stu-id="84004-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="84004-127">O padrão é **_throw**.</span><span class="sxs-lookup"><span data-stu-id="84004-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="84004-128">A tabela a seguir mostra os valores que podem ser especificados para a anotação **nullValue.**</span><span class="sxs-lookup"><span data-stu-id="84004-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="84004-129">Valor nullValue</span><span class="sxs-lookup"><span data-stu-id="84004-129">nullValue Value</span></span>|<span data-ttu-id="84004-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="84004-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="84004-131">*Valor de substituição*</span><span class="sxs-lookup"><span data-stu-id="84004-131">*Replacement Value*</span></span>|<span data-ttu-id="84004-132">Especifique um valor a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="84004-132">Specify a value to be returned.</span></span> <span data-ttu-id="84004-133">O valor retornado deve corresponder ao tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="84004-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="84004-134">Por exemplo, use `nullValue="0"` para retornar 0 para campos de inteiro nulos.</span><span class="sxs-lookup"><span data-stu-id="84004-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="84004-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="84004-135">**_throw**</span></span>|<span data-ttu-id="84004-136">Gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="84004-136">Throw an exception.</span></span> <span data-ttu-id="84004-137">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="84004-137">This is the default.</span></span>|  
|<span data-ttu-id="84004-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="84004-138">**_null**</span></span>|<span data-ttu-id="84004-139">Retorna uma referência nula ou gera uma exceção se um tipo primitivo for localizado.</span><span class="sxs-lookup"><span data-stu-id="84004-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="84004-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="84004-140">**_empty**</span></span>|<span data-ttu-id="84004-141">Para strings, **devolva String.Empty,** caso contrário, retorne um objeto criado a partir de um construtor vazio.</span><span class="sxs-lookup"><span data-stu-id="84004-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="84004-142">Se um tipo primitivo for encontrado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="84004-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="84004-143">A tabela a seguir mostra valores padrão para objetos em um Conjunto de **Dados** digitado e as anotações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="84004-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="84004-144">Objeto/método/evento</span><span class="sxs-lookup"><span data-stu-id="84004-144">Object/Method/Event</span></span>|<span data-ttu-id="84004-145">Padrão</span><span class="sxs-lookup"><span data-stu-id="84004-145">Default</span></span>|<span data-ttu-id="84004-146">Anotação</span><span class="sxs-lookup"><span data-stu-id="84004-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="84004-147">**Datatable**</span><span class="sxs-lookup"><span data-stu-id="84004-147">**DataTable**</span></span>|<span data-ttu-id="84004-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="84004-148">TableNameDataTable</span></span>|<span data-ttu-id="84004-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="84004-149">typedPlural</span></span>|  
|<span data-ttu-id="84004-150">**Tabela de dados** Métodos</span><span class="sxs-lookup"><span data-stu-id="84004-150">**DataTable** Methods</span></span>|<span data-ttu-id="84004-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="84004-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="84004-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="84004-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="84004-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="84004-153">DeleteTableNameRow</span></span>|<span data-ttu-id="84004-154">typedName</span><span class="sxs-lookup"><span data-stu-id="84004-154">typedName</span></span>|  
|<span data-ttu-id="84004-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="84004-155">**DataRowCollection**</span></span>|<span data-ttu-id="84004-156">TableName</span><span class="sxs-lookup"><span data-stu-id="84004-156">TableName</span></span>|<span data-ttu-id="84004-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="84004-157">typedPlural</span></span>|  
|<span data-ttu-id="84004-158">**Datarow**</span><span class="sxs-lookup"><span data-stu-id="84004-158">**DataRow**</span></span>|<span data-ttu-id="84004-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="84004-159">TableNameRow</span></span>|<span data-ttu-id="84004-160">typedName</span><span class="sxs-lookup"><span data-stu-id="84004-160">typedName</span></span>|  
|<span data-ttu-id="84004-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="84004-161">**DataColumn**</span></span>|<span data-ttu-id="84004-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="84004-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="84004-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="84004-163">DataRow.ColumnName</span></span>|<span data-ttu-id="84004-164">typedName</span><span class="sxs-lookup"><span data-stu-id="84004-164">typedName</span></span>|  
|<span data-ttu-id="84004-165">**Propriedade**</span><span class="sxs-lookup"><span data-stu-id="84004-165">**Property**</span></span>|<span data-ttu-id="84004-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="84004-166">PropertyName</span></span>|<span data-ttu-id="84004-167">typedName</span><span class="sxs-lookup"><span data-stu-id="84004-167">typedName</span></span>|  
|<span data-ttu-id="84004-168">**Criança** Acessador</span><span class="sxs-lookup"><span data-stu-id="84004-168">**Child** Accessor</span></span>|<span data-ttu-id="84004-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="84004-169">GetChildTableNameRows</span></span>|<span data-ttu-id="84004-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="84004-170">typedChildren</span></span>|  
|<span data-ttu-id="84004-171">**Pai** Acessador</span><span class="sxs-lookup"><span data-stu-id="84004-171">**Parent** Accessor</span></span>|<span data-ttu-id="84004-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="84004-172">TableNameRow</span></span>|<span data-ttu-id="84004-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="84004-173">typedParent</span></span>|  
|<span data-ttu-id="84004-174">**Conjunto de dados** Eventos</span><span class="sxs-lookup"><span data-stu-id="84004-174">**DataSet** Events</span></span>|<span data-ttu-id="84004-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="84004-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="84004-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="84004-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="84004-177">typedName</span><span class="sxs-lookup"><span data-stu-id="84004-177">typedName</span></span>|  
  
 <span data-ttu-id="84004-178">Para usar anotações **digitadas dataset,** você deve incluir a seguinte referência **xmlns** em seu esquema de definição XML Schema (XSD).</span><span class="sxs-lookup"><span data-stu-id="84004-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="84004-179">Para criar um xsd a <xref:System.Data.DataSet.WriteXmlSchema%2A> partir de tabelas de banco de dados, consulte ou [trabalhando com conjuntos de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="84004-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="84004-180">A seguir está um esquema anotado de amostra que expõe a tabela **Clientes** do banco de dados **Northwind** com uma relação com a tabela **Orders** incluída.</span><span class="sxs-lookup"><span data-stu-id="84004-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="84004-181">O exemplo de código a seguir usa um Conjunto de **Dados** fortemente digitado criado a partir do esquema de amostra.</span><span class="sxs-lookup"><span data-stu-id="84004-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="84004-182">Ele usa <xref:System.Data.SqlClient.SqlDataAdapter> um para preencher <xref:System.Data.SqlClient.SqlDataAdapter> a tabela **Clientes** e outro para preencher a tabela **Pedidos.**</span><span class="sxs-lookup"><span data-stu-id="84004-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="84004-183">O Conjunto de **Dados** fortemente digitado define as **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="84004-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
    customers.Customers.NewCustomer()  
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
    customers.Customers.NewCustomer();  
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
  
## <a name="see-also"></a><span data-ttu-id="84004-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="84004-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="84004-185">DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="84004-185">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="84004-186">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="84004-186">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="84004-187">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="84004-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
