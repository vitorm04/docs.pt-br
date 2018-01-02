---
title: tipo de entidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dd1a669b81b9dbbb54b83d13dbb7c0ba7ce3f5cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="entity-type"></a><span data-ttu-id="3fb4e-102">tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="3fb4e-102">entity type</span></span>
<span data-ttu-id="3fb4e-103">O *tipo de entidade* é o bloco de construção fundamental para descrever a estrutura de dados com modelo de dados de entidade (EDM).</span><span class="sxs-lookup"><span data-stu-id="3fb4e-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="3fb4e-104">Em um modelo conceitual, um tipo de entidade representa a estrutura dos conceitos de nível superior, como clientes ou pedidos.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="3fb4e-105">Um tipo de entidade é um modelo para instâncias do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="3fb4e-106">Cada modelo contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="3fb4e-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="3fb4e-107">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-107">A unique name.</span></span> <span data-ttu-id="3fb4e-108">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="3fb4e-108">(Required.)</span></span>  
  
-   <span data-ttu-id="3fb4e-109">Um [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) definido por uma ou mais propriedades.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="3fb4e-110">(Obrigatório.)</span><span class="sxs-lookup"><span data-stu-id="3fb4e-110">(Required.)</span></span>  
  
-   <span data-ttu-id="3fb4e-111">Os dados na forma de [propriedades](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="3fb4e-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="3fb4e-112">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="3fb4e-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="3fb4e-113">[Propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) que permitem de navegação de um [final](../../../../docs/framework/data/adonet/association-end.md) de um [associação](../../../../docs/framework/data/adonet/association-type.md) para a outra.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="3fb4e-114">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="3fb4e-114">(Optional)</span></span>  
  
 <span data-ttu-id="3fb4e-115">Em um aplicativo, uma instância de um tipo de entidade representa um objeto específico (como um cliente ou uma ordem específica.)</span><span class="sxs-lookup"><span data-stu-id="3fb4e-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="3fb4e-116">Cada instância de um tipo de entidade deve ter uma única [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) dentro de um [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="3fb4e-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="3fb4e-117">Duas instâncias do tipo de entidade são consideradas iguais somente se são do mesmo tipo e os valores das chaves de entidade são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fb4e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3fb4e-118">Example</span></span>  
 <span data-ttu-id="3fb4e-119">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`:</span><span class="sxs-lookup"><span data-stu-id="3fb4e-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 <span data-ttu-id="3fb4e-120">![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="3fb4e-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="3fb4e-121">Observe que as propriedades de cada tipo de entidade que compõem sua chave de entidade são denotadas com chave (“”).</span><span class="sxs-lookup"><span data-stu-id="3fb4e-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="3fb4e-122">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3fb4e-123">CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:</span><span class="sxs-lookup"><span data-stu-id="3fb4e-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="3fb4e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fb4e-124">See Also</span></span>  
 [<span data-ttu-id="3fb4e-125">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3fb4e-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="3fb4e-126">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3fb4e-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="3fb4e-127">facet</span><span class="sxs-lookup"><span data-stu-id="3fb4e-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
