---
title: Usando XML em um DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b4e29a83efaf351ca954493f4dad2bb0fa0bc1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="f053c-102">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="f053c-102">Using XML in a DataSet</span></span>
<span data-ttu-id="f053c-103">Com o ADO.NET, você pode preencher um <xref:System.Data.DataSet> de um fluxo XML ou documento.</span><span class="sxs-lookup"><span data-stu-id="f053c-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="f053c-104">Você pode usar o fluxo XML ou o documento para fornecer ao <xref:System.Data.DataSet> os dados, as informações de esquema ou ambos.</span><span class="sxs-lookup"><span data-stu-id="f053c-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="f053c-105">As informações fornecidas do fluxo XML ou documento podem ser combinadas com os dados existentes ou informações do esquema presentes no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f053c-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="f053c-106">O ADO.NET também permite criar uma representação XML de um <xref:System.Data.DataSet>, com ou sem o esquema, para transportar o <xref:System.Data.DataSet> por HTTP para ser usado por outro aplicativo ou plataforma habilitada para XML.</span><span class="sxs-lookup"><span data-stu-id="f053c-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="f053c-107">Em uma representação de um <xref:System.Data.DataSet>, os dados são gravados em XML e o esquema, se estiver embutido na representação, é escrito usando a linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="f053c-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="f053c-108">O XML e o esquema XML fornecem um formato conveniente para transferir o conteúdo de um <xref:System.Data.DataSet> para e de clientes remotos.</span><span class="sxs-lookup"><span data-stu-id="f053c-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f053c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f053c-109">In This Section</span></span>  
 [<span data-ttu-id="f053c-110">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="f053c-110">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 <span data-ttu-id="f053c-111">Fornece detalhes sobre o DiffGram, um formato XML usado para ler e gravar o conteúdo de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f053c-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="f053c-112">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="f053c-112">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 <span data-ttu-id="f053c-113">Discute as diferentes opções a serem consideradas ao carregar o conteúdo de um <xref:System.Data.DataSet> de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f053c-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="f053c-114">Gravar o conteúdo do conjunto de dados como dados XML</span><span class="sxs-lookup"><span data-stu-id="f053c-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="f053c-115">Descreve como gerar o conteúdo de um <xref:System.Data.DataSet> como dados XML e as diferentes opções de formato XML que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="f053c-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="f053c-116">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="f053c-116">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="f053c-117">Discute os métodos <xref:System.Data.DataSet> usados para carregar o esquema de um <xref:System.Data.DataSet> do XML.</span><span class="sxs-lookup"><span data-stu-id="f053c-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="f053c-118">Gravando informações de esquema de conjunto de dados como XSD</span><span class="sxs-lookup"><span data-stu-id="f053c-118">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="f053c-119">Discute os usos para um esquema XML e como gerar um de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="f053c-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="f053c-120">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="f053c-120">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="f053c-121">Descreve o recurso disponível no .NET Framework de acesso síncrono para as exibições relacionais e hierárquicas de um único conjunto de dados, e mostra como criar uma relação síncrona entre um <xref:System.Data.DataSet> e um <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="f053c-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="f053c-122">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="f053c-122">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="f053c-123">Descreve a importância de objetos <xref:System.Data.DataRelation> aninhados ao representar o conteúdo de um <xref:System.Data.DataSet> como dados XML e descreve como criá-los.</span><span class="sxs-lookup"><span data-stu-id="f053c-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="f053c-124">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="f053c-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="f053c-125">Descreve a estrutura relacional ou o esquema de um <xref:System.Data.DataSet>, que é criado a partir do esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f053c-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="f053c-126">Derivando a estrutura relacional do DataSet do esquema XML</span><span class="sxs-lookup"><span data-stu-id="f053c-126">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="f053c-127">Descreve a estrutura relacional ou o esquema resultante de um <xref:System.Data.DataSet>, criado quando é inferido de elementos XML.</span><span class="sxs-lookup"><span data-stu-id="f053c-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f053c-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f053c-128">Related Sections</span></span>  
 <span data-ttu-id="f053c-129">[ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f053c-129">[ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md)</span></span>  
 <span data-ttu-id="f053c-130">Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes assim como para gerenciar dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f053c-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f053c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f053c-131">See Also</span></span>  
 <span data-ttu-id="f053c-132">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="f053c-132">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="f053c-133">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f053c-133">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
