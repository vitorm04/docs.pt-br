---
title: Gravar informações de esquema de DataSet como XSD
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f86e9100489ddf35d8ef5f98e386306a7dbfd4ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784171"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="05960-102">Gravar informações de esquema de DataSet como XSD</span><span class="sxs-lookup"><span data-stu-id="05960-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="05960-103">Você pode gravar o esquema de um <xref:System.Data.DataSet> esquema XSD (linguagem de definição de esquema XML), para que você possa transportá-lo, com ou sem dados relacionados, em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="05960-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="05960-104">O esquema XML pode ser gravado em um arquivo, um fluxo, <xref:System.Xml.XmlWriter>uma ou uma cadeia de caracteres; ele é útil para gerar um **conjunto**de um DataSet com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="05960-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="05960-105">Para obter mais informações sobre objetos de **conjunto** de dados com rigidez de tipos, consulte [datasets tipados](typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="05960-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="05960-106">Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando a propriedade **ColumnMapping** do <xref:System.Data.DataColumn> objeto.</span><span class="sxs-lookup"><span data-stu-id="05960-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="05960-107">Para obter mais informações, consulte "Mapeando colunas para elementos XML, atributos e texto" na [escrita do conteúdo do conjunto de dados como dado XML](writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="05960-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="05960-108">Para gravar o esquema de um **conjunto** de uma como esquema XML, em um arquivo, fluxo ou **XmlWriter**, use o método **WriteXmlSchema** do **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="05960-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="05960-109">**WriteXmlSchema** Obtém um parâmetro que especifica o destino do esquema XML resultante.</span><span class="sxs-lookup"><span data-stu-id="05960-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="05960-110">Os exemplos de código a seguir demonstram como gravar o esquema XML de um **conjunto** de um em um arquivo, passando uma cadeia de caracteres <xref:System.IO.StreamWriter> contendo um nome de arquivo e um objeto.</span><span class="sxs-lookup"><span data-stu-id="05960-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="05960-111">Para obter o esquema de um **conjunto** de um e gravá-lo como uma cadeia de caracteres de esquema XML, use o método **GetXmlSchema** , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="05960-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="05960-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05960-112">See also</span></span>

- <span data-ttu-id="05960-113">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="05960-113">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- [<span data-ttu-id="05960-114">Gravar o conteúdo do conjunto de dados como dados XML</span><span class="sxs-lookup"><span data-stu-id="05960-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)
- <span data-ttu-id="05960-115">[Typed DataSets](typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="05960-115">[Typed DataSets](typed-datasets.md)</span></span>
- <span data-ttu-id="05960-116">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="05960-116">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="05960-117">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="05960-117">[ADO.NET Overview](../ado-net-overview.md)</span></span>
