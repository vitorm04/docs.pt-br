---
title: tipo de entidade
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 3f99667a06d8aa439232802d4909290dfe9db97c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194772"
---
# <a name="entity-type"></a><span data-ttu-id="33e73-102">tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="33e73-102">entity type</span></span>

<span data-ttu-id="33e73-103">O *tipo de entidade* é o bloco de construção fundamental para descrever a estrutura de dados com o modelo de dados de entidade (EDM).</span><span class="sxs-lookup"><span data-stu-id="33e73-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="33e73-104">Em um modelo conceitual, um tipo de entidade representa a estrutura dos conceitos de nível superior, como clientes ou pedidos.</span><span class="sxs-lookup"><span data-stu-id="33e73-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="33e73-105">Um tipo de entidade é um modelo para instâncias do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="33e73-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="33e73-106">Cada modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="33e73-106">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="33e73-107">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="33e73-107">A unique name.</span></span> <span data-ttu-id="33e73-108">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="33e73-108">(Required.)</span></span>  
  
- <span data-ttu-id="33e73-109">Uma [chave de entidade](entity-key.md) definida por uma ou mais propriedades.</span><span class="sxs-lookup"><span data-stu-id="33e73-109">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="33e73-110">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="33e73-110">(Required.)</span></span>  
  
- <span data-ttu-id="33e73-111">Dados na forma de [Propriedades](property.md).</span><span class="sxs-lookup"><span data-stu-id="33e73-111">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="33e73-112">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="33e73-112">(Optional.)</span></span>  
  
- <span data-ttu-id="33e73-113">[Propriedades de navegação](navigation-property.md) que permitem a navegação de uma [extremidade](association-end.md) de uma [Associação](association-type.md) para a outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="33e73-113">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="33e73-114">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="33e73-114">(Optional)</span></span>  
  
 <span data-ttu-id="33e73-115">Em um aplicativo, uma instância de um tipo de entidade representa um objeto específico (como um cliente ou uma ordem específica.)</span><span class="sxs-lookup"><span data-stu-id="33e73-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="33e73-116">Cada instância de um tipo de entidade deve ter uma [chave de entidade](entity-key.md) exclusiva dentro de um [conjunto de entidades](entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="33e73-116">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="33e73-117">Duas instâncias do tipo de entidade são consideradas iguais somente se são do mesmo tipo e os valores das chaves de entidade são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="33e73-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33e73-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33e73-118">Example</span></span>  

 <span data-ttu-id="33e73-119">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`:</span><span class="sxs-lookup"><span data-stu-id="33e73-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="33e73-121">Observe que as propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”).</span><span class="sxs-lookup"><span data-stu-id="33e73-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="33e73-122">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="33e73-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="33e73-123">CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:</span><span class="sxs-lookup"><span data-stu-id="33e73-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="33e73-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="33e73-124">See also</span></span>

- [<span data-ttu-id="33e73-125">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="33e73-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="33e73-126">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="33e73-126">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="33e73-127">particular</span><span class="sxs-lookup"><span data-stu-id="33e73-127">facet</span></span>](facet.md)
