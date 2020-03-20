---
title: Carregando um DataSet a partir de XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151059"
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="f5b63-102">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="f5b63-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="f5b63-103">O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML.</span><span class="sxs-lookup"><span data-stu-id="f5b63-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="f5b63-104">Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="f5b63-105">Para preencher <xref:System.Data.DataSet> um com dados de XML, use <xref:System.Data.DataSet> o método **ReadXml** do objeto.</span><span class="sxs-lookup"><span data-stu-id="f5b63-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="f5b63-106">O método **ReadXml** lê de um arquivo, um fluxo ou um **XmlReader**, e toma como argumentos a fonte do XML mais um argumento **XmlReadMode** opcional.</span><span class="sxs-lookup"><span data-stu-id="f5b63-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="f5b63-107">Para obter mais informações sobre o **XmlReader,** consulte [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f5b63-107">For more information about the **XmlReader**, see [Reading XML Data with XmlTextReader](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100)).</span></span> <span data-ttu-id="f5b63-108">O método **ReadXml** lê o conteúdo do fluxo ou <xref:System.Data.DataSet> documento XML e carrega o com dados.</span><span class="sxs-lookup"><span data-stu-id="f5b63-108">The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="f5b63-109">Ele também criará o esquema relacional do dependendo do <xref:System.Data.DataSet> **XmlReadMode** especificado e se já existe ou não um esquema relacional.</span><span class="sxs-lookup"><span data-stu-id="f5b63-109">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="f5b63-110">A tabela a seguir descreve as opções para o argumento **XmlReadMode.**</span><span class="sxs-lookup"><span data-stu-id="f5b63-110">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="f5b63-111">Opção</span><span class="sxs-lookup"><span data-stu-id="f5b63-111">Option</span></span>|<span data-ttu-id="f5b63-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5b63-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f5b63-113">**Automático**</span><span class="sxs-lookup"><span data-stu-id="f5b63-113">**Auto**</span></span>|<span data-ttu-id="f5b63-114">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="f5b63-114">This is the default.</span></span> <span data-ttu-id="f5b63-115">Examina o XML e escolhe a opção mais apropriada na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="f5b63-115">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="f5b63-116">- Se o XML for um DiffGram, **diffGram** é usado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-116">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="f5b63-117">- Se <xref:System.Data.DataSet> o houver um esquema ou o XML contiver um esquema inline, **ReadSchema** é usado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-117">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="f5b63-118">- Se <xref:System.Data.DataSet> o esquema não contiver um esquema e o XML não contiver um esquema inline, **inferSchema** é usado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-118">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="f5b63-119">Se você sabe o formato do XML sendo lido, para melhor desempenho é recomendável que você defina um **XmlReadMode**explícito, em vez de aceitar o padrão **Automático.**</span><span class="sxs-lookup"><span data-stu-id="f5b63-119">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="f5b63-120">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="f5b63-120">**ReadSchema**</span></span>|<span data-ttu-id="f5b63-121">Lê qualquer esquema embutido e carrega os dados e o esquema.</span><span class="sxs-lookup"><span data-stu-id="f5b63-121">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="f5b63-122">Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f5b63-122">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f5b63-123">Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="f5b63-123">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="f5b63-124">Você não será capaz de modificar o esquema de uma tabela existente usando **XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="f5b63-124">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="f5b63-125">Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.</span><span class="sxs-lookup"><span data-stu-id="f5b63-125">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="f5b63-126">O esquema embutido pode ser definido usando o esquema da linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="f5b63-126">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="f5b63-127">Para obter detalhes sobre a escrita de esquemas inline como Esquema XML, consulte [Estrutura Relacional de Conjunto de Dados Derivados do Esquema XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="f5b63-127">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="f5b63-128">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="f5b63-128">**IgnoreSchema**</span></span>|<span data-ttu-id="f5b63-129">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="f5b63-129">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="f5b63-130">Os dados que não corresponderem ao esquema existente serão descartados.</span><span class="sxs-lookup"><span data-stu-id="f5b63-130">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="f5b63-131">Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-131">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="f5b63-132">Se os dados forem um DiffGram, **IgnoreSchema** tem a mesma funcionalidade **que diffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="f5b63-132">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="f5b63-133">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="f5b63-133">**InferSchema**</span></span>|<span data-ttu-id="f5b63-134">Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.</span><span class="sxs-lookup"><span data-stu-id="f5b63-134">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="f5b63-135">Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="f5b63-135">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="f5b63-136">As tabelas adicionais não serão adicionadas se não houver tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="f5b63-136">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="f5b63-137">Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.</span><span class="sxs-lookup"><span data-stu-id="f5b63-137">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="f5b63-138">Para obter detalhes sobre como **o ReadXmlSchema** infere um esquema de um documento XML, consulte [Inferindo estrutura relacional do Conjunto de Dados do XML](inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f5b63-138">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="f5b63-139">**Diffgram**</span><span class="sxs-lookup"><span data-stu-id="f5b63-139">**DiffGram**</span></span>|<span data-ttu-id="f5b63-140">Lê um DiffGram e adiciona os dados no esquema atual.</span><span class="sxs-lookup"><span data-stu-id="f5b63-140">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="f5b63-141">**O DiffGram** mescla novas linhas com linhas existentes onde os valores exclusivos do identificador correspondem.</span><span class="sxs-lookup"><span data-stu-id="f5b63-141">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="f5b63-142">Consulte "Mesclando dados de XML” no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f5b63-142">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="f5b63-143">Para obter mais informações sobre diffGrams, consulte [DiffGrams](diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="f5b63-143">For more information about DiffGrams, see [DiffGrams](diffgrams.md).</span></span>|  
|<span data-ttu-id="f5b63-144">**Fragmento**</span><span class="sxs-lookup"><span data-stu-id="f5b63-144">**Fragment**</span></span>|<span data-ttu-id="f5b63-145">Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-145">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="f5b63-146">Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="f5b63-146">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="f5b63-147">Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.</span><span class="sxs-lookup"><span data-stu-id="f5b63-147">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f5b63-148">Se você passar um **XmlReader** para **ReadXml** que está posicionado parte do caminho em um documento XML, **readXml** lerá para o próximo nó de elemento e tratará isso como o elemento raiz, lendo até o final do nó do elemento apenas.</span><span class="sxs-lookup"><span data-stu-id="f5b63-148">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="f5b63-149">Isso não se aplica se você especificar **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="f5b63-149">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="f5b63-150">Entidades DTD</span><span class="sxs-lookup"><span data-stu-id="f5b63-150">DTD Entities</span></span>  
 <span data-ttu-id="f5b63-151">Se o XML contiver entidades definidas em um esquema de definição de tipo de documento <xref:System.Data.DataSet> (DTD), uma exceção será lançada se você tentar carregar um passando um nome de arquivo, fluxo ou não validação **do XmlReader** para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="f5b63-151">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="f5b63-152">Em vez disso, você deve criar um **XmlValidatingReader**, com **EntityHandling** definido para **EntityHandling.ExpandEntities**, e passar seu **XmlValidatingReader** para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="f5b63-152">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="f5b63-153">O **XmlValidatingReader** expandirá as entidades antes <xref:System.Data.DataSet>de serem lidos pelo .</span><span class="sxs-lookup"><span data-stu-id="f5b63-153">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="f5b63-154">Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="f5b63-154">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="f5b63-155">O primeiro exemplo mostra um nome de arquivo sendo passado para o método **ReadXml.**</span><span class="sxs-lookup"><span data-stu-id="f5b63-155">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="f5b63-156">O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="f5b63-156">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
> <span data-ttu-id="f5b63-157">Se você chamar **ReadXml** para carregar um arquivo muito grande, você pode encontrar desempenho lento.</span><span class="sxs-lookup"><span data-stu-id="f5b63-157">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="f5b63-158">Para garantir o melhor desempenho para **ReadXml,** em um arquivo grande, chame o <xref:System.Data.DataTable.BeginLoadData%2A> método para cada tabela no <xref:System.Data.DataSet>e, em seguida, chame **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="f5b63-158">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="f5b63-159">Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5b63-159">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="f5b63-160">Se o esquema XSD <xref:System.Data.DataSet> para o seu incluir um **targetNamespace,** os dados podem não ser lidos <xref:System.Data.DataSet> e você pode encontrar exceções ao chamar **ReadXml** para carregar o com XML que contém elementos sem espaço de nome qualificado.</span><span class="sxs-lookup"><span data-stu-id="f5b63-160">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="f5b63-161">Para ler elementos não qualificados neste caso, defina **o elementoFormDefault** igual a "qualificado" em seu esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="f5b63-161">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="f5b63-162">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="f5b63-162">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="f5b63-163">Mesclando dados de XML</span><span class="sxs-lookup"><span data-stu-id="f5b63-163">Merging Data from XML</span></span>  
 <span data-ttu-id="f5b63-164">Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f5b63-164">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f5b63-165">**ReadXml** não se fundiu <xref:System.Data.DataSet> do XML em qualquer informação de linha com as teclas primárias correspondentes.</span><span class="sxs-lookup"><span data-stu-id="f5b63-165">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="f5b63-166">Para substituir as informações de linha existentes com novas informações do XML, <xref:System.Data.DataSet.Merge%2A> use <xref:System.Data.DataSet> **o ReadXml** para criar um novo <xref:System.Data.DataSet>e, em seguida, o novo no existente <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f5b63-166">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f5b63-167">Observe que o carregamento de um DiffGram usando **ReadXML** com um **XmlReadMode** do **DiffGram** irá mesclar linhas que tenham o mesmo identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="f5b63-167">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b63-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5b63-168">See also</span></span>

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- <span data-ttu-id="f5b63-169">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="f5b63-169">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- [<span data-ttu-id="f5b63-170">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="f5b63-170">DiffGrams</span></span>](diffgrams.md)
- [<span data-ttu-id="f5b63-171">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f5b63-171">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="f5b63-172">Inferir a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="f5b63-172">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="f5b63-173">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="f5b63-173">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="f5b63-174">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="f5b63-174">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="f5b63-175">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5b63-175">ADO.NET Overview</span></span>](../ado-net-overview.md)
