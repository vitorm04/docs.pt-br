---
title: "Gravando informações de esquema de conjunto de dados como XSD"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 95f8a5d4d03c349467cbd13976ca9023470735aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="32d87-102">Gravando informações de esquema de conjunto de dados como XSD</span><span class="sxs-lookup"><span data-stu-id="32d87-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="32d87-103">Você pode escrever o esquema de um <xref:System.Data.DataSet> como esquema de linguagem XSD de definição de esquema XML, para que você pode transportar, com ou sem dados relacionados, em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="32d87-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="32d87-104">Esquema XML pode ser gravado em um arquivo, um fluxo, um <xref:System.Xml.XmlWriter>, ou uma cadeia de caracteres; ele é útil para gerar um fortemente tipada **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="32d87-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="32d87-105">Para obter mais informações sobre fortemente tipado **DataSet** objetos, consulte [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="32d87-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="32d87-106">Você pode especificar como uma coluna de uma tabela é representada no esquema XML usando o **ColumnMapping** propriedade o <xref:System.Data.DataColumn> objeto.</span><span class="sxs-lookup"><span data-stu-id="32d87-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="32d87-107">Para obter mais informações, consulte "Mapeamento de colunas para elementos XML, atributos e texto" [gravar o conteúdo do DataSet como dados XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="32d87-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="32d87-108">Para gravar o esquema de um **DataSet** como um esquema XML, para um arquivo, fluxo, ou **XmlWriter**, use o **WriteXmlSchema** método do **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="32d87-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="32d87-109">**WriteXmlSchema** pega um parâmetro que especifica o destino do esquema XML resultante.</span><span class="sxs-lookup"><span data-stu-id="32d87-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="32d87-110">Os exemplos de código a seguir demonstram como escrever o esquema XML de um **DataSet** para um arquivo, passando uma cadeia de caracteres que contém um nome de arquivo e um <xref:System.IO.StreamWriter> objeto.</span><span class="sxs-lookup"><span data-stu-id="32d87-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
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
  
 <span data-ttu-id="32d87-111">Para obter o esquema de um **DataSet** e gravá-la como uma cadeia de caracteres do esquema XML, use o **GetXmlSchema** método, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="32d87-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="32d87-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32d87-112">See Also</span></span>  
 <span data-ttu-id="32d87-113">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="32d87-113">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 [<span data-ttu-id="32d87-114">Gravar o conteúdo do conjunto de dados como dados XML</span><span class="sxs-lookup"><span data-stu-id="32d87-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="32d87-115">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="32d87-115">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)</span></span>  
 <span data-ttu-id="32d87-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="32d87-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="32d87-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="32d87-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
