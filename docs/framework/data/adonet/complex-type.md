---
title: tipo complexo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 389a3be7342005e424c89ff4e430b4a257f2da5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="complex-type"></a><span data-ttu-id="b2067-102">tipo complexo</span><span class="sxs-lookup"><span data-stu-id="b2067-102">complex type</span></span>
<span data-ttu-id="b2067-103">Um *tipo complexo* é um modelo para definir propriedades ricos, estruturadas em [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md) ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="b2067-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="b2067-104">Cada modelo contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b2067-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="b2067-105">Um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="b2067-105">A unique name.</span></span> <span data-ttu-id="b2067-106">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="b2067-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2067-107">O nome de um tipo complexo não pode ser o mesmo que um nome de tipo de entidade dentro do mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="b2067-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="b2067-108">Dados na forma de um ou mais [propriedades](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="b2067-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="b2067-109">(Opcional).</span><span class="sxs-lookup"><span data-stu-id="b2067-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2067-110">Uma propriedade de um tipo complexo pode ser outro tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="b2067-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="b2067-111">Um tipo complexo é semelhante a um tipo de entidade que um tipo complexo pode levar uma carga útil de dados na forma das propriedades do tipo primitivo ou outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="b2067-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="b2067-112">No entanto, há algumas diferenças entre tipos complexos e tipos de entidade:</span><span class="sxs-lookup"><span data-stu-id="b2067-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="b2067-113">Os tipos complexos não têm identidades e portanto não podem existir independente.</span><span class="sxs-lookup"><span data-stu-id="b2067-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="b2067-114">Os tipos complexos podem existir somente como propriedades em tipos de entidade ou em outros tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="b2067-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="b2067-115">Tipos complexos não podem participar [associações](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="b2067-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="b2067-116">Nenhuma extremidade de uma associação pode ser um tipo complexo e, portanto, [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) não podem ser definidos em tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="b2067-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2067-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2067-117">Example</span></span>  
 <span data-ttu-id="b2067-118">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="b2067-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b2067-119">CSDL seguir define um tipo complexo, endereço, com as propriedades `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`de tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="b2067-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="b2067-120">Para definir o tipo complexo `Address` (acima) como uma propriedade em um tipo de entidade, você deve declarar a propriedade na definição de tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="b2067-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="b2067-121">CSDL seguir declara a propriedade de `Address` como um tipo complexo em um tipo de entidade (Publisher):</span><span class="sxs-lookup"><span data-stu-id="b2067-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="b2067-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2067-122">See Also</span></span>  
 [<span data-ttu-id="b2067-123">Conceitos chave do modelo de dados de entidade</span><span class="sxs-lookup"><span data-stu-id="b2067-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b2067-124">Modelo de dados de entidade</span><span class="sxs-lookup"><span data-stu-id="b2067-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
