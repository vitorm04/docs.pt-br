---
title: "restrição de integridade referencial"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c343a0eba2478e041186f7bef18a85400c54bb5c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="3736c-102">restrição de integridade referencial</span><span class="sxs-lookup"><span data-stu-id="3736c-102">referential integrity constraint</span></span>
<span data-ttu-id="3736c-103">Um *restrição de integridade referencial* modelo de dados na entidade (EDM) é semelhante a uma restrição de integridade referencial em um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="3736c-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="3736c-104">Da mesma forma que uma coluna (ou colunas) de uma tabela de banco de dados podem fazer referência a chave primária de outra tabela, uma [propriedade](../../../../docs/framework/data/adonet/property.md) (ou propriedades) de um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) podem fazer referência a [chave da entidade ](../../../../docs/framework/data/adonet/entity-key.md) de outro tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="3736c-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="3736c-105">O tipo de entidade referenciada é chamado de *extremidade principal* da restrição.</span><span class="sxs-lookup"><span data-stu-id="3736c-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="3736c-106">O tipo de entidade que faz referência a extremidade principal é chamado de *extremidade dependente* da restrição.</span><span class="sxs-lookup"><span data-stu-id="3736c-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="3736c-107">Uma restrição de integridade referencial é definida como parte de um [associação](../../../../docs/framework/data/adonet/association-type.md) entre dois tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="3736c-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="3736c-108">A definição de uma restrição de integridade referencial especifica as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="3736c-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="3736c-109">O final principal de restrição.</span><span class="sxs-lookup"><span data-stu-id="3736c-109">The principal end of the constraint.</span></span> <span data-ttu-id="3736c-110">(Um tipo de entidade cuja chave de entidade é referenciada pela o final dependente.)</span><span class="sxs-lookup"><span data-stu-id="3736c-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="3736c-111">A chave de entidade de extremidade principal.</span><span class="sxs-lookup"><span data-stu-id="3736c-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="3736c-112">O final dependente de restrição.</span><span class="sxs-lookup"><span data-stu-id="3736c-112">The dependent end of the constraint.</span></span> <span data-ttu-id="3736c-113">(Um tipo de entidade que tem uma propriedade ou um propriedades que referenciem a chave de entidade de extremidade principal.)</span><span class="sxs-lookup"><span data-stu-id="3736c-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="3736c-114">A propriedade ou propriedades referência de extremidade dependente.</span><span class="sxs-lookup"><span data-stu-id="3736c-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="3736c-115">O objetivo de restrições de integridade referencial em EDM é garantir que as associações válidos sempre existe.</span><span class="sxs-lookup"><span data-stu-id="3736c-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="3736c-116">Para obter mais informações, consulte [propriedade de chave estrangeira](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="3736c-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3736c-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3736c-117">Example</span></span>  
 <span data-ttu-id="3736c-118">O diagrama a seguir mostra um modelo conceitual com duas associações: `WrittenBy` e `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="3736c-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="3736c-119">O tipo de entidade de `Book` tem uma propriedade, `PublisherId`, que faz referência a chave de entidade do tipo de entidade de `Publisher` quando você define uma restrição de integridade referencial em associação de `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="3736c-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="3736c-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="3736c-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="3736c-121">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="3736c-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="3736c-122">CSDL seguir define uma restrição de integridade referencial em associação de `PublishedBy` mostrada no modelo conceitual anterior.</span><span class="sxs-lookup"><span data-stu-id="3736c-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="3736c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3736c-123">See Also</span></span>  
 [<span data-ttu-id="3736c-124">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3736c-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="3736c-125">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="3736c-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
