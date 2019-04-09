---
title: tipo de entidade
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 026b0aef7cf2de8fe222721191afa459859701ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108258"
---
# <a name="entity-type"></a><span data-ttu-id="5a95f-102">tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="5a95f-102">entity type</span></span>
<span data-ttu-id="5a95f-103">O *tipo de entidade* é o bloco de construção fundamental para descrever a estrutura de dados com o modelo de dados de entidade (EDM).</span><span class="sxs-lookup"><span data-stu-id="5a95f-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="5a95f-104">Em um modelo conceitual, um tipo de entidade representa a estrutura dos conceitos de nível superior, como clientes ou pedidos.</span><span class="sxs-lookup"><span data-stu-id="5a95f-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="5a95f-105">Um tipo de entidade é um modelo para instâncias do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="5a95f-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="5a95f-106">Cada modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="5a95f-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="5a95f-107">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="5a95f-107">A unique name.</span></span> <span data-ttu-id="5a95f-108">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="5a95f-108">(Required.)</span></span>  
  
-   <span data-ttu-id="5a95f-109">Uma [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md) definido por uma ou mais propriedades.</span><span class="sxs-lookup"><span data-stu-id="5a95f-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="5a95f-110">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="5a95f-110">(Required.)</span></span>  
  
-   <span data-ttu-id="5a95f-111">Dados na forma de [propriedades](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="5a95f-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="5a95f-112">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="5a95f-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="5a95f-113">[Propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) que permite a navegação de um [finais](../../../../docs/framework/data/adonet/association-end.md) de uma [associação](../../../../docs/framework/data/adonet/association-type.md) para a outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="5a95f-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="5a95f-114">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="5a95f-114">(Optional)</span></span>  
  
 <span data-ttu-id="5a95f-115">Em um aplicativo, uma instância de um tipo de entidade representa um objeto específico (como um cliente ou uma ordem específica.)</span><span class="sxs-lookup"><span data-stu-id="5a95f-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="5a95f-116">Cada instância de um tipo de entidade deve ter um único [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md) dentro de uma [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="5a95f-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="5a95f-117">Duas instâncias do tipo de entidade são consideradas iguais somente se são do mesmo tipo e os valores das chaves de entidade são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="5a95f-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a95f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a95f-118">Example</span></span>  
 <span data-ttu-id="5a95f-119">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`:</span><span class="sxs-lookup"><span data-stu-id="5a95f-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="5a95f-121">Observe que as propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”).</span><span class="sxs-lookup"><span data-stu-id="5a95f-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="5a95f-122">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="5a95f-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5a95f-123">CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:</span><span class="sxs-lookup"><span data-stu-id="5a95f-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5a95f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a95f-124">See also</span></span>

- [<span data-ttu-id="5a95f-125">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="5a95f-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="5a95f-126">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="5a95f-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="5a95f-127">facet</span><span class="sxs-lookup"><span data-stu-id="5a95f-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
