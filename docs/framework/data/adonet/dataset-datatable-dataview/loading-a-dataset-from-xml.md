---
title: Carregando um DataSet a partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 4c8b26651a1f4050145b6d43e03f9d4cc3d68202
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785283"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="77a9d-102">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="77a9d-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="77a9d-103">O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML.</span><span class="sxs-lookup"><span data-stu-id="77a9d-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="77a9d-104">Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="77a9d-105">Para preencher um <xref:System.Data.DataSet> com dados do XML, use o método **ReadXml** do <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="77a9d-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="77a9d-106">O método **ReadXml** lê de um arquivo, de um fluxo ou de um **XmlReader**e usa como argumentos a origem do XML, além de um argumento **XmlReadMode** opcional.</span><span class="sxs-lookup"><span data-stu-id="77a9d-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="77a9d-107">Para obter mais informações sobre o **XmlReader**, consulte [lendo dados XML com XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="77a9d-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="77a9d-108">O método **ReadXml** lê o conteúdo do fluxo ou do documento XML e carrega o <xref:System.Data.DataSet> com os dados.</span><span class="sxs-lookup"><span data-stu-id="77a9d-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="77a9d-109">Ele também criará o esquema relacional do <xref:System.Data.DataSet> dependendo do **XmlReadMode** especificado e se um esquema relacional já existe ou não.</span><span class="sxs-lookup"><span data-stu-id="77a9d-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="77a9d-110">A tabela a seguir descreve as opções para o argumento **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="77a9d-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="77a9d-111">Opção</span><span class="sxs-lookup"><span data-stu-id="77a9d-111">Option</span></span>|<span data-ttu-id="77a9d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="77a9d-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="77a9d-113">**Auto**</span><span class="sxs-lookup"><span data-stu-id="77a9d-113">**Auto**</span></span>|<span data-ttu-id="77a9d-114">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="77a9d-114">This is the default.</span></span> <span data-ttu-id="77a9d-115">Examina o XML e escolhe a opção mais apropriada na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="77a9d-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="77a9d-116">-Se o XML for um DiffGram, o **DiffGram** será usado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="77a9d-117">-Se o <xref:System.Data.DataSet> contiver um esquema ou o XML contiver um esquema embutido, **ReadSchema** será usado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="77a9d-118">-Se o <xref:System.Data.DataSet> não contiver um esquema e o XML não contiver um esquema embutido, **InferSchema** será usado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="77a9d-119">Se você souber o formato do XML que está sendo lido, para obter o melhor desempenho, é recomendável que você defina um **XmlReadMode**explícito, em vez de aceitar o padrão **automático** .</span><span class="sxs-lookup"><span data-stu-id="77a9d-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="77a9d-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="77a9d-120">**ReadSchema**</span></span>|<span data-ttu-id="77a9d-121">Lê qualquer esquema embutido e carrega os dados e o esquema.</span><span class="sxs-lookup"><span data-stu-id="77a9d-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="77a9d-122">Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="77a9d-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="77a9d-123">Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="77a9d-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="77a9d-124">Você não poderá modificar o esquema de uma tabela existente usando **XmlReadMode. ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="77a9d-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="77a9d-125">Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.</span><span class="sxs-lookup"><span data-stu-id="77a9d-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="77a9d-126">O esquema embutido pode ser definido usando o esquema da linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="77a9d-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="77a9d-127">Para obter detalhes sobre como gravar o esquema embutido como esquema XML, consulte [derivando a estrutura relacional do conjunto de dados do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="77a9d-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="77a9d-128">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="77a9d-128">**IgnoreSchema**</span></span>|<span data-ttu-id="77a9d-129">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="77a9d-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="77a9d-130">Os dados que não corresponderem ao esquema existente serão descartados.</span><span class="sxs-lookup"><span data-stu-id="77a9d-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="77a9d-131">Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="77a9d-132">Se os dados forem um DiffGram, **IgnoreSchema** terá a mesma funcionalidade que **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="77a9d-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="77a9d-133">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="77a9d-133">**InferSchema**</span></span>|<span data-ttu-id="77a9d-134">Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.</span><span class="sxs-lookup"><span data-stu-id="77a9d-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="77a9d-135">Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="77a9d-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="77a9d-136">As tabelas adicionais não serão adicionadas se não houver tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="77a9d-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="77a9d-137">Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.</span><span class="sxs-lookup"><span data-stu-id="77a9d-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="77a9d-138">Para obter detalhes sobre como o **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo a estrutura relacional do conjunto de dados do XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77a9d-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="77a9d-139">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="77a9d-139">**DiffGram**</span></span>|<span data-ttu-id="77a9d-140">Lê um DiffGram e adiciona os dados no esquema atual.</span><span class="sxs-lookup"><span data-stu-id="77a9d-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="77a9d-141">O **DiffGram** mescla novas linhas com linhas existentes nas quais os valores de identificador exclusivos correspondem.</span><span class="sxs-lookup"><span data-stu-id="77a9d-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="77a9d-142">Consulte "Mesclando dados de XML” no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="77a9d-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="77a9d-143">Para obter mais informações sobre DiffGrams, consulte [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="77a9d-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="77a9d-144">**Fragmento**</span><span class="sxs-lookup"><span data-stu-id="77a9d-144">**Fragment**</span></span>|<span data-ttu-id="77a9d-145">Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="77a9d-146">Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="77a9d-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="77a9d-147">Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.</span><span class="sxs-lookup"><span data-stu-id="77a9d-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="77a9d-148">Se você passar um **XmlReader** para **ReadXml** que está posicionado parte do caminho em um documento XML, o **ReadXml** lerá para o próximo nó do elemento e tratará isso como o elemento raiz, lendo até o final do nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="77a9d-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="77a9d-149">Isso não se aplicará se você especificar **XmlReadMode. Fragment**.</span><span class="sxs-lookup"><span data-stu-id="77a9d-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="77a9d-150">Entidades DTD</span><span class="sxs-lookup"><span data-stu-id="77a9d-150">DTD Entities</span></span>  
 <span data-ttu-id="77a9d-151">Se o XML contiver entidades definidas em um esquema de definição de tipo de documento (DTD), uma exceção será gerada se você tentar <xref:System.Data.DataSet> carregar um passando um nome de arquivo, um fluxo ou um **XmlReader** de não validação para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="77a9d-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="77a9d-152">Em vez disso, você deve criar um **XmlValidatingReader**, com **EntityHandling** definido como **EntityHandling. ExpandEntities**e passar seu **XmlValidatingReader** para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="77a9d-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="77a9d-153">O **XmlValidatingReader** expandirá as entidades antes de serem lidas pelo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="77a9d-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="77a9d-154">Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="77a9d-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="77a9d-155">O primeiro exemplo mostra um nome de arquivo que está sendo passado para o método **ReadXml** .</span><span class="sxs-lookup"><span data-stu-id="77a9d-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="77a9d-156">O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="77a9d-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> <span data-ttu-id="77a9d-157">Se você chamar a **ReadXml** para carregar um arquivo muito grande, você poderá encontrar um desempenho lento.</span><span class="sxs-lookup"><span data-stu-id="77a9d-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="77a9d-158">Para garantir o melhor desempenho para o **ReadXml**, em um arquivo grande, <xref:System.Data.DataTable.BeginLoadData%2A> chame o método para <xref:System.Data.DataSet>cada tabela no e chame **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="77a9d-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="77a9d-159">Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="77a9d-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> <span data-ttu-id="77a9d-160">Se o esquema XSD para o <xref:System.Data.DataSet> incluir um **targetNamespace**, os dados poderão não ser lidos e você poderá encontrar exceções ao chamar **ReadXml** para carregar o <xref:System.Data.DataSet> com XML que contém elementos sem namespace qualificado.</span><span class="sxs-lookup"><span data-stu-id="77a9d-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="77a9d-161">Para ler elementos não qualificados nesse caso, defina **elementFormDefault** igual a "qualified" no seu esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="77a9d-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="77a9d-162">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="77a9d-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="77a9d-163">Mesclando dados de XML</span><span class="sxs-lookup"><span data-stu-id="77a9d-163">Merging Data from XML</span></span>  
 <span data-ttu-id="77a9d-164">Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="77a9d-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="77a9d-165">A<xref:System.Data.DataSet> ReadXml não faz a mesclagem do XML com as informações de linha com chaves primárias correspondentes.</span><span class="sxs-lookup"><span data-stu-id="77a9d-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="77a9d-166">Para substituir as informações de linha existentes por novas informações de XML, use o **ReadXml** para <xref:System.Data.DataSet>criar um novo <xref:System.Data.DataSet.Merge%2A> e, <xref:System.Data.DataSet> em seguida, <xref:System.Data.DataSet>o novo no existente.</span><span class="sxs-lookup"><span data-stu-id="77a9d-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="77a9d-167">Observe que o carregamento de um DiffGram usando **ReadXml** com um **XmlReadMode** de **DiffGram** mesclará as linhas que têm o mesmo identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="77a9d-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a9d-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77a9d-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- <span data-ttu-id="77a9d-169">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="77a9d-169">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- [<span data-ttu-id="77a9d-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="77a9d-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="77a9d-171">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="77a9d-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="77a9d-172">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="77a9d-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="77a9d-173">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="77a9d-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- <span data-ttu-id="77a9d-174">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="77a9d-174">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="77a9d-175">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="77a9d-175">[ADO.NET Overview](../ado-net-overview.md)</span></span>
