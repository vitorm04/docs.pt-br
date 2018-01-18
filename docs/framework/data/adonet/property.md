---
title: propriedade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 50cd2f2678d304af8b898380645424e0635891d2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="property"></a><span data-ttu-id="dc5b8-102">propriedade</span><span class="sxs-lookup"><span data-stu-id="dc5b8-102">property</span></span>
<span data-ttu-id="dc5b8-103">*Propriedades* são os blocos de construção fundamentais de [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md) e [tipos complexos](../../../../docs/framework/data/adonet/complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-103">*Properties* are the fundamental building blocks of [entity types](../../../../docs/framework/data/adonet/entity-type.md) and [complex types](../../../../docs/framework/data/adonet/complex-type.md).</span></span> <span data-ttu-id="dc5b8-104">As propriedades definem a forma e as características de dados que uma instância do tipo de entidade ou a instância do tipo complexo conterão.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="dc5b8-105">As propriedades em um modelo conceitual são análogas as propriedades definidas em uma classe.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="dc5b8-106">Da mesma forma que as propriedades em uma classe definem a forma da classe e transportam informações sobre objetos, as propriedades em um modelo conceitual definem a forma de um tipo de entidade e transportam informações sobre as instâncias dos tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5b8-107">As propriedades, como descrito neste tópico, são diferentes de propriedades de navegação.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="dc5b8-108">Para obter mais informações, consulte [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-108">For more information, see [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md).</span></span>  
  
 <span data-ttu-id="dc5b8-109">Uma definição de propriedade contém as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="dc5b8-109">A property definition contains the following information:</span></span>  
  
-   <span data-ttu-id="dc5b8-110">Um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-110">A property name.</span></span> <span data-ttu-id="dc5b8-111">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="dc5b8-111">(Required)</span></span>  
  
-   <span data-ttu-id="dc5b8-112">Um tipo de propriedade.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-112">A property type.</span></span> <span data-ttu-id="dc5b8-113">(Necessário)</span><span class="sxs-lookup"><span data-stu-id="dc5b8-113">(Required)</span></span>  
  
-   <span data-ttu-id="dc5b8-114">Um conjunto de [facetas](../../../../docs/framework/data/adonet/facet.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-114">A set of [facets](../../../../docs/framework/data/adonet/facet.md).</span></span> <span data-ttu-id="dc5b8-115">(Opcional)</span><span class="sxs-lookup"><span data-stu-id="dc5b8-115">(Optional)</span></span>  
  
 <span data-ttu-id="dc5b8-116">Uma propriedade pode conter dados primitivos (como uma cadeia de caracteres, um número inteiro ou um valor booliano) ou dados estruturados (como um tipo complexo).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="dc5b8-117">As propriedades que são do tipo primitivo também são chamadas propriedades escalares.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="dc5b8-118">Para obter mais informações, consulte [modelo de dados de entidade: tipos de dados primitivos](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-118">For more information, see [Entity Data Model: Primitive Data Types](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5b8-119">Um tipo complexo pode, em si, para ter as propriedades que são tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc5b8-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc5b8-120">Example</span></span>  
 <span data-ttu-id="dc5b8-121">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="dc5b8-122">Cada tipo de entidade tem várias propriedades, embora as informações de tipo para cada propriedade não é transmitida no diagrama.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="dc5b8-123">Propriedades que são [chaves de entidade](../../../../docs/framework/data/adonet/entity-key.md) são indicados com (chave).</span><span class="sxs-lookup"><span data-stu-id="dc5b8-123">Properties that are [entity keys](../../../../docs/framework/data/adonet/entity-key.md) are denoted with (Key).</span></span>  
  
 <span data-ttu-id="dc5b8-124">![Modelo de exemplo](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="dc5b8-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="dc5b8-125">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="dc5b8-126">CSDL seguir define o tipo de entidade de `Book` (conforme mostrado no diagrama anterior) e indica o tipo e o nome de cada propriedade usando atributos XML.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="dc5b8-127">Um aspecto opcional, `Nullable`, também é definida usando um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="dc5b8-128">É possível que uma das propriedades mostradas no diagrama é uma propriedade do tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="dc5b8-129">Por exemplo, a propriedade de `Address` no tipo de entidade de `Publisher` pode ser uma propriedade do tipo complexo composto de várias propriedades escalares, como `StreetAddress`, `City`, `StateOrProvince`, `Country`, e `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="dc5b8-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="dc5b8-130">A representação de CSDL de um tipo complexo seria como segue:</span><span class="sxs-lookup"><span data-stu-id="dc5b8-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="dc5b8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc5b8-131">See Also</span></span>  
 [<span data-ttu-id="dc5b8-132">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="dc5b8-132">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="dc5b8-133">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="dc5b8-133">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
