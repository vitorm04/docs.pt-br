---
title: propriedade de chave estrangeira
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 044be77cbbd8b5ad16cfbd5bbf1fdde984a060d5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="foreign-key-property"></a><span data-ttu-id="f6ff5-102">propriedade de chave estrangeira</span><span class="sxs-lookup"><span data-stu-id="f6ff5-102">foreign key property</span></span>
<span data-ttu-id="f6ff5-103">Um *propriedade de chave estrangeira* modelo de dados na entidade (EDM) é um tipo primitivo [propriedade](../../../../docs/framework/data/adonet/property.md) (ou um conjunto de propriedades de tipo primitivo) em um [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md) que contém o [chave da entidade](../../../../docs/framework/data/adonet/entity-key.md) de outro tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](../../../../docs/framework/data/adonet/property.md) (or a set of primitive type properties) on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that contains the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="f6ff5-104">Uma propriedade de chave externa é análogo a uma coluna de chave externa em uma base de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="f6ff5-105">Da mesma forma que colunas de chave estrangeira são usadas em um banco de dados relacional para criar relações entre linhas em tabelas, as propriedades de chave estrangeira em um modelo conceitual são usadas para estabelecer [associações](../../../../docs/framework/data/adonet/association-type.md) entre tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](../../../../docs/framework/data/adonet/association-type.md) between entity types.</span></span> <span data-ttu-id="f6ff5-106">Um [restrição de integridade referencial](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) é usado para definir uma associação entre dois tipos de entidade quando um dos tipos tem uma propriedade de chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-106">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ff5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6ff5-107">Example</span></span>  
 <span data-ttu-id="f6ff5-108">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="f6ff5-109">O tipo de entidade de `Book` tem uma propriedade, `PublisherId`, que faz referência a chave de entidade do tipo de entidade de `Publisher` quando você define uma restrição de integridade referencial em associação de `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="f6ff5-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="f6ff5-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="f6ff5-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="f6ff5-111">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-111">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="f6ff5-112">CSDL seguir usa a propriedade `PublisherId` de chave externa para definir uma restrição de integridade referencial em associação de `PublishedBy` mostrada no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="f6ff5-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="f6ff5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6ff5-113">See Also</span></span>  
 [<span data-ttu-id="f6ff5-114">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="f6ff5-114">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="f6ff5-115">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="f6ff5-115">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
