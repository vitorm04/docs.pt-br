---
title: extremidade do conjunto de associação
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 61dc00e6c349a25767f6221bed56ef8b65f823d9
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412000"
---
# <a name="association-set-end"></a><span data-ttu-id="6acaf-102">extremidade do conjunto de associação</span><span class="sxs-lookup"><span data-stu-id="6acaf-102">association set end</span></span>
<span data-ttu-id="6acaf-103">Uma *final do conjunto de associações* identifica a [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) e o [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md) no final de uma [conjunto de associações](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="6acaf-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="6acaf-104">Termina do conjunto de associações são definidas como parte de um conjunto de associações; um conjunto de associações deve ter exatamente duas termina do conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="6acaf-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="6acaf-105">Uma definição de final do conjunto de associações contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="6acaf-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="6acaf-106">Um dos tipos de entidade envolvidos no conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="6acaf-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="6acaf-107">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="6acaf-107">(Required)</span></span>  
  
-   <span data-ttu-id="6acaf-108">O conjunto de entidades para o tipo de entidade envolvido no conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="6acaf-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="6acaf-109">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="6acaf-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="6acaf-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6acaf-110">Example</span></span>  
 <span data-ttu-id="6acaf-111">O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="6acaf-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="6acaf-113">O diagrama a seguir mostra um conjunto de associações (`PublishedBy`) e dois conjuntos de entidades (`Books` e `Publishers`) com base no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="6acaf-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="6acaf-114">Termina do conjunto de associações são conjuntos de entidades de `Books` e de `Publishers` .</span><span class="sxs-lookup"><span data-stu-id="6acaf-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="6acaf-115">BI na `Books` conjunto de entidades representa uma instância das `Book` tipo de entidade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6acaf-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="6acaf-116">Da mesma forma, Pj representa uma `Publisher` da instância no `Publishers` conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="6acaf-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="6acaf-117">BiPj representa uma instância das `PublishedBy` associação no `PublishedBy` conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="6acaf-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Captura de tela que mostra um exemplo de conjuntos.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="6acaf-119">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa DSL chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="6acaf-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="6acaf-120">CSDL seguir define um contêiner de entidade com um conjunto de associações para cada associação no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="6acaf-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="6acaf-121">Observe que termina do conjunto de associações são definidas como parte de cada definição do conjunto de associações.</span><span class="sxs-lookup"><span data-stu-id="6acaf-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="6acaf-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6acaf-122">See also</span></span>
- [<span data-ttu-id="6acaf-123">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="6acaf-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="6acaf-124">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="6acaf-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
