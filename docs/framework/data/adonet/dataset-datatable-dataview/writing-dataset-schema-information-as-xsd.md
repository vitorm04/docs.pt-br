---
title: Gravar informações de esquema de DataSet como XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 8403f9d9be88f34e473fd3512f5499193245d227
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099437"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Gravar informações de esquema de DataSet como XSD
Você pode gravar o esquema de um <xref:System.Data.DataSet> como esquema de (XSD) de linguagem de definição de esquema XML, para que você pode transportar, com ou sem dados relacionados, em um documento XML. Esquema XML podem ser gravado em um arquivo, um fluxo, uma <xref:System.Xml.XmlWriter>, ou uma cadeia de caracteres; ele é útil para gerar um com rigidez de tipos **conjunto de dados**. Para obter mais informações sobre fortemente tipadas **DataSet** objetos, consulte [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando o **ColumnMapping** propriedade do <xref:System.Data.DataColumn> objeto. Para obter mais informações, consulte "Mapeamento de colunas para elementos XML, atributos e texto" em [gravando o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Para gravar o esquema de um **conjunto de dados** como um esquema XML, em um arquivo, fluxo, ou **XmlWriter**, use o **WriteXmlSchema** o método da **conjunto de dados**. **WriteXmlSchema** assume um parâmetro que especifica o destino do esquema XML resultante. Os exemplos de código a seguir demonstram como gravar o esquema XML de um **DataSet** em um arquivo, passando uma cadeia de caracteres que contém um nome de arquivo e um <xref:System.IO.StreamWriter> objeto.  
  
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
  
 Para obter o esquema de um **DataSet** e gravá-lo como uma cadeia de caracteres do esquema XML, use o **GetXmlSchema** método, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Consulte também

- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Gravando o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
