---
title: Sincronização de DataSet e XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: cb16d4fae5dc153361fe2cb31cfd6af9b4b83c68
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759160"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="0a373-102">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="0a373-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="0a373-103">O ADO.NET <xref:System.Data.DataSet> fornece uma representação de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="0a373-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="0a373-104">Para obter acesso a dados hierárquicos, você pode usar as classes XML disponíveis no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a373-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="0a373-105">Historicamente, essas duas representações de dados foram usadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="0a373-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="0a373-106">No entanto, o .NET Framework permite acesso síncrono em tempo real com ambas as representações relacionais e hierárquicas de dados por meio de **DataSet** objeto e o <xref:System.Xml.XmlDataDocument> do objeto, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0a373-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="0a373-107">Quando um **DataSet** está sincronizado com um **XmlDataDocument**, os dois objetos estiver trabalhando com um único conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="0a373-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="0a373-108">Isso significa que, se uma alteração for feita para o **DataSet**, a alteração será refletida no **XmlDataDocument**e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="0a373-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="0a373-109">A relação entre o **DataSet** e **XmlDataDocument** cria grande flexibilidade, permitindo que um único aplicativo, usando um único conjunto de dados, para acessar todo o pacote de serviços criados em torno de **conjunto de dados** (por exemplo, os controles de formulários da Web e o Windows Forms e designers do Visual Studio .NET), bem como o pacote de serviços XML, incluindo Extensible Stylesheet Language (XSL), transformações de XSL (XSLT) e XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="0a373-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="0a373-110">Você não tem que escolher qual conjunto de serviços direcionar com o aplicativo; ambos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0a373-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="0a373-111">Há várias maneiras que você pode sincronizar um **DataSet** com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="0a373-112">Você pode:</span><span class="sxs-lookup"><span data-stu-id="0a373-112">You can:</span></span>  
  
-   <span data-ttu-id="0a373-113">Preencher um **DataSet** com o esquema (ou seja, uma estrutura relacional) e os dados e, em seguida, sincronizá-lo com um novo **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="0a373-114">Isso fornece uma exibição hierárquica de dados relacionais existentes.</span><span class="sxs-lookup"><span data-stu-id="0a373-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="0a373-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0a373-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="0a373-116">Preencher um **DataSet** somente com esquema (como fortemente tipada **conjunto de dados**), sincronizá-lo com um **XmlDataDocument**e, em seguida, carregue o  **XmlDataDocument** de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="0a373-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="0a373-117">Isso fornece uma exibição relacional de dados hierárquicos existentes.</span><span class="sxs-lookup"><span data-stu-id="0a373-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="0a373-118">Os nomes de tabela e nomes de coluna na sua **DataSet** esquema deve corresponder aos nomes dos elementos XML que deseja que sejam sincronizados com o.</span><span class="sxs-lookup"><span data-stu-id="0a373-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="0a373-119">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0a373-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="0a373-120">Observe que o esquema do **DataSet** só precisa corresponder os elementos XML que você deseja expor no modo de exibição relacional.</span><span class="sxs-lookup"><span data-stu-id="0a373-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="0a373-121">Dessa maneira, você pode ter um documento XML muito grande e uma "janela" relacional muito pequena nesse documento.</span><span class="sxs-lookup"><span data-stu-id="0a373-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="0a373-122">O **XmlDataDocument** preserva o documento XML inteiro, embora o **DataSet** expõe apenas uma pequena parte dele.</span><span class="sxs-lookup"><span data-stu-id="0a373-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="0a373-123">(Para obter um exemplo detalhado de isso, consulte [sincronizando um conjunto de dados com um XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="0a373-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="0a373-124">O exemplo de código a seguir mostra as etapas para criar um **DataSet** preencher seu esquema, e sincronizá-lo com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="0a373-125">Observe que o **DataSet** esquema só precisa corresponder os elementos do **XmlDataDocument** que você deseja expor usando o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="0a373-126">Não é possível carregar um **XmlDataDocument** se ele for sincronizado com um **conjunto de dados** que contém dados.</span><span class="sxs-lookup"><span data-stu-id="0a373-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="0a373-127">Uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="0a373-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="0a373-128">Criar um novo **XmlDataDocument** e carregá-lo de um documento XML e, em seguida, acesse o modo de exibição relacional de dados usando o **DataSet** propriedade o **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="0a373-129">É necessário definir o esquema do **DataSet** antes de exibir os dados no **XmlDataDocument** usando o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="0a373-130">Novamente, os nomes de tabela e coluna nomes no seu **DataSet** esquema deve corresponder aos nomes dos elementos XML que deseja que sejam sincronizados com o.</span><span class="sxs-lookup"><span data-stu-id="0a373-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="0a373-131">Essa correspondência diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0a373-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="0a373-132">O exemplo de código a seguir mostra como acessar o modo de exibição relacional de dados em um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="0a373-133">Outra vantagem da sincronização de um **XmlDataDocument** com um **DataSet** é que a fidelidade de um documento XML é preservada.</span><span class="sxs-lookup"><span data-stu-id="0a373-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="0a373-134">Se o **DataSet** é preenchida com um documento XML usando **ReadXml**, quando os dados são gravados de volta como um documento XML usando **WriteXml** ele pode diferir significativamente a documento XML original.</span><span class="sxs-lookup"><span data-stu-id="0a373-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="0a373-135">Isso ocorre porque o **conjunto de dados** não mantém a formatação, como espaço em branco ou informações hierárquicas, como ordem de elemento do documento XML.</span><span class="sxs-lookup"><span data-stu-id="0a373-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="0a373-136">O **DataSet** também não contém elementos do documento XML que foram ignorados porque elas não coincidiu com o esquema do **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="0a373-137">Sincronizando um **XmlDataDocument** com um **DataSet** permite que a estrutura hierárquica e formatação do elemento do documento XML original seja mantido no **XmlDataDocument**, enquanto o **DataSet** contém apenas informações de esquema e os dados apropriadas para o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="0a373-138">Ao sincronizar um **conjunto de dados** com um **XmlDataDocument**, resultados podem diferir dependendo se deseja ou não o <xref:System.Data.DataRelation> objetos aninhados.</span><span class="sxs-lookup"><span data-stu-id="0a373-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="0a373-139">Para obter mais informações, consulte [aninhamento DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="0a373-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a373-140">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0a373-140">In This Section</span></span>  
 [<span data-ttu-id="0a373-141">Sincronizando um conjunto de dados com um XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="0a373-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="0a373-142">Demonstra a sincronização fortemente tipada **DataSet**, com esquema mínima, com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="0a373-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="0a373-143">Executar uma consulta XPath em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="0a373-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="0a373-144">Demonstra a executar uma consulta XPath no conteúdo de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="0a373-145">Aplicando uma transformação XSLT a um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="0a373-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="0a373-146">Demonstra a aplicação de uma transformação XSLT para o conteúdo de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0a373-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a373-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="0a373-147">Related Sections</span></span>  
 <span data-ttu-id="0a373-148">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="0a373-148">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="0a373-149">Descreve como o **DataSet** interage com o XML como uma fonte de dados, incluindo o carregamento e a manter o conteúdo de um **DataSet** como dados XML.</span><span class="sxs-lookup"><span data-stu-id="0a373-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="0a373-150">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="0a373-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="0a373-151">Descreve a importância de aninhada **DataRelation** objetos ao representar o conteúdo de um **DataSet** como dados XML e descreve como criar essas relações.</span><span class="sxs-lookup"><span data-stu-id="0a373-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 <span data-ttu-id="0a373-152">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="0a373-152">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="0a373-153">Descreve o **DataSet** e como usá-lo para gerenciar dados de aplicativo e interagir com fontes de dados, incluindo bancos de dados relacionais e XML.</span><span class="sxs-lookup"><span data-stu-id="0a373-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="0a373-154">Contém informações de referência sobre o **XmlDataDocument** classe.</span><span class="sxs-lookup"><span data-stu-id="0a373-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a373-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a373-155">See Also</span></span>  
 <span data-ttu-id="0a373-156">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0a373-156">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
