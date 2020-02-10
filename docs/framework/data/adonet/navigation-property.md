---
title: Propriedade de navegação
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094378"
---
# <a name="navigation-property"></a><span data-ttu-id="6066d-102">Propriedade de navegação</span><span class="sxs-lookup"><span data-stu-id="6066d-102">Navigation property</span></span>

<span data-ttu-id="6066d-103">Uma *propriedade de navegação* é uma propriedade opcional em [um tipo de entidade](entity-type.md) que permite a navegação de uma [extremidade](association-end.md) de uma [Associação](association-type.md) para a outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="6066d-103">A *navigation property* is an optional property on an [entity type](entity-type.md) that allows for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="6066d-104">Ao contrário de outras [Propriedades](property.md), as propriedades de navegação não contêm dados.</span><span class="sxs-lookup"><span data-stu-id="6066d-104">Unlike other [properties](property.md), navigation properties do not carry data.</span></span>

<span data-ttu-id="6066d-105">Uma definição de propriedade de navegação inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6066d-105">A navigation property definition includes the following:</span></span>

- <span data-ttu-id="6066d-106">Um nome.</span><span class="sxs-lookup"><span data-stu-id="6066d-106">A name.</span></span> <span data-ttu-id="6066d-107">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="6066d-107">(Required)</span></span>

- <span data-ttu-id="6066d-108">A associação que navega.</span><span class="sxs-lookup"><span data-stu-id="6066d-108">The association that it navigates.</span></span> <span data-ttu-id="6066d-109">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="6066d-109">(Required)</span></span>

- <span data-ttu-id="6066d-110">Termina de associação que navega.</span><span class="sxs-lookup"><span data-stu-id="6066d-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="6066d-111">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="6066d-111">(Required)</span></span>

<span data-ttu-id="6066d-112">As propriedades de navegação são opcionais em ambos os tipos de entidade nas extremidades de uma associação.</span><span class="sxs-lookup"><span data-stu-id="6066d-112">Navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="6066d-113">Se você definir uma propriedade de navegação em um tipo de entidade no final de uma associação, você não precisa definir uma propriedade de navegação no tipo de entidade no outro extremo de associação.</span><span class="sxs-lookup"><span data-stu-id="6066d-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>

<span data-ttu-id="6066d-114">O tipo de dados de uma propriedade de navegação é determinado pela [multiplicidade](association-end-multiplicity.md) de sua [extremidade de associação](association-end.md)remota.</span><span class="sxs-lookup"><span data-stu-id="6066d-114">The data type of a navigation property is determined by the [multiplicity](association-end-multiplicity.md) of its remote [association end](association-end.md).</span></span> <span data-ttu-id="6066d-115">Por exemplo, suponha uma propriedade de navegação, `OrdersNavProp`, existe em um tipo de entidade de `Customer` e navegar em um para muitos associação entre `Customer` e `Order`.</span><span class="sxs-lookup"><span data-stu-id="6066d-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="6066d-116">Como a extremidade de associação remota para a propriedade de navegação tem multiplicidade de muitos (\*), seu tipo de dados é uma coleção (de `Order`).</span><span class="sxs-lookup"><span data-stu-id="6066d-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="6066d-117">Da mesma forma, se uma propriedade de navegação, `CustomerNavProp`, existe no tipo de entidade de `Order` , seu tipo de dados deve ser `Customer`, porque a multiplicidade de extremidade remoto é um (1).</span><span class="sxs-lookup"><span data-stu-id="6066d-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>

## <a name="example"></a><span data-ttu-id="6066d-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6066d-118">Example</span></span>

<span data-ttu-id="6066d-119">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="6066d-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="6066d-120">As propriedades de navegação `Publisher` e `Authors` são definidas no tipo de entidade de livro.</span><span class="sxs-lookup"><span data-stu-id="6066d-120">The navigation properties `Publisher` and `Authors` are defined on the Book entity type.</span></span> <span data-ttu-id="6066d-121">A propriedade `Books` de navegação é definida no tipo de entidade do Publisher e tipo de entidade de `Author` .</span><span class="sxs-lookup"><span data-stu-id="6066d-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>

![Diagrama mostrando um modelo conceitual com três tipos de entidade.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

<span data-ttu-id="6066d-123">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="6066d-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="6066d-124">CSDL seguir define o tipo de entidade de `Book` mostrado no diagrama anterior:</span><span class="sxs-lookup"><span data-stu-id="6066d-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

<span data-ttu-id="6066d-125">Os atributos XML são usados para comunicar as informações necessárias para definir uma propriedade de navegação: o atributo `Name` contém o nome da propriedade, `Relationship` contém o nome da associação que navega e `FromRole` e `ToRole` contêm as extremidades da associação.</span><span class="sxs-lookup"><span data-stu-id="6066d-125">XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>

## <a name="see-also"></a><span data-ttu-id="6066d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6066d-126">See also</span></span>

- [<span data-ttu-id="6066d-127">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="6066d-127">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="6066d-128">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="6066d-128">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="6066d-129">Relações, propriedades de navegação e chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="6066d-129">Relationships, navigation properties, and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
