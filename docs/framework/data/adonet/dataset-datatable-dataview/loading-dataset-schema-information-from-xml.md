---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151046"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="37be3-102">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="37be3-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="37be3-103">O esquema de <xref:System.Data.DataSet> a (suas tabelas, colunas, relações e restrições) pode ser definido programáticamente, criado <xref:System.Data.Common.DataAdapter>pelos métodos **Fill** ou **FillSchema** de a , ou carregado a partir de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="37be3-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="37be3-104">Para carregar as informações do esquema **DataSet** de um documento XML, você pode usar o **ReadXmlSchema** ou o método **InferXmlSchema** do Conjunto de **Dados**.</span><span class="sxs-lookup"><span data-stu-id="37be3-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="37be3-105">**ReadXmlSchema** permite carregar ou inferir informações do esquema **DataSet** do documento que contém esquema xml de definição de esquema (XSD) ou um documento XML com esquema XML inline.</span><span class="sxs-lookup"><span data-stu-id="37be3-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="37be3-106">**InferXmlSchema** permite inferir o esquema do documento XML enquanto ignora certos espaços de nome XML que você especifica.</span><span class="sxs-lookup"><span data-stu-id="37be3-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37be3-107">O pedido de tabela em um **Conjunto de Dados** pode não ser preservado quando você usa serviços Web ou serialização XML para transferir um **DataSet** criado na memória usando construtos XSD (como relações aninhadas).</span><span class="sxs-lookup"><span data-stu-id="37be3-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="37be3-108">Portanto, o destinatário do **DataSet** não deve depender do pedido de tabela neste caso.</span><span class="sxs-lookup"><span data-stu-id="37be3-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="37be3-109">No entanto, o pedido de tabela é sempre preservado se o esquema do **DataSet** sendo transferido foi lido a partir de arquivos XSD, em vez de ser criado na memória.</span><span class="sxs-lookup"><span data-stu-id="37be3-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="37be3-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="37be3-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="37be3-111">Para carregar o esquema de um **DataSet** de um documento XML sem carregar nenhum dado, você pode usar o método **ReadXmlSchema** do **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="37be3-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="37be3-112">**ReadXmlSchema** cria esquema **DataSet** definido usando o esquema xml schema definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="37be3-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="37be3-113">O método **ReadXmlSchema** leva um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** contendo o documento XML a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="37be3-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="37be3-114">O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados.</span><span class="sxs-lookup"><span data-stu-id="37be3-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="37be3-115">Para obter detalhes sobre a escrita de esquemas inline como Esquema XML, consulte [Estrutura Relacional de Conjunto de Dados Derivados do Esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="37be3-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="37be3-116">Se o documento XML passado para **ReadXmlSchema** não contiver nenhuma informação de esquema inline, **ReadXmlSchema** inferirá o esquema dos elementos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="37be3-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="37be3-117">Se o **DataSet** já contiver um esquema, o esquema atual será estendido adicionando novas tabelas se elas ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="37be3-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="37be3-118">As novas colunas não serão adicionadas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="37be3-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="37be3-119">Se uma coluna que está sendo adicionada já existe no **DataSet,** mas tem um tipo incompatível com a coluna encontrada no XML, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="37be3-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="37be3-120">Para obter detalhes sobre como **o ReadXmlSchema** infere um esquema de um documento XML, consulte [Inferindo estrutura relacional do Conjunto de Dados do XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="37be3-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="37be3-121">Embora **o ReadXmlSchema** carregue ou infera apenas o esquema de um Conjunto de **Dados,** o método **ReadXml** do **DataSet** carrega ou infere tanto o esquema quanto os dados contidos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="37be3-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="37be3-122">Para obter mais informações, consulte [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="37be3-122">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="37be3-123">Os exemplos de código a seguir mostram como carregar um esquema **DataSet** de um documento ou fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="37be3-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="37be3-124">O primeiro exemplo mostra um nome de arquivo XML Schema sendo passado para o método **ReadXmlSchema.**</span><span class="sxs-lookup"><span data-stu-id="37be3-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="37be3-125">O segundo exemplo mostra um **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="37be3-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="37be3-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="37be3-126">InferXmlSchema</span></span>  
 <span data-ttu-id="37be3-127">Você também pode instruir o **DataSet** a inferir seu esquema a partir de um documento XML usando o método **InferXmlSchema** do **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="37be3-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="37be3-128">**InferXmlSchema** funciona da mesma forma que o **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere esquema) e **ReadXmlSchema** se o documento que está sendo lido não contiver nenhum esquema inline.</span><span class="sxs-lookup"><span data-stu-id="37be3-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="37be3-129">No entanto, **o InferXmlSchema** fornece a capacidade adicional de permitir que você especifique espaços de nome XML específicos para serem ignorados quando o esquema é inferido.</span><span class="sxs-lookup"><span data-stu-id="37be3-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="37be3-130">**InferXmlSchema** leva dois argumentos necessários: a localização do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader;** e uma matriz de strings de namespaces XML a serem ignoradas pela operação.</span><span class="sxs-lookup"><span data-stu-id="37be3-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="37be3-131">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="37be3-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="37be3-132">Devido aos atributos especificados para os elementos no documento XML anterior, tanto o método **ReadXmlSchema** quanto o método **ReadXml** com um **XmlReadMode** de **InferSchema** criariam **tabelas**para cada elemento no documento: Categorias , **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**e **Descontinuado**.</span><span class="sxs-lookup"><span data-stu-id="37be3-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="37be3-133">(Para obter mais informações, consulte [Inferindo estrutura relacional do conjunto de dados do XML](inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar apenas as **tabelas Categorias** e **Produtos** e, em seguida, criar colunas **CategoriaID,** **CategoryName**e **Descrição** na tabela **Categorias** e **ProductID,** **ReorderLevel**e Colunas **Descontinuadas** na tabela **Produtos.**</span><span class="sxs-lookup"><span data-stu-id="37be3-133">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="37be3-134">Para garantir que o esquema inferido ignore os atributos especificados nos elementos XML, use o método **InferXmlSchema** e especifique o namespace XML para **que os dados de escritório** sejam ignorados, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="37be3-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="37be3-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="37be3-135">See also</span></span>

- <span data-ttu-id="37be3-136">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="37be3-136">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- [<span data-ttu-id="37be3-137">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="37be3-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="37be3-138">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="37be3-138">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="37be3-139">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="37be3-139">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="37be3-140">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="37be3-140">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="37be3-141">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="37be3-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
