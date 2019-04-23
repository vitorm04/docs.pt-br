---
title: tipo complexo
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 9d63660c441192bbc9ecb48bb3a86030b46461cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160804"
---
# <a name="complex-type"></a><span data-ttu-id="3ef0c-102">tipo complexo</span><span class="sxs-lookup"><span data-stu-id="3ef0c-102">complex type</span></span>
<span data-ttu-id="3ef0c-103">Um *tipo complexo* é um modelo para definir propriedades ricas, estruturados nos [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md) ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="3ef0c-104">Cada modelo contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3ef0c-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="3ef0c-105">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-105">A unique name.</span></span> <span data-ttu-id="3ef0c-106">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="3ef0c-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ef0c-107">O nome de um tipo complexo não pode ser o mesmo que um nome de tipo de entidade dentro do mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="3ef0c-108">Dados na forma de um ou mais [propriedades](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="3ef0c-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="3ef0c-109">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="3ef0c-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ef0c-110">Uma propriedade de um tipo complexo pode ser outro tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="3ef0c-111">Um tipo complexo é semelhante a um tipo de entidade que um tipo complexo pode levar uma carga útil de dados na forma das propriedades do tipo primitivo ou outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="3ef0c-112">No entanto, há algumas diferenças entre tipos complexos e tipos de entidade:</span><span class="sxs-lookup"><span data-stu-id="3ef0c-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="3ef0c-113">Os tipos complexos não têm identidades e portanto não podem existir independente.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="3ef0c-114">Os tipos complexos podem existir somente como propriedades em tipos de entidade ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="3ef0c-115">Tipos complexos não podem participar [associações](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="3ef0c-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="3ef0c-116">Nenhum o final de uma associação pode ser um tipo complexo e portanto [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) não podem ser definidos em tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ef0c-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ef0c-117">Example</span></span>  
 <span data-ttu-id="3ef0c-118">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3ef0c-119">CSDL seguir define um tipo complexo, endereço, com as propriedades `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`de tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="3ef0c-120">Para definir o tipo complexo `Address` (acima) como uma propriedade em um tipo de entidade, você deve declarar a propriedade na definição de tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="3ef0c-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="3ef0c-121">CSDL seguir declara a propriedade de `Address` como um tipo complexo em um tipo de entidade (Publisher):</span><span class="sxs-lookup"><span data-stu-id="3ef0c-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="3ef0c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ef0c-122">See also</span></span>

- [<span data-ttu-id="3ef0c-123">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3ef0c-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="3ef0c-124">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3ef0c-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
