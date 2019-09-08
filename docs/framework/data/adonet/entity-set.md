---
title: conjunto de entidades
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: b74d6bf373925ac90a998e2c4425c053e533f82a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783995"
---
# <a name="entity-set"></a><span data-ttu-id="0e827-102">conjunto de entidades</span><span class="sxs-lookup"><span data-stu-id="0e827-102">entity set</span></span>
<span data-ttu-id="0e827-103">Um *conjunto de entidades* é um contêiner lógico para instâncias de um [tipo de entidade](entity-type.md) e instâncias de qualquer tipo derivado desse tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="0e827-103">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="0e827-104">(Para obter informações sobre tipos derivados, [consulte modelo de dados de entidade: Herança](entity-data-model-inheritance.md).) A relação entre um tipo de entidade e um conjunto de entidades é análoga à relação entre uma linha e uma tabela em um banco de dados relacional: Como uma linha, um tipo de entidade descreve a estrutura de dados e, como uma tabela, um conjunto de entidades contém instâncias de uma determinada estrutura.</span><span class="sxs-lookup"><span data-stu-id="0e827-104">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="0e827-105">Um conjunto de entidades não é um dados que modelam a compilação; não descreve a estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="0e827-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="0e827-106">Em vez disso, um conjunto de entidades fornece uma compilação para um ambiente de hospedagem ou de armazenamento (como Common Language Runtime ou um base de dados do SQL Server) instâncias de tipo de entidade do grupo de modo que eles possam ser mapeadas em um armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="0e827-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="0e827-107">Um conjunto de entidades é definido em um [contêiner de entidade](entity-container.md), que é um agrupamento lógico de conjuntos de entidades e conjuntos de [Associação](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="0e827-107">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="0e827-108">Para uma instância do tipo de entidade existe em um conjunto de entidades, o seguinte deve ser verdadeira:</span><span class="sxs-lookup"><span data-stu-id="0e827-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="0e827-109">O tipo de qualquer instância é o mesmo como o tipo de objeto no qual o conjunto de entidades é baseado, ou o tipo de instância é um subtipo do tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="0e827-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="0e827-110">A [chave de entidade](entity-key.md) para a instância é exclusiva dentro do conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="0e827-110">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="0e827-111">A instância não existir em qualquer outro conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="0e827-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e827-112">Os vários conjuntos de entidades podem ser definidos usando o mesmo tipo de entidade, mas uma instância de um tipo de dado entidade só pode existir em um conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="0e827-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="0e827-113">Você não precisa definir um conjunto de entidades para cada tipo de entidade em um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="0e827-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e827-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e827-114">Example</span></span>  
 <span data-ttu-id="0e827-115">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="0e827-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="0e827-117">A seguir temos de diagrama dois conjuntos de entidades (`Books` e `Publishers`) e um conjunto de associações (`PublishedBy`) com base no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="0e827-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="0e827-118">Bi no conjunto `Books` de entidades representa uma instância `Book` do tipo de entidade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0e827-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="0e827-119">Da mesma forma, PJ `Publisher` representa uma instância `Publishers` no conjunto de entidades.</span><span class="sxs-lookup"><span data-stu-id="0e827-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="0e827-120">BiPj representa uma instância da `PublishedBy` Associação `PublishedBy` no conjunto de associação.</span><span class="sxs-lookup"><span data-stu-id="0e827-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Captura de tela que mostra um exemplo de conjuntos.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="0e827-122">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](./ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="0e827-122">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="0e827-123">CSDL seguir define um contêiner de entidade com um conjunto de entidades para cada tipo de entidade no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="0e827-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="0e827-124">Observe que o nome e o tipo de entidade para cada conjunto de entidades são definidos usando atributos XML.</span><span class="sxs-lookup"><span data-stu-id="0e827-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="0e827-125">É possível definir vários conjuntos de entidades por tipo (MEST).</span><span class="sxs-lookup"><span data-stu-id="0e827-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="0e827-126">CSDL seguir define um contêiner de entidade com dois conjuntos de entidades para o tipo de entidade de `Book` :</span><span class="sxs-lookup"><span data-stu-id="0e827-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="0e827-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e827-127">See also</span></span>

- [<span data-ttu-id="0e827-128">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="0e827-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="0e827-129">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="0e827-129">Entity Data Model</span></span>](entity-data-model.md)
