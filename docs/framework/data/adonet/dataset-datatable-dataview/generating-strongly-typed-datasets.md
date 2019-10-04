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
# <a name="generating-strongly-typed-datasets"></a>Gerando DataSets fortemente tipados
Dado um esquema XML que está em conformidade com o padrão XSD, você pode gerar um <xref:System.Data.DataSet> com rigidez de tipos usando a ferramenta XSD. exe fornecida com o SDK (Software Development Kit) do Windows.  
  
 (Para criar um XSD a partir de tabelas de banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com DataSets no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 O código a seguir mostra a sintaxe para gerar um conjunto de um **DataSet** usando essa ferramenta.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Nessa sintaxe, a diretiva `/d` informa a ferramenta para gerar um **conjunto**de uma e o `/l:` informa à ferramenta qual idioma usar (por exemplo, C# ou Visual Basic .net). A diretiva opcional `/eld` especifica que você pode usar LINQ to DataSet para consultar o conjunto de um **dataset gerado.** Essa opção é usada quando a opção `/d` também está especificada. Para obter mais informações, consulte [consultando conjuntos de dados tipados](../querying-typed-datasets.md). A diretiva opcional `/n:` informa à ferramenta para gerar também um namespace para o **conjunto** de espaço chamado **XSDSchema. namespace**. A saída do comando é XSDSchemaFileName.cs, o que pode ser compilado e usado em um aplicativo ADO.NET. O código gerado pode ser compilado como uma biblioteca ou um módulo.  
  
 O código a seguir mostra a sintaxe para compilar o código gerado como uma biblioteca usando o compilador C# (csc.exe).  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 A política `/t:` diz à ferramenta para criar em uma biblioteca e as políticas `/r:` especificam as bibliotecas dependentes necessárias para compilar. A saída do comando é XSDSchemaFileName.dll, que pode ser passado para o compilador ao criar um aplicativo do ADO.NET com a política `/r:`.  
  
 O código a seguir mostra a sintaxe para acessar o namespace passado para XSD.exe em um aplicativo ADO.NET.  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 O exemplo de código a seguir usa um **DataSet** tipado chamado **CustomerDataSet** para carregar uma lista de clientes do banco de dados **Northwind** . Depois que os dados são carregados usando o método **Fill** , o exemplo percorre cada cliente na tabela **Customers** usando o objeto **CustomersRow** (**DataRow**) digitado. Isso fornece acesso direto à coluna **CustomerID** , em oposição ao por meio de **DataColumnCollection**.  
  
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
  
 Este é o esquema XML usado para o exemplo:
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Typed DataSets](typed-datasets.md) (DataSets tipados)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
