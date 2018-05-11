---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="5877b-102">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="5877b-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="5877b-103">O esquema de um <xref:System.Data.DataSet> (suas tabelas, colunas, relações e restrições) podem ser definidas programaticamente, criado pelo **preencher** ou **FillSchema** métodos de um <xref:System.Data.Common.DataAdapter>, ou carregados de um Documento XML.</span><span class="sxs-lookup"><span data-stu-id="5877b-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="5877b-104">Para carregar **conjunto de dados** informações de esquema de um documento XML, você pode usar o **ReadXmlSchema** ou o **InferXmlSchema** método o **deconjuntodedados**.</span><span class="sxs-lookup"><span data-stu-id="5877b-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="5877b-105">**ReadXmlSchema** permite que você carregue ou inferir **DataSet** informações de esquema do documento que contém o esquema de linguagem XSD de definição de esquema XML ou um documento XML com embutido esquema XML.</span><span class="sxs-lookup"><span data-stu-id="5877b-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="5877b-106">**InferXmlSchema** permite inferir o esquema do documento XML ignorando certas namespaces XML que você especificar.</span><span class="sxs-lookup"><span data-stu-id="5877b-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5877b-107">Tabela Pedidos em um **DataSet** podem não ser preservadas quando você usar os serviços Web ou serialização de XML para transferir um **conjunto de dados** que foi criado na memória por meio de construções XSD (como relações aninhadas).</span><span class="sxs-lookup"><span data-stu-id="5877b-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="5877b-108">Portanto, o destinatário do **conjunto de dados** não deve depender tabela Pedidos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="5877b-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="5877b-109">No entanto, a ordenação de tabela é sempre preservado se o esquema do **conjunto de dados** que estão sendo transferidos foi lido no arquivo XSD, em vez de ser criado na memória.</span><span class="sxs-lookup"><span data-stu-id="5877b-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="5877b-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="5877b-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="5877b-111">Para carregar o esquema de um **conjunto de dados** de um documento XML sem carregar os dados, você pode usar o **ReadXmlSchema** método o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="5877b-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="5877b-112">**ReadXmlSchema** cria **DataSet** esquema definido usando o esquema de linguagem XSD de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="5877b-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="5877b-113">O **ReadXmlSchema** método aceita um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** que contém o documento XML a serem carregadas.</span><span class="sxs-lookup"><span data-stu-id="5877b-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="5877b-114">O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados.</span><span class="sxs-lookup"><span data-stu-id="5877b-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="5877b-115">Para obter detalhes sobre como escrever um esquema embutido como um esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="5877b-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="5877b-116">Se o documento XML passado para **ReadXmlSchema** não contêm nenhuma informação de esquema embutido, **ReadXmlSchema** deduzirá o esquema de elementos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="5877b-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="5877b-117">Se o **DataSet** já contém um esquema, o esquema atual será estendido pela adição de novas tabelas se elas ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="5877b-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="5877b-118">As novas colunas não serão adicionadas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="5877b-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="5877b-119">Se uma coluna que está sendo adicionada já existe no **conjunto de dados** , mas tem um tipo incompatível com a coluna encontrado no XML, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="5877b-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="5877b-120">Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5877b-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="5877b-121">Embora **ReadXmlSchema** carrega ou infere somente o esquema de um **conjunto de dados**, o **ReadXml** método o **conjunto de dados** carrega ou infere ambos o esquema e os dados contidos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="5877b-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="5877b-122">Para obter mais informações, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5877b-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="5877b-123">Os exemplos de código a seguir mostram como carregar um **DataSet** esquema a partir de um documento XML ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="5877b-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="5877b-124">O primeiro exemplo mostra um nome de arquivo de esquema XML que está sendo passado para o **ReadXmlSchema** método.</span><span class="sxs-lookup"><span data-stu-id="5877b-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="5877b-125">O segundo exemplo mostra um **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="5877b-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="5877b-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="5877b-126">InferXmlSchema</span></span>  
 <span data-ttu-id="5877b-127">Você também pode instruir o **DataSet** para inferir a esquema de um documento XML usando o **InferXmlSchema** método o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="5877b-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="5877b-128">**InferXmlSchema** funciona da mesma maneira que ambos **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere o esquema) e **ReadXmlSchema** se o documento que está sendo lido não contém nenhum esquema embutido.</span><span class="sxs-lookup"><span data-stu-id="5877b-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="5877b-129">No entanto, **InferXmlSchema** fornece a capacidade adicional de permitir que você especifique namespaces XML específico sejam ignorados quando o esquema é inferido.</span><span class="sxs-lookup"><span data-stu-id="5877b-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="5877b-130">**InferXmlSchema** leva dois argumentos necessários: o local do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader**; e uma matriz de cadeia de caracteres de namespaces XML para ser ignorada pela operação.</span><span class="sxs-lookup"><span data-stu-id="5877b-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="5877b-131">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="5877b-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="5877b-132">Devido os atributos especificados para os elementos no documento XML anterior, tanto o **ReadXmlSchema** método e o **ReadXml** método com um **XmlReadMode** de **InferSchema** cria tabelas para cada elemento do documento: **categorias**, **CategoryID**, **CategoryName**, **Descrição**, **produtos**, **ProductID**, **ReorderLevel**, e **Descontinuado**.</span><span class="sxs-lookup"><span data-stu-id="5877b-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="5877b-133">(Para obter mais informações, consulte [inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar somente o **categorias** e **produtos** tabelas e, em seguida, criar **CategoryID**, **CategoryName** , e **descrição** colunas o **categorias** tabela, e **ProductID**, **ReorderLevel**, e **Descontinuado** colunas o **produtos** tabela.</span><span class="sxs-lookup"><span data-stu-id="5877b-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="5877b-134">Para garantir que o esquema deduzido ignora os atributos especificados nos elementos XML, use o **InferXmlSchema** método e especifique o namespace XML **officedata** sejam ignorados, conforme mostrado do exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5877b-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="5877b-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5877b-135">See Also</span></span>  
 <span data-ttu-id="5877b-136">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="5877b-136">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 [<span data-ttu-id="5877b-137">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="5877b-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="5877b-138">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="5877b-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="5877b-139">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="5877b-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 <span data-ttu-id="5877b-140">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="5877b-140">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="5877b-141">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5877b-141">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
