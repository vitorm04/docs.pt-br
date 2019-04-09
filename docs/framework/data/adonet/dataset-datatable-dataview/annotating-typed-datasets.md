---
title: Anotando DataSets tipados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085123"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="35b35-102">Anotando DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="35b35-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="35b35-103">As anotações permitem que você modifique os nomes dos elementos em seu <xref:System.Data.DataSet> tipado sem modificar o esquema subjacente.</span><span class="sxs-lookup"><span data-stu-id="35b35-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="35b35-104">Modificar os nomes dos elementos no esquema subjacente causaria tipado **conjunto de dados** para se referir a objetos que não existe na fonte de dados, bem como de perder uma referência para os objetos que existem na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="35b35-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="35b35-105">Usando anotações, você pode personalizar os nomes dos objetos no seu tipado **conjunto de dados** com nomes mais significativos, tornando o código mais legível e seu tipado **conjunto de dados** mais fácil para os clientes usarem, deixando os esquema subjacente intacto.</span><span class="sxs-lookup"><span data-stu-id="35b35-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="35b35-106">Por exemplo, o seguinte elemento de esquema para o **clientes** tabela da **Northwind** banco de dados pode resultar em um **DataRow** nome do objeto do  **CustomersRow** e uma <xref:System.Data.DataRowCollection> denominado **clientes**.</span><span class="sxs-lookup"><span data-stu-id="35b35-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="35b35-107">Um **DataRowCollection** nome do **clientes** significativa no código do cliente, mas um **DataRow** nome do **CustomersRow** está incorreta porque ele é um único objeto.</span><span class="sxs-lookup"><span data-stu-id="35b35-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="35b35-108">Além disso, em comum cenários, o objeto seria chamado sem a **linha** identificador e, em vez disso, seria chamado simplesmente como um **cliente** objeto.</span><span class="sxs-lookup"><span data-stu-id="35b35-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="35b35-109">A solução é anotar o esquema e identificar novos nomes para o **DataRow** e **DataRowCollection** objetos.</span><span class="sxs-lookup"><span data-stu-id="35b35-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="35b35-110">Veja a seguir a versão anotada do esquema anterior.</span><span class="sxs-lookup"><span data-stu-id="35b35-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="35b35-111">Especificando um **typedName** valor de **Customer** resultará em um **DataRow** nome do objeto do **cliente**.</span><span class="sxs-lookup"><span data-stu-id="35b35-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="35b35-112">Especificando um **typedPlural** valor de **clientes** preserva o **DataRowCollection** nome do **clientes**.</span><span class="sxs-lookup"><span data-stu-id="35b35-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="35b35-113">A tabela a seguir mostra as anotações disponíveis para uso.</span><span class="sxs-lookup"><span data-stu-id="35b35-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="35b35-114">Anotação</span><span class="sxs-lookup"><span data-stu-id="35b35-114">Annotation</span></span>|<span data-ttu-id="35b35-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="35b35-115">Description</span></span>|  
|----------------|-----------------|  
|**<span data-ttu-id="35b35-116">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-116">typedName</span></span>**|<span data-ttu-id="35b35-117">Nome do objeto.</span><span class="sxs-lookup"><span data-stu-id="35b35-117">Name of the object.</span></span>|  
|**<span data-ttu-id="35b35-118">typedPlural</span><span class="sxs-lookup"><span data-stu-id="35b35-118">typedPlural</span></span>**|<span data-ttu-id="35b35-119">Nome de uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="35b35-119">Name of a collection of objects.</span></span>|  
|**<span data-ttu-id="35b35-120">typedParent</span><span class="sxs-lookup"><span data-stu-id="35b35-120">typedParent</span></span>**|<span data-ttu-id="35b35-121">Nome do objeto quando chamado em uma relação de pai.</span><span class="sxs-lookup"><span data-stu-id="35b35-121">Name of the object when referred to in a parent relationship.</span></span>|  
|**<span data-ttu-id="35b35-122">typedChildren</span><span class="sxs-lookup"><span data-stu-id="35b35-122">typedChildren</span></span>**|<span data-ttu-id="35b35-123">Nome do método para retornar objetos de uma relação filho.</span><span class="sxs-lookup"><span data-stu-id="35b35-123">Name of the method to return objects from a child relationship.</span></span>|  
|**<span data-ttu-id="35b35-124">nullValue</span><span class="sxs-lookup"><span data-stu-id="35b35-124">nullValue</span></span>**|<span data-ttu-id="35b35-125">Valor se o valor subjacente for **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="35b35-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="35b35-126">Consulte a tabela a seguir para **nullValue** anotações.</span><span class="sxs-lookup"><span data-stu-id="35b35-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="35b35-127">O padrão é **throw**.</span><span class="sxs-lookup"><span data-stu-id="35b35-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="35b35-128">A tabela a seguir mostra os valores que podem ser especificados para o **nullValue** anotação.</span><span class="sxs-lookup"><span data-stu-id="35b35-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="35b35-129">Valor nullValue</span><span class="sxs-lookup"><span data-stu-id="35b35-129">nullValue Value</span></span>|<span data-ttu-id="35b35-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="35b35-130">Description</span></span>|  
|---------------------|-----------------|  
|*<span data-ttu-id="35b35-131">Valor de substituição</span><span class="sxs-lookup"><span data-stu-id="35b35-131">Replacement Value</span></span>*|<span data-ttu-id="35b35-132">Especifique um valor a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="35b35-132">Specify a value to be returned.</span></span> <span data-ttu-id="35b35-133">O valor retornado deve corresponder ao tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="35b35-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="35b35-134">Por exemplo, use `nullValue="0"` para retornar 0 para campos de inteiro nulos.</span><span class="sxs-lookup"><span data-stu-id="35b35-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|**<span data-ttu-id="35b35-135">_throw</span><span class="sxs-lookup"><span data-stu-id="35b35-135">_throw</span></span>**|<span data-ttu-id="35b35-136">Gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="35b35-136">Throw an exception.</span></span> <span data-ttu-id="35b35-137">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="35b35-137">This is the default.</span></span>|  
|**<span data-ttu-id="35b35-138">_null</span><span class="sxs-lookup"><span data-stu-id="35b35-138">_null</span></span>**|<span data-ttu-id="35b35-139">Retorna uma referência nula ou gera uma exceção se um tipo primitivo for localizado.</span><span class="sxs-lookup"><span data-stu-id="35b35-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|**<span data-ttu-id="35b35-140">_empty</span><span class="sxs-lookup"><span data-stu-id="35b35-140">_empty</span></span>**|<span data-ttu-id="35b35-141">Para cadeias de caracteres de retorno **String. Empty**, caso contrário, retornará um objeto criado a partir de um construtor vazio.</span><span class="sxs-lookup"><span data-stu-id="35b35-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="35b35-142">Se um tipo primitivo for encontrado, gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="35b35-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="35b35-143">A tabela a seguir mostra valores padrão para objetos em um tipado **conjunto de dados** e as anotações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="35b35-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="35b35-144">Objeto/método/evento</span><span class="sxs-lookup"><span data-stu-id="35b35-144">Object/Method/Event</span></span>|<span data-ttu-id="35b35-145">Padrão</span><span class="sxs-lookup"><span data-stu-id="35b35-145">Default</span></span>|<span data-ttu-id="35b35-146">Anotação</span><span class="sxs-lookup"><span data-stu-id="35b35-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|**<span data-ttu-id="35b35-147">DataTable</span><span class="sxs-lookup"><span data-stu-id="35b35-147">DataTable</span></span>**|<span data-ttu-id="35b35-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="35b35-148">TableNameDataTable</span></span>|<span data-ttu-id="35b35-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="35b35-149">typedPlural</span></span>|  
|<span data-ttu-id="35b35-150">**DataTable** métodos</span><span class="sxs-lookup"><span data-stu-id="35b35-150">**DataTable** Methods</span></span>|<span data-ttu-id="35b35-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="35b35-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="35b35-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="35b35-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="35b35-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="35b35-153">DeleteTableNameRow</span></span>|<span data-ttu-id="35b35-154">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-154">typedName</span></span>|  
|**<span data-ttu-id="35b35-155">DataRowCollection</span><span class="sxs-lookup"><span data-stu-id="35b35-155">DataRowCollection</span></span>**|<span data-ttu-id="35b35-156">TableName</span><span class="sxs-lookup"><span data-stu-id="35b35-156">TableName</span></span>|<span data-ttu-id="35b35-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="35b35-157">typedPlural</span></span>|  
|**<span data-ttu-id="35b35-158">DataRow</span><span class="sxs-lookup"><span data-stu-id="35b35-158">DataRow</span></span>**|<span data-ttu-id="35b35-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="35b35-159">TableNameRow</span></span>|<span data-ttu-id="35b35-160">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-160">typedName</span></span>|  
|**<span data-ttu-id="35b35-161">DataColumn</span><span class="sxs-lookup"><span data-stu-id="35b35-161">DataColumn</span></span>**|<span data-ttu-id="35b35-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="35b35-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="35b35-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="35b35-163">DataRow.ColumnName</span></span>|<span data-ttu-id="35b35-164">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-164">typedName</span></span>|  
|**<span data-ttu-id="35b35-165">Propriedade</span><span class="sxs-lookup"><span data-stu-id="35b35-165">Property</span></span>**|<span data-ttu-id="35b35-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="35b35-166">PropertyName</span></span>|<span data-ttu-id="35b35-167">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-167">typedName</span></span>|  
|<span data-ttu-id="35b35-168">**Filho** acessador</span><span class="sxs-lookup"><span data-stu-id="35b35-168">**Child** Accessor</span></span>|<span data-ttu-id="35b35-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="35b35-169">GetChildTableNameRows</span></span>|<span data-ttu-id="35b35-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="35b35-170">typedChildren</span></span>|  
|<span data-ttu-id="35b35-171">**Pai** acessador</span><span class="sxs-lookup"><span data-stu-id="35b35-171">**Parent** Accessor</span></span>|<span data-ttu-id="35b35-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="35b35-172">TableNameRow</span></span>|<span data-ttu-id="35b35-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="35b35-173">typedParent</span></span>|  
|<span data-ttu-id="35b35-174">**Conjunto de dados** eventos</span><span class="sxs-lookup"><span data-stu-id="35b35-174">**DataSet** Events</span></span>|<span data-ttu-id="35b35-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="35b35-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="35b35-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="35b35-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="35b35-177">typedName</span><span class="sxs-lookup"><span data-stu-id="35b35-177">typedName</span></span>|  
  
 <span data-ttu-id="35b35-178">Usar digitado **DataSet** anotações, você deve incluir o seguinte **xmlns** referência em seu esquema XSD (linguagem) de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="35b35-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="35b35-179">Para criar um xsd de tabelas do banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com conjuntos de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="35b35-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="35b35-180">A seguir está um esquema anotado de exemplo que expõe o **clientes** tabela da **Northwind** banco de dados com uma relação com o **pedidos** tabela incluída.</span><span class="sxs-lookup"><span data-stu-id="35b35-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
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
  
 <span data-ttu-id="35b35-181">O exemplo de código a seguir usa um fortemente tipados **conjunto de dados** criado do esquema de exemplo.</span><span class="sxs-lookup"><span data-stu-id="35b35-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="35b35-182">Ele usa um <xref:System.Data.SqlClient.SqlDataAdapter> para preencher a **clientes** e outra tabela <xref:System.Data.SqlClient.SqlDataAdapter> para preencher o **pedidos** tabela.</span><span class="sxs-lookup"><span data-stu-id="35b35-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="35b35-183">Fortemente tipados **DataSet** define o **DataRelations**.</span><span class="sxs-lookup"><span data-stu-id="35b35-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35b35-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35b35-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="35b35-185">DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="35b35-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [<span data-ttu-id="35b35-186">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="35b35-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="35b35-187">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="35b35-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
