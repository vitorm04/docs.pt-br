---
title: Gravar informações de esquema de DataSet como XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f9664d8e7bc221da68492140f30419ea8fb0d316
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204370"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>Gravar informações de esquema de DataSet como XSD
Você pode gravar o esquema de um <xref:System.Data.DataSet> esquema XSD (linguagem de definição de esquema XML), para que você possa transportá-lo, com ou sem dados relacionados, em um documento XML. O esquema XML pode ser gravado em um arquivo, um fluxo, <xref:System.Xml.XmlWriter>uma ou uma cadeia de caracteres; ele é útil para gerar um **conjunto**de um DataSet com rigidez de tipos. Para obter mais informações sobre objetos de **conjunto** de dados com rigidez de tipos, consulte [datasets tipados](typed-datasets.md).  
  
 Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando a propriedade **ColumnMapping** do <xref:System.Data.DataColumn> objeto. Para obter mais informações, consulte "Mapeando colunas para elementos XML, atributos e texto" na [escrita do conteúdo do conjunto de dados como dado XML](writing-dataset-contents-as-xml-data.md).  
  
 Para gravar o esquema de um **conjunto** de uma como esquema XML, em um arquivo, fluxo ou **XmlWriter**, use o método **WriteXmlSchema** do **conjunto**de um. **WriteXmlSchema** Obtém um parâmetro que especifica o destino do esquema XML resultante. Os exemplos de código a seguir demonstram como gravar o esquema XML de um **conjunto** de um em um arquivo, passando uma cadeia de caracteres <xref:System.IO.StreamWriter> contendo um nome de arquivo e um objeto.  
  
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
  
 Para obter o esquema de um **conjunto** de um e gravá-lo como uma cadeia de caracteres de esquema XML, use o método GetXmlSchema, conforme mostrado no exemplo a seguir.  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>Consulte também

- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Gravar o conteúdo do conjunto de dados como dados XML](writing-dataset-contents-as-xml-data.md)
- [Typed DataSets](typed-datasets.md) (DataSets tipados)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
