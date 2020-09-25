---
title: tipo complexo
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203781"
---
# <a name="complex-type"></a><span data-ttu-id="96fa7-102">tipo complexo</span><span class="sxs-lookup"><span data-stu-id="96fa7-102">complex type</span></span>

<span data-ttu-id="96fa7-103">Um *tipo complexo* é um modelo para definir propriedades ricas e estruturadas em [tipos de entidade](entity-type.md) ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="96fa7-103">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="96fa7-104">Cada modelo contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="96fa7-104">Each template contains the following:</span></span>  
  
- <span data-ttu-id="96fa7-105">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="96fa7-105">A unique name.</span></span> <span data-ttu-id="96fa7-106">(Obrigatória)</span><span class="sxs-lookup"><span data-stu-id="96fa7-106">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="96fa7-107">O nome de um tipo complexo não pode ser o mesmo que um nome de tipo de entidade dentro do mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="96fa7-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="96fa7-108">Dados na forma de uma ou mais [Propriedades](property.md).</span><span class="sxs-lookup"><span data-stu-id="96fa7-108">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="96fa7-109">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="96fa7-109">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="96fa7-110">Uma propriedade de um tipo complexo pode ser outro tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="96fa7-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="96fa7-111">Um tipo complexo é semelhante a um tipo de entidade que um tipo complexo pode levar uma carga útil de dados na forma das propriedades do tipo primitivo ou outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="96fa7-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="96fa7-112">No entanto, há algumas diferenças entre tipos complexos e tipos de entidade:</span><span class="sxs-lookup"><span data-stu-id="96fa7-112">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="96fa7-113">Os tipos complexos não têm identidades e portanto não podem existir independente.</span><span class="sxs-lookup"><span data-stu-id="96fa7-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="96fa7-114">Os tipos complexos podem existir somente como propriedades em tipos de entidade ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="96fa7-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="96fa7-115">Tipos complexos não podem participar de [associações](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="96fa7-115">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="96fa7-116">Nenhuma extremidade de uma associação pode ser um tipo complexo e, portanto, [as propriedades de navegação](navigation-property.md) não podem ser definidas em tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="96fa7-116">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96fa7-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96fa7-117">Example</span></span>  

 <span data-ttu-id="96fa7-118">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="96fa7-118">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="96fa7-119">CSDL seguir define um tipo complexo, endereço, com as propriedades `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`de tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="96fa7-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="96fa7-120">Para definir o tipo complexo `Address` (acima) como uma propriedade em um tipo de entidade, você deve declarar a propriedade na definição de tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="96fa7-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="96fa7-121">CSDL seguir declara a propriedade de `Address` como um tipo complexo em um tipo de entidade (Publisher):</span><span class="sxs-lookup"><span data-stu-id="96fa7-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="96fa7-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="96fa7-122">See also</span></span>

- [<span data-ttu-id="96fa7-123">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="96fa7-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="96fa7-124">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="96fa7-124">Entity Data Model</span></span>](entity-data-model.md)
