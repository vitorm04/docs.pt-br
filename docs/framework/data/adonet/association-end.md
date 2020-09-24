---
title: extremidade de associação
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 00e3a7d855957ae539ea652dc8cde3ed8841dda5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153437"
---
# <a name="association-end"></a><span data-ttu-id="7d700-102">extremidade de associação</span><span class="sxs-lookup"><span data-stu-id="7d700-102">association end</span></span>

<span data-ttu-id="7d700-103">Uma *extremidade de associação* identifica o [tipo de entidade](entity-type.md) em uma extremidade de uma [Associação](association-type.md) e o número de instâncias de tipo de entidade que podem existir no final de uma associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-103">An *association end* identifies the [entity type](entity-type.md) on one end of an [association](association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="7d700-104">Termina de associação são definidas como parte de uma associação; uma associação deve ter exatamente duas termina de associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="7d700-105">[As propriedades de navegação](navigation-property.md) permitem a navegação de uma extremidade de associação para a outra.</span><span class="sxs-lookup"><span data-stu-id="7d700-105">[Navigation properties](navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="7d700-106">Uma definição de fim de associação contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="7d700-106">An association end definition contains the following information:</span></span>  
  
- <span data-ttu-id="7d700-107">Um dos tipos de entidade envolvidos na associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="7d700-108">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="7d700-108">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7d700-109">Para uma associação determinada, o tipo de entidade especificada para cada o final da associação pode ser o mesmo.</span><span class="sxs-lookup"><span data-stu-id="7d700-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="7d700-110">Isso cria uma dica associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-110">This creates a self-association.</span></span>  
  
- <span data-ttu-id="7d700-111">Uma [multiplicidade de extremidade de associação](association-end-multiplicity.md) que indica o número de instâncias de tipo de entidade que podem estar em uma extremidade da associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-111">An [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="7d700-112">Uma multiplicidade de extremidade de associação pode ter um valor de um (1), zero ou um (0.. 1) ou muitos ( \* ).</span><span class="sxs-lookup"><span data-stu-id="7d700-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
- <span data-ttu-id="7d700-113">Um nome para o final da associação.</span><span class="sxs-lookup"><span data-stu-id="7d700-113">A name for the association end.</span></span> <span data-ttu-id="7d700-114">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="7d700-114">(Optional)</span></span>  
  
- <span data-ttu-id="7d700-115">Informações sobre as operações que são executadas no final da associação, como em cascata exclusão.</span><span class="sxs-lookup"><span data-stu-id="7d700-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="7d700-116">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="7d700-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d700-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d700-117">Example</span></span>  

 <span data-ttu-id="7d700-118">O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="7d700-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="7d700-119">Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` .</span><span class="sxs-lookup"><span data-stu-id="7d700-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="7d700-120">A multiplicidade do `Publisher` final é um (1) e a multiplicidade do `Book` final é Many ( \* ), indicando que um Publicador publica muitos livros e um livro é publicado por um Publicador.</span><span class="sxs-lookup"><span data-stu-id="7d700-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="7d700-122">O Entity Framework ADO.NET usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="7d700-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="7d700-123">CSDL a seguir define a associação de `PublishedBy` mostrada no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="7d700-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="7d700-124">Observe que o tipo, nome, e a multiplicidade de cada o final da associação são especificados por atributos XML ( `Type`, `Role`, e atributos de `Multiplicity` , respectivamente).</span><span class="sxs-lookup"><span data-stu-id="7d700-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="7d700-125">Opcional informações sobre as operações executadas em uma extremidade é especificado em um elemento XML (o elemento de `OnDelete` ).</span><span class="sxs-lookup"><span data-stu-id="7d700-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="7d700-126">Nesse caso, se um editor é excluído, é para todos livros associados.</span><span class="sxs-lookup"><span data-stu-id="7d700-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="7d700-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d700-127">See also</span></span>

- [<span data-ttu-id="7d700-128">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="7d700-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7d700-129">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="7d700-129">Entity Data Model</span></span>](entity-data-model.md)
