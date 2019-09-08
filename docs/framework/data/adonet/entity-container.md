---
title: contêiner da entidade
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795247"
---
# <a name="entity-container"></a><span data-ttu-id="0bf1a-102">contêiner da entidade</span><span class="sxs-lookup"><span data-stu-id="0bf1a-102">entity container</span></span>
<span data-ttu-id="0bf1a-103">Um *contêiner de entidade* é um agrupamento lógico [de conjuntos de entidades](entity-set.md), conjuntos de [Associação](association-set.md)e importações de [função](model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="0bf1a-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="0bf1a-104">O seguinte deve ser verdadeiro de um contêiner de entidade definido em um modelo conceitual:</span><span class="sxs-lookup"><span data-stu-id="0bf1a-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="0bf1a-105">Pelo menos um contêiner de entidade deve ser definido em cada modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="0bf1a-106">O contêiner de entidade deve ter um nome exclusivo dentro de cada modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="0bf1a-107">Um contêiner de entidade pode definir os conjuntos de entidades ou conjuntos de associações que usam os tipos de entidade ou as associações definidos em um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="0bf1a-108">Para obter mais informações, [consulte modelo de dados de entidade: Namespaces](entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="0bf1a-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf1a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bf1a-109">Example</span></span>  
 <span data-ttu-id="0bf1a-110">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="0bf1a-111">Consulte o próximo exemplo para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-111">See the next example for more information.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="0bf1a-113">Embora o diagrama não transmite informações do contêiner de entidade, o modelo conceitual deve definir um contêiner de entidade.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="0bf1a-114">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL chamada linguagem de definição de esquema conceitual ([CSDL](./ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="0bf1a-115">CSDL seguir define um contêiner de entidade para o modelo conceitual mostrado no diagrama anterior.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="0bf1a-116">Observe que o nome de contêiner de entidade é definido em um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="0bf1a-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="0bf1a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bf1a-117">See also</span></span>

- [<span data-ttu-id="0bf1a-118">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="0bf1a-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="0bf1a-119">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="0bf1a-119">Entity Data Model</span></span>](entity-data-model.md)
