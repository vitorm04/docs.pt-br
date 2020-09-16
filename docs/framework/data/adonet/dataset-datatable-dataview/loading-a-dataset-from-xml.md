---
title: Carregando um DataSet a partir de XML
description: Saiba como adicionar conteúdo a um conjunto de ADO.NET de XML. O .NET Framework oferece flexibilidade para o que carregar e a estrutura do conjunto de dados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 77715913c24423c1dc95478977f4e3821e4c247b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545305"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="ec915-104">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="ec915-104">Loading a DataSet from XML</span></span>
<span data-ttu-id="ec915-105">O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML.</span><span class="sxs-lookup"><span data-stu-id="ec915-105">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="ec915-106">Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.</span><span class="sxs-lookup"><span data-stu-id="ec915-106">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="ec915-107">Para preencher um <xref:System.Data.DataSet> com dados do XML, use o método **ReadXml** do <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="ec915-107">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="ec915-108">O método **ReadXml** lê de um arquivo, de um fluxo ou de um **XmlReader**e usa como argumentos a origem do XML, além de um argumento **XmlReadMode** opcional.</span><span class="sxs-lookup"><span data-stu-id="ec915-108">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="ec915-109">Para obter mais informações sobre o **XmlReader**, consulte [lendo dados XML com XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ec915-109">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="ec915-110">O método **ReadXml** lê o conteúdo do fluxo ou do documento XML e carrega o <xref:System.Data.DataSet> com os dados.</span><span class="sxs-lookup"><span data-stu-id="ec915-110">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="ec915-111">Ele também criará o esquema relacional do <xref:System.Data.DataSet> dependendo do **XmlReadMode** especificado e se um esquema relacional já existe ou não.</span><span class="sxs-lookup"><span data-stu-id="ec915-111">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="ec915-112">A tabela a seguir descreve as opções para o argumento **XmlReadMode** .</span><span class="sxs-lookup"><span data-stu-id="ec915-112">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="ec915-113">Opção</span><span class="sxs-lookup"><span data-stu-id="ec915-113">Option</span></span>|<span data-ttu-id="ec915-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec915-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ec915-115">**Auto**</span><span class="sxs-lookup"><span data-stu-id="ec915-115">**Auto**</span></span>|<span data-ttu-id="ec915-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ec915-116">This is the default.</span></span> <span data-ttu-id="ec915-117">Examina o XML e escolhe a opção mais apropriada na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="ec915-117">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="ec915-118">-Se o XML for um DiffGram, o **DiffGram** será usado.</span><span class="sxs-lookup"><span data-stu-id="ec915-118">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="ec915-119">-Se o <xref:System.Data.DataSet> contiver um esquema ou o XML contiver um esquema embutido, **ReadSchema** será usado.</span><span class="sxs-lookup"><span data-stu-id="ec915-119">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="ec915-120">-Se o não <xref:System.Data.DataSet> contiver um esquema e o XML não contiver um esquema embutido, **InferSchema** será usado.</span><span class="sxs-lookup"><span data-stu-id="ec915-120">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="ec915-121">Se você souber o formato do XML que está sendo lido, para obter o melhor desempenho, é recomendável que você defina um **XmlReadMode**explícito, em vez de aceitar o padrão **automático** .</span><span class="sxs-lookup"><span data-stu-id="ec915-121">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="ec915-122">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="ec915-122">**ReadSchema**</span></span>|<span data-ttu-id="ec915-123">Lê qualquer esquema embutido e carrega os dados e o esquema.</span><span class="sxs-lookup"><span data-stu-id="ec915-123">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="ec915-124">Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ec915-124">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ec915-125">Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="ec915-125">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="ec915-126">Você não poderá modificar o esquema de uma tabela existente usando **XmlReadMode. ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="ec915-126">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="ec915-127">Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.</span><span class="sxs-lookup"><span data-stu-id="ec915-127">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="ec915-128">O esquema embutido pode ser definido usando o esquema da linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="ec915-128">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="ec915-129">Para obter detalhes sobre como gravar o esquema embutido como esquema XML, consulte [derivando a estrutura relacional do conjunto de dados do esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="ec915-129">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="ec915-130">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="ec915-130">**IgnoreSchema**</span></span>|<span data-ttu-id="ec915-131">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="ec915-131">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="ec915-132">Os dados que não corresponderem ao esquema existente serão descartados.</span><span class="sxs-lookup"><span data-stu-id="ec915-132">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="ec915-133">Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.</span><span class="sxs-lookup"><span data-stu-id="ec915-133">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="ec915-134">Se os dados forem um DiffGram, **IgnoreSchema** terá a mesma funcionalidade que **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="ec915-134">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="ec915-135">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="ec915-135">**InferSchema**</span></span>|<span data-ttu-id="ec915-136">Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.</span><span class="sxs-lookup"><span data-stu-id="ec915-136">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="ec915-137">Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="ec915-137">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="ec915-138">As tabelas adicionais não serão adicionadas se não houver tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="ec915-138">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="ec915-139">Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.</span><span class="sxs-lookup"><span data-stu-id="ec915-139">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="ec915-140">Para obter detalhes sobre como o **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo a estrutura relacional do conjunto de dados do XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ec915-140">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="ec915-141">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="ec915-141">**DiffGram**</span></span>|<span data-ttu-id="ec915-142">Lê um DiffGram e adiciona os dados no esquema atual.</span><span class="sxs-lookup"><span data-stu-id="ec915-142">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="ec915-143">O **DiffGram** mescla novas linhas com linhas existentes nas quais os valores de identificador exclusivos correspondem.</span><span class="sxs-lookup"><span data-stu-id="ec915-143">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="ec915-144">Consulte "Mesclando dados de XML” no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ec915-144">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="ec915-145">Para obter mais informações sobre DiffGrams, consulte [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="ec915-145">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="ec915-146">**Fragmento**</span><span class="sxs-lookup"><span data-stu-id="ec915-146">**Fragment**</span></span>|<span data-ttu-id="ec915-147">Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado.</span><span class="sxs-lookup"><span data-stu-id="ec915-147">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="ec915-148">Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="ec915-148">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="ec915-149">Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.</span><span class="sxs-lookup"><span data-stu-id="ec915-149">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ec915-150">Se você passar um **XmlReader** para **ReadXml** que está posicionado parte do caminho em um documento XML, o **ReadXml** lerá para o próximo nó do elemento e tratará isso como o elemento raiz, lendo até o final do nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="ec915-150">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="ec915-151">Isso não se aplicará se você especificar **XmlReadMode. Fragment**.</span><span class="sxs-lookup"><span data-stu-id="ec915-151">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="ec915-152">Entidades DTD</span><span class="sxs-lookup"><span data-stu-id="ec915-152">DTD Entities</span></span>  
 <span data-ttu-id="ec915-153">Se o XML contiver entidades definidas em um esquema de definição de tipo de documento (DTD), uma exceção será gerada se você tentar carregar um <xref:System.Data.DataSet> passando um nome de arquivo, um fluxo ou um **XmlReader** de não validação para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ec915-153">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="ec915-154">Em vez disso, você deve criar um **XmlValidatingReader**, com **EntityHandling** definido como **EntityHandling. ExpandEntities**e passar seu **XmlValidatingReader** para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ec915-154">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="ec915-155">O **XmlValidatingReader** expandirá as entidades antes de serem lidas pelo <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="ec915-155">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="ec915-156">Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="ec915-156">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="ec915-157">O primeiro exemplo mostra um nome de arquivo que está sendo passado para o método **ReadXml** .</span><span class="sxs-lookup"><span data-stu-id="ec915-157">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="ec915-158">O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="ec915-158">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="ec915-159">Se você chamar a **ReadXml** para carregar um arquivo muito grande, você poderá encontrar um desempenho lento.</span><span class="sxs-lookup"><span data-stu-id="ec915-159">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="ec915-160">Para garantir o melhor desempenho para o **ReadXml**, em um arquivo grande, chame o <xref:System.Data.DataTable.BeginLoadData%2A> método para cada tabela no <xref:System.Data.DataSet> e chame **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="ec915-160">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="ec915-161">Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec915-161">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="ec915-162">Se o esquema XSD para o <xref:System.Data.DataSet> incluir um **targetNamespace**, os dados poderão não ser lidos e você poderá encontrar exceções ao chamar **ReadXml** para carregar o <xref:System.Data.DataSet> com XML que contém elementos sem namespace qualificado.</span><span class="sxs-lookup"><span data-stu-id="ec915-162">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="ec915-163">Para ler elementos não qualificados nesse caso, defina **elementFormDefault** igual a "qualified" no seu esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="ec915-163">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="ec915-164">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ec915-164">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="ec915-165">Mesclando dados de XML</span><span class="sxs-lookup"><span data-stu-id="ec915-165">Merging Data from XML</span></span>  
 <span data-ttu-id="ec915-166">Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ec915-166">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ec915-167">A **ReadXml** não faz a mesclagem do XML <xref:System.Data.DataSet> com as informações de linha com chaves primárias correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ec915-167">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="ec915-168">Para substituir as informações de linha existentes por novas informações de XML, use o **ReadXml** para criar um novo <xref:System.Data.DataSet> e, em seguida, <xref:System.Data.DataSet.Merge%2A> o novo <xref:System.Data.DataSet> no existente <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="ec915-168">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ec915-169">Observe que o carregamento de um DiffGram usando **ReadXml** com um **XmlReadMode** de **DiffGram** mesclará as linhas que têm o mesmo identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="ec915-169">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec915-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec915-170">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ec915-171">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="ec915-171">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="ec915-172">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="ec915-172">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="ec915-173">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ec915-173">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="ec915-174">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="ec915-174">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="ec915-175">Carregando informações do esquema de DataSet do XML</span><span class="sxs-lookup"><span data-stu-id="ec915-175">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ec915-176">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="ec915-176">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ec915-177">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ec915-177">ADO.NET Overview</span></span>](../ado-net-overview.md)
