---
title: multiplicidade da extremidade da associação
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 183bbafaf1de3adf8719c7ee562be3513832ef10
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412091"
---
# <a name="association-end-multiplicity"></a><span data-ttu-id="531cc-102">multiplicidade da extremidade da associação</span><span class="sxs-lookup"><span data-stu-id="531cc-102">association end multiplicity</span></span>
<span data-ttu-id="531cc-103">*Multiplicidade de extremidades de associação* define o número de [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) instâncias que podem estar em uma extremidade de uma [associação](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="531cc-103">*Association end multiplicity* defines the number of [entity type](../../../../docs/framework/data/adonet/entity-type.md) instances that can be at one end of an [association](../../../../docs/framework/data/adonet/association-type.md).</span></span>  
  
 <span data-ttu-id="531cc-104">Uma multiplicidade do final da associação pode ter um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="531cc-104">An association end multiplicity can have one of the following values:</span></span>  
  
-   <span data-ttu-id="531cc-105">um (1): Indica se que essa instância de tipo exatamente uma entidade existe no final da associação.</span><span class="sxs-lookup"><span data-stu-id="531cc-105">one (1): Indicates that exactly one entity type instance exists at the association end.</span></span>  
  
-   <span data-ttu-id="531cc-106">zero ou um (entre 0 e 1): Indica que zero ou uma instância de tipo de entidade existe no final da associação.</span><span class="sxs-lookup"><span data-stu-id="531cc-106">zero or one (0..1): Indicates that zero or one entity type instances exist at the association end.</span></span>  
  
-   <span data-ttu-id="531cc-107">muitos (\*): indica que zero, um ou mais instâncias de tipo de entidade existem no final da associação.</span><span class="sxs-lookup"><span data-stu-id="531cc-107">many (\*): Indicates that zero, one, or more entity type instances exist at the association end.</span></span>  
  
 <span data-ttu-id="531cc-108">Uma associação é caracterizada frequentemente pelos multiplicities final da associação.</span><span class="sxs-lookup"><span data-stu-id="531cc-108">An association is often characterized by its association end multiplicities.</span></span> <span data-ttu-id="531cc-109">Por exemplo, se as extremidades de uma associação tem multiplicidades um (1) e muitos (\*), a associação é chamada de uma associação um-para-muitos.</span><span class="sxs-lookup"><span data-stu-id="531cc-109">For example, if the ends of an association have multiplicities one (1) and many (\*), the association is called a one-to-many association.</span></span> <span data-ttu-id="531cc-110">No exemplo abaixo, a associação de `PublishedBy` é um para muitos associação (um editor publica muitos livros e um livro é publicado por um editor).</span><span class="sxs-lookup"><span data-stu-id="531cc-110">In the example below, the `PublishedBy` association is a one-to-many association (a publisher publishes many books and a book is published by one publisher).</span></span> <span data-ttu-id="531cc-111">A associação de `WrittenBy` é um muitos para muitos associação (um livro pode ter vários autores e um autor pode escrever diversos livros).</span><span class="sxs-lookup"><span data-stu-id="531cc-111">The `WrittenBy` association is a many-to-many association (a book can have multiple authors and an author can write multiple books).</span></span>  
  
## <a name="example"></a><span data-ttu-id="531cc-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="531cc-112">Example</span></span>  
 <span data-ttu-id="531cc-113">O diagrama a seguir mostra um modelo conceitual com duas associações: `PublishedBy` e `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="531cc-113">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="531cc-114">Terminar a associação para associação de `PublishedBy` são os tipos de entidade de `Book` e de `Publisher` .</span><span class="sxs-lookup"><span data-stu-id="531cc-114">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="531cc-115">A multiplicidade do `Publisher` final é um (1) e a multiplicidade do `Book` end é muitas (\*).</span><span class="sxs-lookup"><span data-stu-id="531cc-115">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*).</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="531cc-117">O ADO.NET Entity Framework usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="531cc-117">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="531cc-118">CSDL seguir define a associação de `PublishedBy` mostrada no diagrama anterior:</span><span class="sxs-lookup"><span data-stu-id="531cc-118">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="531cc-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="531cc-119">See also</span></span>
- [<span data-ttu-id="531cc-120">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="531cc-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="531cc-121">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="531cc-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
