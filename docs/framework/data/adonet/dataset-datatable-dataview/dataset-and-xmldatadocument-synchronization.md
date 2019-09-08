---
title: Sincronização de DataSet e XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785420"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="7f9b0-102">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="7f9b0-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="7f9b0-103">O ADO.NET <xref:System.Data.DataSet> fornece uma representação de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="7f9b0-104">Para obter acesso a dados hierárquicos, você pode usar as classes XML disponíveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="7f9b0-105">Historicamente, essas duas representações de dados foram usadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="7f9b0-106">No entanto, o .NET Framework permite o acesso síncrono em tempo real a representações hierárquicas e relacionais de dados por meio do objeto **DataSet** e <xref:System.Xml.XmlDataDocument> do objeto, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="7f9b0-107">Quando um **conjunto** de dados é sincronizado com um **XmlDataDocument**, ambos os objetos estão trabalhando com um único conjunto.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="7f9b0-108">Isso significa que, se uma alteração for feita no **conjunto**de um, a alteração será refletida no **XmlDataDocument**, e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="7f9b0-109">A relação entre o **conjunto** de dados e o **XmlDataDocument** cria uma grande flexibilidade ao permitir que um único aplicativo, usando um único conjunto de dados, acesse o conjunto completo de serviços criados em todo o **DataSet** (como Web Forms e Windows Forms controles e designers do Visual Studio .NET), bem como o conjunto de serviços XML, incluindo XSL (Extensible Stylesheet Language), XSLT (transformações XSL) e XPath (linguagem de caminho XML).</span><span class="sxs-lookup"><span data-stu-id="7f9b0-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="7f9b0-110">Você não tem que escolher qual conjunto de serviços direcionar com o aplicativo; ambos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="7f9b0-111">Há várias maneiras de sincronizar um **conjunto** de uma com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="7f9b0-112">Você pode:</span><span class="sxs-lookup"><span data-stu-id="7f9b0-112">You can:</span></span>  
  
- <span data-ttu-id="7f9b0-113">Popule um **conjunto** de dados com esquema (ou seja, uma estrutura relacional) e sincronize-os com um novo **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="7f9b0-114">Isso fornece uma exibição hierárquica de dados relacionais existentes.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="7f9b0-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7f9b0-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- <span data-ttu-id="7f9b0-116">Popular um **conjunto** de um DataSet somente com esquema (como um **conjunto**de um DataSet com rigidez de tipos), sincronizá-lo com um **XmlDataDocument**e, em seguida, carregar o **XmlDataDocument** de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="7f9b0-117">Isso fornece uma exibição relacional de dados hierárquicos existentes.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="7f9b0-118">Os nomes de tabela e de coluna no seu esquema de conjunto de seus **conjuntos** de itens devem corresponder aos nomes dos elementos XML com os quais você deseja que eles sejam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="7f9b0-119">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="7f9b0-120">Observe que o esquema do **conjunto** de um só precisa corresponder aos elementos XML que você deseja expor em sua exibição relacional.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="7f9b0-121">Dessa maneira, você pode ter um documento XML muito grande e uma "janela" relacional muito pequena nesse documento.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="7f9b0-122">O **XmlDataDocument** preserva todo o documento XML, embora o **conjunto** de os apenas exponha uma pequena parte dele.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="7f9b0-123">(Para obter um exemplo detalhado disso, confira [sincronizando um conjunto de informações com um XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="7f9b0-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="7f9b0-124">O exemplo de código a seguir mostra as etapas para criar um **conjunto** de um e preencher seu esquema e, em seguida, sincronizá-lo com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="7f9b0-125">Observe que o esquema do **conjunto** de um só precisa corresponder aos elementos do **XmlDataDocument** que você deseja expor usando o **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="7f9b0-126">Você não poderá carregar um **XmlDataDocument** se ele estiver sincronizado com um **conjunto** de dados que contenha dado.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="7f9b0-127">Uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="7f9b0-128">Crie um novo **XmlDataDocument** e carregue-o de um documento XML e, em seguida, acesse a exibição relacional dos dados usando a propriedade **DataSet** de **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="7f9b0-129">Você precisa definir o esquema do **conjunto** de dados antes de poder exibir qualquer dado no **XmlDataDocument** usando o **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="7f9b0-130">Novamente, os nomes de tabela e os nomes de coluna no esquema do conjunto de seus **conjuntos** devem corresponder aos nomes dos elementos XML com os quais você deseja que eles sejam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="7f9b0-131">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="7f9b0-132">O exemplo de código a seguir mostra como acessar a exibição relacional dos dados em um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="7f9b0-133">Outra vantagem de sincronizar um **XmlDataDocument** com um **DataSet** é que a fidelidade de um documento XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="7f9b0-134">Se o **conjunto** de dados for populado a partir de um documento XML usando **ReadXml**, quando eles forem gravados como um documento XML usando o **WriteXml** , ele poderá diferir significativamente do documento XML original.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="7f9b0-135">Isso ocorre porque o **conjunto** de dados não mantém a formatação, como o espaço em branco, ou informações hierárquicas, como a ordem dos elementos, a partir do documento XML.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="7f9b0-136">O **conjunto** de os também não contém elementos do documento XML que foram ignorados porque não corresponderam ao esquema do **conjunto**de um.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="7f9b0-137">A sincronização de um **XmlDataDocument** com um **conjunto** de dados permite que a estrutura de elementos de formatação e hierárquica do documento XML original seja mantida no **XmlDataDocument**, enquanto o **conjunto** de dados contém apenas informações de esquema apropriadas para o **conjunto**de dados.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="7f9b0-138">Ao sincronizar um **conjunto** de uma com um **XmlDataDocument**, os resultados podem diferir dependendo se seus <xref:System.Data.DataRelation> objetos estão ou não aninhados.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="7f9b0-139">Para obter mais informações, consulte [aninhando DataRelations](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="7f9b0-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7f9b0-140">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7f9b0-140">In This Section</span></span>  
 [<span data-ttu-id="7f9b0-141">Sincronizando um conjunto de dados com um XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="7f9b0-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="7f9b0-142">Demonstra a sincronização de um conjunto de um **DataSet**com rigidez de tipos, com o esquema mínimo, com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="7f9b0-143">Executar uma consulta XPath em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="7f9b0-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="7f9b0-144">Demonstra como executar uma consulta XPath no conteúdo de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="7f9b0-145">Aplicando uma transformação XSLT a um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="7f9b0-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="7f9b0-146">Demonstra a aplicação de uma transformação XSLT ao conteúdo de um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7f9b0-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7f9b0-147">Related Sections</span></span>  
 <span data-ttu-id="7f9b0-148">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="7f9b0-148">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="7f9b0-149">Descreve como o **DataSet** interage com o XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um **conjunto** de dados como um dado XML.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="7f9b0-150">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="7f9b0-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="7f9b0-151">Discute a importância de objetos **DataRelation** aninhados ao representar o conteúdo de um **DataSet** como dados XML e descreve como criar essas relações.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 <span data-ttu-id="7f9b0-152">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="7f9b0-152">[DataSets, DataTables, and DataViews](index.md)</span></span>  
 <span data-ttu-id="7f9b0-153">Descreve o **DataSet** e como usá-lo para gerenciar dados de aplicativo e interagir com fontes de dados, incluindo bancos de dados relacionais e XML.</span><span class="sxs-lookup"><span data-stu-id="7f9b0-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="7f9b0-154">Contém informações de referência sobre a classe **XmlDataDocument** .</span><span class="sxs-lookup"><span data-stu-id="7f9b0-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9b0-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f9b0-155">See also</span></span>

- <span data-ttu-id="7f9b0-156">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7f9b0-156">[ADO.NET Overview](../ado-net-overview.md)</span></span>
