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
# <a name="generating-strongly-typed-datasets"></a>Gerando DataSets fortemente tipados
Considerando um esquema XML que está em conformidade com o padrão da linguagem XSD, você pode gerar um <xref:System.Data.DataSet> fortemente tipado usando a ferramenta XSD.exe fornecida com o [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)].  
  
 (Para criar um xsd de tabelas do banco de dados, consulte <xref:System.Data.DataSet.WriteXmlSchema%2A> ou [trabalhando com conjuntos de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio)).  
  
 O código a seguir mostra a sintaxe para gerar uma **conjunto de dados** usando essa ferramenta.  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 Nesta sintaxe, o `/d` diretiva diz à ferramenta para gerar uma **DataSet**e o `/l:` diz à ferramenta qual idioma usar (por exemplo, C# ou Visual Basic .NET). Opcional `/eld` diretiva especifica que você pode usar [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] a consulta gerado **conjunto de dados.** Essa opção é usada quando a opção `/d` também está especificada. Para obter mais informações, consulte [consultando DataSets tipados](../../../../../docs/framework/data/adonet/querying-typed-datasets.md). Opcional `/n:` diretiva diz à ferramenta para também gerar um namespace para o **DataSet** chamado **Xsdschema**. A saída do comando é XSDSchemaFileName.cs, o que pode ser compilado e usado em um aplicativo ADO.NET. O código gerado pode ser compilado como uma biblioteca ou um módulo.  
  
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
  
 O exemplo de código a seguir usa um tipado **conjunto de dados** denominado **CustomerDataSet** para carregar uma lista de clientes do **Northwind** banco de dados. Depois que os dados são carregados usando o **preencher** método, o exemplo percorre cada cliente na **clientes** usando o tipo de tabela **CustomersRow** ( **DataRow**) objeto. Isso fornece acesso direto à **CustomerID** coluna, em vez de por meio de **DataColumnCollection**.  
  
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
  
 Veja a seguir o esquema XML usado para o exemplo.  
  
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
- [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)
- [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
