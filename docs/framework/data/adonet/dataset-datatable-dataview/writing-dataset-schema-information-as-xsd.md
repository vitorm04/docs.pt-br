---
title: Gravando informações de esquema de conjunto de dados como XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: b2012b32b0751bc093b9b3267cbbfc2e1a408156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760993"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Gravando informações de esquema de conjunto de dados como XSD
Você pode escrever o esquema de um <xref:System.Data.DataSet> como esquema de linguagem XSD de definição de esquema XML, para que você pode transportar, com ou sem dados relacionados, em um documento XML. Esquema XML pode ser gravado em um arquivo, um fluxo, um <xref:System.Xml.XmlWriter>, ou uma cadeia de caracteres; ele é útil para gerar um fortemente tipada **conjunto de dados**. Para obter mais informações sobre fortemente tipado **DataSet** objetos, consulte [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando o **ColumnMapping** propriedade o <xref:System.Data.DataColumn> objeto. Para obter mais informações, consulte "Mapeamento de colunas para elementos XML, atributos e texto" [gravar o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Para gravar o esquema de um **DataSet** como um esquema XML, para um arquivo, fluxo, ou **XmlWriter**, use o **WriteXmlSchema** método do **conjunto de dados**. **WriteXmlSchema** pega um parâmetro que especifica o destino do esquema XML resultante. Os exemplos de código a seguir demonstram como escrever o esquema XML de um **DataSet** para um arquivo, passando uma cadeia de caracteres que contém um nome de arquivo e um <xref:System.IO.StreamWriter> objeto.  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 Para obter o esquema de um **DataSet** e gravá-la como uma cadeia de caracteres do esquema XML, use o **GetXmlSchema** método, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [Gravar o conteúdo do conjunto de dados como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
