---
title: Gerando DataSets fortemente tipados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: ce7e5ad53f7aa5dad457ca1aa6ab76716086c0c3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833986"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="95cd2-102">Gerando DataSets fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="95cd2-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="95cd2-103">Dado um esquema XML que está em conformidade com o padrão XSD, você pode gerar um <xref:System.Data.DataSet> com rigidez de tipos usando a ferramenta XSD. exe fornecida com o SDK (Software Development Kit) do Windows.</span><span class="sxs-lookup"><span data-stu-id="95cd2-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the Windows Software Development Kit (SDK).</span></span>  
  
 <span data-ttu-id="95cd2-104">(Para criar um XSD a partir de tabelas de banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com DataSets no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="95cd2-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="95cd2-105">O código a seguir mostra a sintaxe para gerar um conjunto de um **DataSet** usando essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="95cd2-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="95cd2-106">Nessa sintaxe, a diretiva `/d` informa a ferramenta para gerar um **conjunto**de uma e o `/l:` informa à ferramenta qual idioma usar (por exemplo, C# ou Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="95cd2-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="95cd2-107">A diretiva opcional `/eld` especifica que você pode usar LINQ to DataSet para consultar o conjunto de um **dataset gerado.**</span><span class="sxs-lookup"><span data-stu-id="95cd2-107">The optional `/eld` directive specifies that you can use LINQ to DataSet to query against the generated **DataSet.**</span></span> <span data-ttu-id="95cd2-108">Essa opção é usada quando a opção `/d` também está especificada.</span><span class="sxs-lookup"><span data-stu-id="95cd2-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="95cd2-109">Para obter mais informações, consulte [consultando conjuntos de dados tipados](../querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="95cd2-109">For more information, see [Querying Typed DataSets](../querying-typed-datasets.md).</span></span> <span data-ttu-id="95cd2-110">A diretiva opcional `/n:` informa à ferramenta para gerar também um namespace para o **conjunto** de espaço chamado **XSDSchema. namespace**.</span><span class="sxs-lookup"><span data-stu-id="95cd2-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="95cd2-111">A saída do comando é XSDSchemaFileName.cs, o que pode ser compilado e usado em um aplicativo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="95cd2-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="95cd2-112">O código gerado pode ser compilado como uma biblioteca ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="95cd2-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="95cd2-113">O código a seguir mostra a sintaxe para compilar o código gerado como uma biblioteca usando o compilador C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="95cd2-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="95cd2-114">A política `/t:` diz à ferramenta para criar em uma biblioteca e as políticas `/r:` especificam as bibliotecas dependentes necessárias para compilar.</span><span class="sxs-lookup"><span data-stu-id="95cd2-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="95cd2-115">A saída do comando é XSDSchemaFileName.dll, que pode ser passado para o compilador ao criar um aplicativo do ADO.NET com a política `/r:`.</span><span class="sxs-lookup"><span data-stu-id="95cd2-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="95cd2-116">O código a seguir mostra a sintaxe para acessar o namespace passado para XSD.exe em um aplicativo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="95cd2-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="95cd2-117">O exemplo de código a seguir usa um **DataSet** tipado chamado **CustomerDataSet** para carregar uma lista de clientes do banco de dados **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="95cd2-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="95cd2-118">Depois que os dados são carregados usando o método **Fill** , o exemplo percorre cada cliente na tabela **Customers** usando o objeto **CustomersRow** (**DataRow**) digitado.</span><span class="sxs-lookup"><span data-stu-id="95cd2-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="95cd2-119">Isso fornece acesso direto à coluna **CustomerID** , em oposição ao por meio de **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="95cd2-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 <span data-ttu-id="95cd2-120">Este é o esquema XML usado para o exemplo:</span><span class="sxs-lookup"><span data-stu-id="95cd2-120">The following is the XML Schema used for the example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95cd2-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95cd2-121">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- <span data-ttu-id="95cd2-122">[Typed DataSets](typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="95cd2-122">[Typed DataSets](typed-datasets.md)</span></span>
- <span data-ttu-id="95cd2-123">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="95cd2-123">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="95cd2-124">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="95cd2-124">[ADO.NET Overview](../ado-net-overview.md)</span></span>
