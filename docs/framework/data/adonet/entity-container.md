---
title: contêiner da entidade
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 4a629a800df63c67dc17d3fc1531a9862861e9c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144060"
---
# <a name="entity-container"></a><span data-ttu-id="ee4c0-102">contêiner da entidade</span><span class="sxs-lookup"><span data-stu-id="ee4c0-102">entity container</span></span>
<span data-ttu-id="ee4c0-103">Uma *contêiner de entidade* é um agrupamento lógico de [conjuntos de entidades](../../../../docs/framework/data/adonet/entity-set.md), [conjuntos de associações](../../../../docs/framework/data/adonet/association-set.md), e [importações de função](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="ee4c0-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="ee4c0-104">O seguinte deve ser verdadeiro de um contêiner de entidade definido em um modelo conceitual:</span><span class="sxs-lookup"><span data-stu-id="ee4c0-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="ee4c0-105">Pelo menos um contêiner de entidade deve ser definido em cada modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="ee4c0-106">O contêiner de entidade deve ter um nome exclusivo dentro de cada modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="ee4c0-107">Um contêiner de entidade pode definir os conjuntos de entidades ou conjuntos de associações que usam os tipos de entidade ou as associações definidos em um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="ee4c0-108">Para obter mais informações, consulte [modelo de dados de entidade: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="ee4c0-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee4c0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee4c0-109">Example</span></span>  
 <span data-ttu-id="ee4c0-110">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="ee4c0-111">Consulte o próximo exemplo para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-111">See the next example for more information.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ee4c0-113">Embora o diagrama não transmite informações do contêiner de entidade, o modelo conceitual deve definir um contêiner de entidade.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="ee4c0-114">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa DSL chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ee4c0-115">CSDL seguir define um contêiner de entidade para o modelo conceitual mostrado no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="ee4c0-116">Observe que o nome de contêiner de entidade é definido em um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="ee4c0-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ee4c0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee4c0-117">See also</span></span>

- [<span data-ttu-id="ee4c0-118">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="ee4c0-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="ee4c0-119">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="ee4c0-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
