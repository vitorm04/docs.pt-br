---
title: facet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 23346fe2095cea2b3f0d705c7d6d8914c35c06f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="facet"></a><span data-ttu-id="b239d-102">facet</span><span class="sxs-lookup"><span data-stu-id="b239d-102">facet</span></span>
<span data-ttu-id="b239d-103">Um *faceta* é usado para adicionar detalhes a uma definição de propriedade do tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="b239d-103">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="b239d-104">Um [propriedade](../../../../docs/framework/data/adonet/property.md) definição contém informações sobre o tipo de propriedade, mas geralmente é necessário obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="b239d-104">A [property](../../../../docs/framework/data/adonet/property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="b239d-105">Por exemplo, um tipo de entidade em um modelo conceitual pode ter uma propriedade do tipo `String` cujo valor pode não ser definido como nulo.</span><span class="sxs-lookup"><span data-stu-id="b239d-105">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="b239d-106">As facetas permitem que você especifique esse nível de detalhe.</span><span class="sxs-lookup"><span data-stu-id="b239d-106">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="b239d-107">A tabela a seguir descreve as facetas que são suportadas em EDM.</span><span class="sxs-lookup"><span data-stu-id="b239d-107">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b239d-108">Os valores precisos e os comportamentos de facetas são determinados pelo ambiente de tempo de execução usando uma implementação de EDM.</span><span class="sxs-lookup"><span data-stu-id="b239d-108">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="b239d-109">Aspecto</span><span class="sxs-lookup"><span data-stu-id="b239d-109">Facet</span></span>|<span data-ttu-id="b239d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b239d-110">Description</span></span>|<span data-ttu-id="b239d-111">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="b239d-111">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="b239d-112">Especifica a sequência de agrupamento (ou sequência de classificação) a ser usadas para executar a comparação e em ordenação operações em valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b239d-112">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="b239d-113">Indica que o valor da propriedade deve ser usado para verificação de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="b239d-113">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="b239d-114">As propriedades do tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="b239d-114">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="b239d-115">Especifica o valor de propriedade padrão se nenhum valor é fornecido em cima de instanciação.</span><span class="sxs-lookup"><span data-stu-id="b239d-115">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="b239d-116">As propriedades do tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="b239d-116">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="b239d-117">Especifica se o comprimento do valor da propriedade pode variar.</span><span class="sxs-lookup"><span data-stu-id="b239d-117">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="b239d-118">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="b239d-118">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="b239d-119">Especifica o comprimento máximo de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b239d-119">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="b239d-120">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="b239d-120">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="b239d-121">Especifica se a propriedade pode ter um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="b239d-121">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="b239d-122">As propriedades do tipo primitivo</span><span class="sxs-lookup"><span data-stu-id="b239d-122">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="b239d-123">Para propriedades de tipo `Decimal`, especifica o número de dígitos que um valor de propriedade pode ter.</span><span class="sxs-lookup"><span data-stu-id="b239d-123">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="b239d-124">Para propriedades de tipo `Time`, `DateTime`, e `DateTimeOffset`, especifique o número de dígitos para a parte fracionária de segundos de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b239d-124">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="b239d-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span><span class="sxs-lookup"><span data-stu-id="b239d-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="b239d-126">Especifica o número de dígitos à direita do ponto decimal para o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="b239d-126">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="b239d-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="b239d-127">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="b239d-128">Indica se o valor da propriedade é armazenado como Unicode.</span><span class="sxs-lookup"><span data-stu-id="b239d-128">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="b239d-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b239d-129">Example</span></span>  
 <span data-ttu-id="b239d-130">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="b239d-130">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b239d-131">CSDL seguir define um tipo de entidade de `Book` .</span><span class="sxs-lookup"><span data-stu-id="b239d-131">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="b239d-132">Observe que as facetas são implementadas como atributos XML.</span><span class="sxs-lookup"><span data-stu-id="b239d-132">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="b239d-133">Os valores de aspecto indica que nenhuma propriedade pode ser definida para nulo, e que `Scale` e `Precision` de propriedade de cada `Revision` são definidas como 29.</span><span class="sxs-lookup"><span data-stu-id="b239d-133">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b239d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b239d-134">See Also</span></span>  
 [<span data-ttu-id="b239d-135">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="b239d-135">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b239d-136">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="b239d-136">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
