---
title: Carregando informações do esquema de DataSet do XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 06dcbbedf8c1533b3da52b447c121746ce705083
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083342"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="15c1c-102">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="15c1c-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="15c1c-103">O esquema de um <xref:System.Data.DataSet> (suas tabelas, colunas, relações e restrições) podem ser definidas programaticamente, criado pelo **preencher** ou **FillSchema** métodos de um <xref:System.Data.Common.DataAdapter>, ou carregados de um Documento XML.</span><span class="sxs-lookup"><span data-stu-id="15c1c-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="15c1c-104">Para carregar **DataSet** informações de esquema de um documento XML, você pode usar o **ReadXmlSchema** ou o **InferXmlSchema** o método da **doconjuntodedados**.</span><span class="sxs-lookup"><span data-stu-id="15c1c-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15c1c-105">**{1&gt;readxmlschema&lt;1** permite que você carregue ou Deduza **conjunto de dados** informações de esquema do documento que contém o esquema de (XSD) de linguagem de definição de esquema XML ou um documento XML com esquema XML embutido.</span><span class="sxs-lookup"><span data-stu-id="15c1c-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="15c1c-106">**{1&gt;inferxmlschema&lt;1** permite que você inferir o esquema do documento XML ignorando determinados namespaces XML que você especificar.</span><span class="sxs-lookup"><span data-stu-id="15c1c-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15c1c-107">Tabela de ordenação em um **DataSet** podem não ser preservadas quando você usa serviços da Web ou serialização XML para transferir um **conjunto de dados** que foi criado na memória usando construções XSD (como relações aninhadas).</span><span class="sxs-lookup"><span data-stu-id="15c1c-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="15c1c-108">Portanto, o destinatário dos **conjunto de dados** não devem depender nesse caso, a ordenação de tabela.</span><span class="sxs-lookup"><span data-stu-id="15c1c-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="15c1c-109">No entanto, a ordenação de tabela sempre é preservada se o esquema do **conjunto de dados** que está sendo transferido foi lido de arquivos XSD, em vez de que está sendo criado na memória.</span><span class="sxs-lookup"><span data-stu-id="15c1c-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="15c1c-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="15c1c-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="15c1c-111">Para carregar o esquema de um **DataSet** de um documento XML sem carregar todos os dados, você pode usar o **ReadXmlSchema** método da **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="15c1c-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15c1c-112">**{1&gt;readxmlschema&lt;1** cria **conjunto de dados** esquema definido usando o esquema de (XSD) de linguagem de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="15c1c-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="15c1c-113">O **ReadXmlSchema** método aceita um único argumento de um nome de arquivo, um fluxo ou um **XmlReader** que contém o documento XML a serem carregadas.</span><span class="sxs-lookup"><span data-stu-id="15c1c-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="15c1c-114">O documento XML pode conter somente o esquema ou pode conter o esquema embutido com elementos XML que contêm dados.</span><span class="sxs-lookup"><span data-stu-id="15c1c-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="15c1c-115">Para obter detalhes sobre como escrever um esquema embutido como o esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="15c1c-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="15c1c-116">Se o documento XML passado para **ReadXmlSchema** não contém nenhuma informação de esquema embutido, **ReadXmlSchema** inferirá o esquema dos elementos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="15c1c-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="15c1c-117">Se o **conjunto de dados** já contiver um esquema, o esquema atual será estendido adicionando novas tabelas se elas ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="15c1c-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="15c1c-118">As novas colunas não serão adicionadas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="15c1c-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="15c1c-119">Se uma coluna que está sendo adicionada já existe na **conjunto de dados** , mas tem um tipo incompatível com a coluna foi encontrado no XML, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="15c1c-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="15c1c-120">Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="15c1c-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="15c1c-121">Embora **ReadXmlSchema** carregue ou Deduza somente o esquema de uma **conjunto de dados**, o **ReadXml** o método da **DataSet** carrega ou deduz ambos o esquema e os dados contidos no documento XML.</span><span class="sxs-lookup"><span data-stu-id="15c1c-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="15c1c-122">Para obter mais informações, consulte [carregar um conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="15c1c-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="15c1c-123">Os exemplos de código a seguir mostram como carregar uma **conjunto de dados** esquema de um documento XML ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="15c1c-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="15c1c-124">O primeiro exemplo mostra um nome de arquivo de esquema XML que está sendo passado para o **ReadXmlSchema** método.</span><span class="sxs-lookup"><span data-stu-id="15c1c-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="15c1c-125">O segundo exemplo mostra uma **StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="15c1c-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="15c1c-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="15c1c-126">InferXmlSchema</span></span>  
 <span data-ttu-id="15c1c-127">Você também pode instruir o **DataSet** para deduzir o esquema de um documento XML usando o **InferXmlSchema** método da **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="15c1c-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="15c1c-128">**{1&gt;inferxmlschema&lt;1** funciona da mesma maneira **ReadXml** com um **XmlReadMode** de **InferSchema** (carrega dados, bem como infere o esquema) e **ReadXmlSchema** se o documento que está sendo lido não contém nenhum esquema embutido.</span><span class="sxs-lookup"><span data-stu-id="15c1c-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="15c1c-129">No entanto, **InferXmlSchema** fornece a capacidade adicional de permitir que você especificar namespaces específicos de XML a serem ignorados quando o esquema será inferido.</span><span class="sxs-lookup"><span data-stu-id="15c1c-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="15c1c-130">**{1&gt;inferxmlschema&lt;1** utiliza dois argumentos necessários: o local do documento XML, especificado por um nome de arquivo, um fluxo ou um **XmlReader**; e uma matriz de cadeia de caracteres de namespaces XML a ser ignorada pela operação.</span><span class="sxs-lookup"><span data-stu-id="15c1c-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="15c1c-131">Por exemplo, considere o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="15c1c-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="15c1c-132">Por causa dos atributos especificados para os elementos no documento XML anterior, tanto a **ReadXmlSchema** método e o **ReadXml** método com um **XmlReadMode** de **InferSchema** seria criar tabelas para cada elemento no documento: **Categorias**, **CategoryID**, **CategoryName**, **descrição**, **produtos**, **ProductID**, **ReorderLevel**, e **Descontinuado**.</span><span class="sxs-lookup"><span data-stu-id="15c1c-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="15c1c-133">(Para obter mais informações, consulte [inferindo estrutura relacional do DataSet do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) No entanto, uma estrutura mais apropriada seria criar somente o **categorias** e **produtos** tabelas e, em seguida, crie **CategoryID**, **CategoryName** , e **descrição** colunas no **categorias** tabela, e **ProductID**, **ReorderLevel**, e **Descontinuado** colunas na **produtos** tabela.</span><span class="sxs-lookup"><span data-stu-id="15c1c-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="15c1c-134">Para garantir que o esquema deduzido ignora os atributos especificados nos elementos XML, use o **InferXmlSchema** método e especifique o namespace XML para **officedata** devem ser ignorados, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="15c1c-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="15c1c-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15c1c-135">See also</span></span>

- [<span data-ttu-id="15c1c-136">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="15c1c-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="15c1c-137">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="15c1c-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="15c1c-138">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="15c1c-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="15c1c-139">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="15c1c-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="15c1c-140">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="15c1c-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="15c1c-141">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="15c1c-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
