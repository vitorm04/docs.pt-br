---
title: extremidade do conjunto de associação
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786935"
---
# <a name="association-set-end"></a><span data-ttu-id="8287a-102">extremidade do conjunto de associação</span><span class="sxs-lookup"><span data-stu-id="8287a-102">association set end</span></span>
<span data-ttu-id="8287a-103">Uma *extremidade de conjunto de associação* identifica o [tipo de entidade](entity-type.md) e a [entidade definida](entity-set.md) no final de um [conjunto de associação](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="8287a-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="8287a-104">Termina do conjunto de associações são definidas como parte de um conjunto de associações; um conjunto de associações deve ter exatamente duas termina do conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="8287a-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="8287a-105">Uma definição de final do conjunto de associações contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="8287a-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="8287a-106">Um dos tipos de entidade envolvidos no conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="8287a-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="8287a-107">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="8287a-107">(Required)</span></span>  
  
- <span data-ttu-id="8287a-108">O conjunto de entidades para o tipo de entidade envolvido no conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="8287a-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="8287a-109">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="8287a-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="8287a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8287a-110">Example</span></span>  
 <span data-ttu-id="8287a-111">O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="8287a-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="8287a-113">O diagrama a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="8287a-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="8287a-114">Termina do conjunto de associações são conjuntos de entidades de `Books` e de `Publishers` .</span><span class="sxs-lookup"><span data-stu-id="8287a-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="8287a-115">Bi no conjunto `Books` de entidades representa uma instância `Book` do tipo de entidade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8287a-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="8287a-116">Da mesma forma, PJ `Publisher` representa uma instância `Publishers` no conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="8287a-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="8287a-117">BiPj representa uma instância da `PublishedBy` Associação `PublishedBy` no conjunto de associação.</span><span class="sxs-lookup"><span data-stu-id="8287a-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Captura de tela que mostra um exemplo de conjuntos.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="8287a-119">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL chamada linguagem de definição de esquema conceitual ([CSDL](./ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="8287a-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8287a-120">CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="8287a-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="8287a-121">Observe que termina do conjunto de associações são definidas como parte de cada definição do conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="8287a-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="8287a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8287a-122">See also</span></span>

- [<span data-ttu-id="8287a-123">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="8287a-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="8287a-124">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="8287a-124">Entity Data Model</span></span>](entity-data-model.md)
