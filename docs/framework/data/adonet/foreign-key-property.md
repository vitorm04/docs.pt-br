---
title: propriedade de chave estrangeira
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: a77f7479ce38cb34830377021157f312916baca4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738400"
---
# <a name="foreign-key-property"></a><span data-ttu-id="90d66-102">propriedade de chave estrangeira</span><span class="sxs-lookup"><span data-stu-id="90d66-102">foreign key property</span></span>
<span data-ttu-id="90d66-103">Uma *propriedade de chave estrangeira* no modelo de dados de entidade (EDM) é uma [Propriedade](property.md) de tipo primitivo (ou um conjunto de propriedades de tipo primitivo) em um [tipo de entidade](entity-type.md) que contém a chave de [entidade](entity-key.md) de outro tipo de entidade.</span><span class="sxs-lookup"><span data-stu-id="90d66-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="90d66-104">Uma propriedade de chave externa é análogo a uma coluna de chave externa em uma base de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="90d66-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="90d66-105">Da mesma forma que as colunas de chave estrangeira são usadas em um banco de dados relacional para criar relações entre linhas em tabelas, as propriedades de chave estrangeira em um modelo conceitual são usadas para estabelecer [associações](association-type.md) entre tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="90d66-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="90d66-106">Uma [restrição de integridade referencial](referential-integrity-constraint.md) é usada para definir uma associação entre dois tipos de entidade quando um dos tipos tem uma propriedade de chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="90d66-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90d66-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90d66-107">Example</span></span>  
 <span data-ttu-id="90d66-108">O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.</span><span class="sxs-lookup"><span data-stu-id="90d66-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="90d66-109">O tipo de entidade de `Book` tem uma propriedade, `PublisherId`, que faz referência a chave de entidade do tipo de entidade de `Publisher` quando você define uma restrição de integridade referencial em associação de `PublishedBy` .</span><span class="sxs-lookup"><span data-stu-id="90d66-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="90d66-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Exemplo de um modelo de restrição referencial")</span><span class="sxs-lookup"><span data-stu-id="90d66-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="90d66-111">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="90d66-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="90d66-112">CSDL seguir usa a propriedade `PublisherId` de chave externa para definir uma restrição de integridade referencial em associação de `PublishedBy` mostrada no modelo conceitual mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="90d66-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="90d66-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90d66-113">See also</span></span>

- [<span data-ttu-id="90d66-114">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="90d66-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="90d66-115">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="90d66-115">Entity Data Model</span></span>](entity-data-model.md)
