---
title: "conjunto de associações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db293cbc636d0ae4e532f24b2852444395f603c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="association-set"></a><span data-ttu-id="4e8a6-102">conjunto de associações</span><span class="sxs-lookup"><span data-stu-id="4e8a6-102">association set</span></span>
<span data-ttu-id="4e8a6-103">Um *conjunto de associações* é um contêiner lógico para [associação](../../../../docs/framework/data/adonet/association-type.md) instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="4e8a6-104">Um conjunto de associações não é um dados que modelam a compilação; isto é, não descreve a estrutura de dados ou relações.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="4e8a6-105">Em vez disso, um conjunto de associações fornece uma compilação para um ambiente de hospedagem ou de armazenamento (como Common Language Runtime ou um base de dados SQL Server) às instâncias de associação do grupo de modo que eles possam ser mapeadas em um armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="4e8a6-106">Um conjunto de associação é definido dentro de um [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md), que é um agrupamento lógico de [conjuntos de entidades](../../../../docs/framework/data/adonet/entity-set.md) e conjuntos de associação.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="4e8a6-107">Uma definição de um conjunto de associações contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e8a6-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="4e8a6-108">O nome de conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-108">The association set name.</span></span> <span data-ttu-id="4e8a6-109">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="4e8a6-109">(Required)</span></span>  
  
-   <span data-ttu-id="4e8a6-110">A associação de que irá conter instâncias.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-110">The association of which it will contain instances.</span></span> <span data-ttu-id="4e8a6-111">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="4e8a6-111">(Required)</span></span>  
  
-   <span data-ttu-id="4e8a6-112">Dois [extremidades do conjunto de associação](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="4e8a6-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e8a6-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e8a6-113">Example</span></span>  
 <span data-ttu-id="4e8a6-114">O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy`, e `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="4e8a6-115">Embora informações sobre conjuntos de associações não é transmitida no diagrama, o diagrama a seguir mostra um exemplo de conjuntos de associações e conjuntos de entidades baseados nesse modelo.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="4e8a6-116">![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="4e8a6-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="4e8a6-117">O exemplo a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="4e8a6-118">BI no `Books` conjunto de entidade representa uma ocorrência da `Book` tipo de entidade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="4e8a6-119">Da mesma forma, Pj representa um `Publisher` de instância de `Publishers` conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="4e8a6-120">BiPj representa uma ocorrência da `PublishedBy` associação no `PublishedBy` conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="4e8a6-121">![Exemplo](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="4e8a6-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="4e8a6-122">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4e8a6-123">CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="4e8a6-124">Observe que o nome e a associação para cada conjunto de associações são definidos usando atributos XML.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="4e8a6-125">É possível definir vários conjuntos de associação por associação, contanto que nenhum compartilhamento de conjuntos de dois associação um [final do conjunto de associação](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="4e8a6-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="4e8a6-126">CSDL seguir define um contêiner de entidade com dois conjuntos de associações para associação de `WrittenBy` .</span><span class="sxs-lookup"><span data-stu-id="4e8a6-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="4e8a6-127">Observe que os vários conjuntos de entidades foram definidos para os tipos de entidade de `Book` e de `Author` e que nenhum conjunto de associações compartilha fim do conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="4e8a6-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="4e8a6-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e8a6-128">See Also</span></span>  
 [<span data-ttu-id="4e8a6-129">Conceitos chave do modelo de dados de entidade</span><span class="sxs-lookup"><span data-stu-id="4e8a6-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="4e8a6-130">Modelo de dados de entidade</span><span class="sxs-lookup"><span data-stu-id="4e8a6-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="4e8a6-131">propriedade de chave estrangeira</span><span class="sxs-lookup"><span data-stu-id="4e8a6-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
