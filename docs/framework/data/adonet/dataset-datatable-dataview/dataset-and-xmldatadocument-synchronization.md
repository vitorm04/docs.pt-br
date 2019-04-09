---
title: Sincronização de DataSet e XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: ea597d7caca3174b17ce16a1e9d70c022e3e75c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164730"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="76b7f-102">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="76b7f-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="76b7f-103">O ADO.NET <xref:System.Data.DataSet> fornece uma representação de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="76b7f-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="76b7f-104">Para obter acesso a dados hierárquicos, você pode usar as classes XML disponíveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76b7f-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="76b7f-105">Historicamente, essas duas representações de dados foram usadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="76b7f-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="76b7f-106">No entanto, o .NET Framework permite acesso síncrono em tempo real às representações relacionais e hierárquicas de dados por meio de **DataSet** objeto e o <xref:System.Xml.XmlDataDocument> do objeto, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="76b7f-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="76b7f-107">Quando um **DataSet** está sincronizado com um **XmlDataDocument**, ambos os objetos estão trabalhando com um único conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="76b7f-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="76b7f-108">Isso significa que, se uma alteração for feita para o **DataSet**, a alteração será refletida na **XmlDataDocument**e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="76b7f-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="76b7f-109">A relação entre o **DataSet** e o **XmlDataDocument** cria grande flexibilidade, permitindo que um único aplicativo, usando um único conjunto de dados, para acessar o pacote completo de serviços internos em torno de **conjunto de dados** (como controles de Web Forms e Windows Forms e designers do Visual Studio .NET), bem como o pacote de serviços XML, incluindo Extensible Stylesheet Language (XSL), as transformações de XSL (XSLT) e o caminho de XML Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="76b7f-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="76b7f-110">Você não tem que escolher qual conjunto de serviços direcionar com o aplicativo; ambos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="76b7f-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="76b7f-111">Há várias maneiras que você pode sincronizar uma **DataSet** com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="76b7f-112">Você pode:</span><span class="sxs-lookup"><span data-stu-id="76b7f-112">You can:</span></span>  
  
-   <span data-ttu-id="76b7f-113">Preencher uma **DataSet** com o esquema (ou seja, uma estrutura relacional) e os dados e, em seguida, sincronizá-lo com uma nova **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="76b7f-114">Isso fornece uma exibição hierárquica de dados relacionais existentes.</span><span class="sxs-lookup"><span data-stu-id="76b7f-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="76b7f-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="76b7f-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="76b7f-116">Preencher uma **conjunto de dados** somente com esquema (como fortemente tipado **DataSet**), sincronizá-lo com um **XmlDataDocument**e, em seguida, carregue o  **XmlDataDocument** de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="76b7f-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="76b7f-117">Isso fornece uma exibição relacional de dados hierárquicos existentes.</span><span class="sxs-lookup"><span data-stu-id="76b7f-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="76b7f-118">Os nomes de tabela e nomes de coluna em sua **conjunto de dados** esquema deve corresponder aos nomes dos elementos XML que você deseja que eles sincronizados com o.</span><span class="sxs-lookup"><span data-stu-id="76b7f-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="76b7f-119">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="76b7f-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="76b7f-120">Observe que o esquema do **conjunto de dados** somente precisa corresponder os elementos XML que você deseja expor na sua exibição relacional.</span><span class="sxs-lookup"><span data-stu-id="76b7f-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="76b7f-121">Dessa maneira, você pode ter um documento XML muito grande e uma "janela" relacional muito pequena nesse documento.</span><span class="sxs-lookup"><span data-stu-id="76b7f-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="76b7f-122">O **XmlDataDocument** preserva todo o documento XML, embora o **conjunto de dados** expõe apenas uma pequena parte dele.</span><span class="sxs-lookup"><span data-stu-id="76b7f-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="76b7f-123">(Para obter um exemplo detalhado disso, consulte [sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="76b7f-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="76b7f-124">O exemplo de código a seguir mostra as etapas para criar uma **DataSet** e preencher seu esquema e, em seguida, sincronizá-lo com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="76b7f-125">Observe que o **DataSet** esquema somente precisa corresponder os elementos da **XmlDataDocument** que você deseja expor usando o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="76b7f-126">Você não pode carregar uma **XmlDataDocument** se ele estiver sincronizado com um **conjunto de dados** que contém os dados.</span><span class="sxs-lookup"><span data-stu-id="76b7f-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="76b7f-127">Uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="76b7f-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="76b7f-128">Criar um novo **XmlDataDocument** e carregá-lo de um documento XML e, em seguida, acessar a exibição relacional dos dados usando o **DataSet** propriedade do **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="76b7f-129">Você precisa definir o esquema do **DataSet** antes de exibir os dados no **XmlDataDocument** usando o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="76b7f-130">Novamente, os nomes de tabela e das colunas em sua **conjunto de dados** esquema deve corresponder aos nomes dos elementos XML que você deseja que eles sincronizados com o.</span><span class="sxs-lookup"><span data-stu-id="76b7f-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="76b7f-131">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="76b7f-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="76b7f-132">O exemplo de código a seguir mostra como acessar a exibição relacional dos dados em um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="76b7f-133">Outra vantagem da sincronização de um **XmlDataDocument** com um **conjunto de dados** é que a fidelidade de um documento XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="76b7f-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="76b7f-134">Se o **DataSet** é populado de um documento XML usando **ReadXml**, quando os dados forem escritos novamente como um documento XML usando **WriteXml** poderão diferir bastante das documento XML original.</span><span class="sxs-lookup"><span data-stu-id="76b7f-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="76b7f-135">Isso ocorre porque o **conjunto de dados** não mantém a formatação, como espaço em branco ou informações hierárquicas, como a ordem dos elementos, do documento XML.</span><span class="sxs-lookup"><span data-stu-id="76b7f-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="76b7f-136">O **DataSet** também não contém elementos do documento XML que foram ignorados porque eles não correspondeu ao esquema da **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="76b7f-137">Sincronizando um **XmlDataDocument** com um **DataSet** permite que a estrutura hierárquica e formatação do elemento do documento XML original seja mantido no **XmlDataDocument**, enquanto a **DataSet** contém apenas informações de dados e o esquema apropriadas para o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="76b7f-138">Durante a sincronização de uma **DataSet** com um **XmlDataDocument**, os resultados poderão diferir dependendo se deseja ou não seu <xref:System.Data.DataRelation> objetos são aninhados.</span><span class="sxs-lookup"><span data-stu-id="76b7f-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="76b7f-139">Para obter mais informações, consulte [aninhamento de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="76b7f-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76b7f-140">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="76b7f-140">In This Section</span></span>  
 [<span data-ttu-id="76b7f-141">Sincronizar um DataSet com um XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="76b7f-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="76b7f-142">Demonstra a sincronização fortemente tipado **DataSet**, com esquema mínimo, com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="76b7f-143">Executar uma consulta XPath em um DataSet</span><span class="sxs-lookup"><span data-stu-id="76b7f-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="76b7f-144">Demonstra a execução de uma consulta XPath no conteúdo de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="76b7f-145">Aplicar uma transformação XSLT a um DataSet</span><span class="sxs-lookup"><span data-stu-id="76b7f-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="76b7f-146">Demonstra a aplicação de uma transformação XSLT ao conteúdo de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="76b7f-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76b7f-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="76b7f-147">Related Sections</span></span>  
 [<span data-ttu-id="76b7f-148">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="76b7f-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="76b7f-149">Descreve como o **DataSet** interage com XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um **conjunto de dados** como dados XML.</span><span class="sxs-lookup"><span data-stu-id="76b7f-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="76b7f-150">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="76b7f-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="76b7f-151">Descreve a importância de aninhados **DataRelation** objetos ao representar o conteúdo de um **conjunto de dados** como dados XML e descreve como criar essas relações.</span><span class="sxs-lookup"><span data-stu-id="76b7f-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="76b7f-152">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="76b7f-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="76b7f-153">Descreve o **conjunto de dados** e como usá-lo para gerenciar dados de aplicativo e interagir com fontes de dados, incluindo bancos de dados relacionais e XML.</span><span class="sxs-lookup"><span data-stu-id="76b7f-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="76b7f-154">Contém informações de referência sobre as **XmlDataDocument** classe.</span><span class="sxs-lookup"><span data-stu-id="76b7f-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b7f-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76b7f-155">See also</span></span>

- [<span data-ttu-id="76b7f-156">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="76b7f-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
