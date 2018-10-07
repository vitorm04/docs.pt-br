---
title: Gravando informações de esquema de conjunto de dados como XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 2a59a9fc1c3b2f52543f4cc69de22a5703fa9b8b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840098"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="4e0b9-102">Gravando informações de esquema de conjunto de dados como XSD</span><span class="sxs-lookup"><span data-stu-id="4e0b9-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="4e0b9-103">Você pode gravar o esquema de um <xref:System.Data.DataSet> como esquema de (XSD) de linguagem de definição de esquema XML, para que você pode transportar, com ou sem dados relacionados, em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="4e0b9-104">Esquema XML podem ser gravado em um arquivo, um fluxo, uma <xref:System.Xml.XmlWriter>, ou uma cadeia de caracteres; ele é útil para gerar um com rigidez de tipos **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="4e0b9-105">Para obter mais informações sobre fortemente tipadas **DataSet** objetos, consulte [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="4e0b9-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="4e0b9-106">Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando o **ColumnMapping** propriedade do <xref:System.Data.DataColumn> objeto.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="4e0b9-107">Para obter mais informações, consulte "Mapeamento de colunas para elementos XML, atributos e texto" em [gravando o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="4e0b9-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="4e0b9-108">Para gravar o esquema de um **conjunto de dados** como um esquema XML, em um arquivo, fluxo, ou **XmlWriter**, use o **WriteXmlSchema** o método da **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="4e0b9-109">**WriteXmlSchema** assume um parâmetro que especifica o destino do esquema XML resultante.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="4e0b9-110">Os exemplos de código a seguir demonstram como gravar o esquema XML de um **DataSet** em um arquivo, passando uma cadeia de caracteres que contém um nome de arquivo e um <xref:System.IO.StreamWriter> objeto.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="4e0b9-111">Para obter o esquema de um **DataSet** e gravá-lo como uma cadeia de caracteres do esquema XML, use o **GetXmlSchema** método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e0b9-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e0b9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e0b9-112">See Also</span></span>  
 <span data-ttu-id="4e0b9-113">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="4e0b9-113">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 [<span data-ttu-id="4e0b9-114">Gravar o conteúdo do conjunto de dados como dados XML</span><span class="sxs-lookup"><span data-stu-id="4e0b9-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="4e0b9-115">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="4e0b9-115">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)</span></span>  
 <span data-ttu-id="4e0b9-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="4e0b9-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="4e0b9-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4e0b9-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
