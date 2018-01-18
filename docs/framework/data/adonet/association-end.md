---
title: "extremidade de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ffa768f50b3a80c22b4c84cffaf42897193a7d9f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="association-end"></a><span data-ttu-id="d94a0-102">extremidade de associação</span><span class="sxs-lookup"><span data-stu-id="d94a0-102">association end</span></span>
<span data-ttu-id="d94a0-103">Um *end de associação* identifica o [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) em uma extremidade de um [associação](../../../../docs/framework/data/adonet/association-type.md) e o número de entidades que final de uma associação de tipo instâncias que podem existir.</span><span class="sxs-lookup"><span data-stu-id="d94a0-103">An *association end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) on one end of an [association](../../../../docs/framework/data/adonet/association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="d94a0-104">Termina de associação são definidas como parte de uma associação; uma associação deve ter exatamente duas termina de associação.</span><span class="sxs-lookup"><span data-stu-id="d94a0-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="d94a0-105">[Propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) permitir a navegação de uma extremidade de associação para o outro.</span><span class="sxs-lookup"><span data-stu-id="d94a0-105">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="d94a0-106">Uma definição de fim de associação contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="d94a0-106">An association end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="d94a0-107">Um dos tipos de entidade envolvidos na associação.</span><span class="sxs-lookup"><span data-stu-id="d94a0-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="d94a0-108">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="d94a0-108">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d94a0-109">Para uma associação determinada, o tipo de entidade especificada para cada o final da associação pode ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="d94a0-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="d94a0-110">Isso cria uma dica associação.</span><span class="sxs-lookup"><span data-stu-id="d94a0-110">This creates a self-association.</span></span>  
  
-   <span data-ttu-id="d94a0-111">Um [multiplicidade da extremidade da associação](../../../../docs/framework/data/adonet/association-end-multiplicity.md) que indica o número de instâncias de tipo de entidade que pode estar em uma extremidade da associação.</span><span class="sxs-lookup"><span data-stu-id="d94a0-111">An [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="d94a0-112">Uma multiplicidade de extremidades de associação pode ter um valor igual a um (1), a zero ou a um (0..1) ou a muitos (\*).</span><span class="sxs-lookup"><span data-stu-id="d94a0-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
-   <span data-ttu-id="d94a0-113">Um nome para o final da associação.</span><span class="sxs-lookup"><span data-stu-id="d94a0-113">A name for the association end.</span></span> <span data-ttu-id="d94a0-114">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="d94a0-114">(Optional)</span></span>  
  
-   <span data-ttu-id="d94a0-115">Informações sobre as operações que são executadas no final da associação, como em cascata exclusão.</span><span class="sxs-lookup"><span data-stu-id="d94a0-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="d94a0-116">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="d94a0-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="d94a0-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d94a0-117">Example</span></span>  
 <span data-ttu-id="d94a0-118">O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="d94a0-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="d94a0-119">Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` .</span><span class="sxs-lookup"><span data-stu-id="d94a0-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="d94a0-120">A multiplicidade do final de `Publisher` é um (1) e a multiplicidade do final de `Book` é muitas (\*), indicando que publica um editor muitos livros e um livro é publicado por um editor.</span><span class="sxs-lookup"><span data-stu-id="d94a0-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="d94a0-121">![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="d94a0-121">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="d94a0-122">O ADO.NET Entity Framework usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="d94a0-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d94a0-123">CSDL a seguir define a associação de `PublishedBy` mostrada no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="d94a0-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="d94a0-124">Observe que o tipo, nome, e a multiplicidade de cada o final da associação são especificados por atributos XML ( `Type`, `Role`, e atributos de `Multiplicity` , respectivamente).</span><span class="sxs-lookup"><span data-stu-id="d94a0-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="d94a0-125">Opcional informações sobre as operações executadas em uma extremidade é especificado em um elemento XML (o elemento de `OnDelete` ).</span><span class="sxs-lookup"><span data-stu-id="d94a0-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="d94a0-126">Nesse caso, se um editor é excluído, é para todos livros associados.</span><span class="sxs-lookup"><span data-stu-id="d94a0-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="d94a0-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d94a0-127">See Also</span></span>  
 [<span data-ttu-id="d94a0-128">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="d94a0-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="d94a0-129">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="d94a0-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
