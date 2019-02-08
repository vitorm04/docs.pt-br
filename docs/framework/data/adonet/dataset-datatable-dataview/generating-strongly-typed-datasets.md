---
title: Gerando DataSets fortemente tipados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: d0a22a4ec4ed508a06e385d954a8ed5b9e9ff6a9
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825583"
---
# <a name="generating-strongly-typed-datasets"></a><span data-ttu-id="91596-102">Gerando DataSets fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="91596-102">Generating Strongly Typed DataSets</span></span>
<span data-ttu-id="91596-103">Considerando um esquema XML que está em conformidade com o padrão da linguagem XSD, você pode gerar um <xref:System.Data.DataSet> fortemente tipado usando a ferramenta XSD.exe fornecida com o [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91596-103">Given an XML Schema that complies with the XML Schema definition language (XSD) standard, you can generate a strongly typed <xref:System.Data.DataSet> using the XSD.exe tool provided with the [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].</span></span>  
  
 <span data-ttu-id="91596-104">(Para criar um xsd de tabelas do banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com conjuntos de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="91596-104">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).</span></span>  
  
 <span data-ttu-id="91596-105">O código a seguir mostra a sintaxe para gerar uma **conjunto de dados** usando essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="91596-105">The following code shows the syntax for generating a **DataSet** using this tool.</span></span>  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 <span data-ttu-id="91596-106">Nesta sintaxe, o `/d` diretiva diz à ferramenta para gerar uma **DataSet**e o `/l:` diz à ferramenta qual idioma usar (por exemplo, c# ou Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="91596-106">In this syntax, the `/d` directive tells the tool to generate a **DataSet**, and the `/l:` tells the tool what language to use (for example, C# or Visual Basic .NET).</span></span> <span data-ttu-id="91596-107">Opcional `/eld` diretiva especifica que você pode usar [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] a consulta gerado **conjunto de dados.**</span><span class="sxs-lookup"><span data-stu-id="91596-107">The optional `/eld` directive specifies that you can use [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] to query against the generated **DataSet.**</span></span> <span data-ttu-id="91596-108">Essa opção é usada quando a opção `/d` também está especificada.</span><span class="sxs-lookup"><span data-stu-id="91596-108">This option is used when the `/d` option is also specified.</span></span> <span data-ttu-id="91596-109">Para obter mais informações, consulte [consultando DataSets tipados](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="91596-109">For more information, see [Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="91596-110">Opcional `/n:` diretiva diz à ferramenta para também gerar um namespace para o **DataSet** chamado **Xsdschema**.</span><span class="sxs-lookup"><span data-stu-id="91596-110">The optional `/n:` directive tells the tool to also generate a namespace for the **DataSet** called **XSDSchema.Namespace**.</span></span> <span data-ttu-id="91596-111">A saída do comando é XSDSchemaFileName.cs, o que pode ser compilado e usado em um aplicativo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="91596-111">The output of the command is XSDSchemaFileName.cs, which can be compiled and used in an ADO.NET application.</span></span> <span data-ttu-id="91596-112">O código gerado pode ser compilado como uma biblioteca ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="91596-112">The generated code can be compiled as a library or a module.</span></span>  
  
 <span data-ttu-id="91596-113">O código a seguir mostra a sintaxe para compilar o código gerado como uma biblioteca usando o compilador C# (csc.exe).</span><span class="sxs-lookup"><span data-stu-id="91596-113">The following code shows the syntax for compiling the generated code as a library using the C# compiler (csc.exe).</span></span>  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 <span data-ttu-id="91596-114">A política `/t:` diz à ferramenta para criar em uma biblioteca e as políticas `/r:` especificam as bibliotecas dependentes necessárias para compilar.</span><span class="sxs-lookup"><span data-stu-id="91596-114">The `/t:` directive tells the tool to compile to a library, and the `/r:` directives specify dependent libraries required to compile.</span></span> <span data-ttu-id="91596-115">A saída do comando é XSDSchemaFileName.dll, que pode ser passado para o compilador ao criar um aplicativo do ADO.NET com a política `/r:`.</span><span class="sxs-lookup"><span data-stu-id="91596-115">The output of the command is XSDSchemaFileName.dll, which can be passed to the compiler when compiling an ADO.NET application with the `/r:` directive.</span></span>  
  
 <span data-ttu-id="91596-116">O código a seguir mostra a sintaxe para acessar o namespace passado para XSD.exe em um aplicativo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="91596-116">The following code shows the syntax for accessing the namespace passed to XSD.exe in an ADO.NET application.</span></span>  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 <span data-ttu-id="91596-117">O exemplo de código a seguir usa um tipado **conjunto de dados** denominado **CustomerDataSet** para carregar uma lista de clientes do **Northwind** banco de dados.</span><span class="sxs-lookup"><span data-stu-id="91596-117">The following code example uses a typed **DataSet** named **CustomerDataSet** to load a list of customers from the **Northwind** database.</span></span> <span data-ttu-id="91596-118">Depois que os dados são carregados usando o **preencher** método, o exemplo percorre cada cliente na **clientes** usando o tipo de tabela **CustomersRow** ( **DataRow**) objeto.</span><span class="sxs-lookup"><span data-stu-id="91596-118">Once the data is loaded using the **Fill** method, the example loops through each customer in the **Customers** table using the typed **CustomersRow** (**DataRow**) object.</span></span> <span data-ttu-id="91596-119">Isso fornece acesso direto à **CustomerID** coluna, em vez de por meio de **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="91596-119">This provides direct access to the **CustomerID** column, as opposed to through the **DataColumnCollection**.</span></span>  
  
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
  
 <span data-ttu-id="91596-120">Veja a seguir o esquema XML usado para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="91596-120">Following is the XML Schema used for the example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91596-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91596-121">See also</span></span>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- <span data-ttu-id="91596-122">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="91596-122">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)</span></span>
- <span data-ttu-id="91596-123">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="91596-123">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>
- <span data-ttu-id="91596-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="91596-124">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
