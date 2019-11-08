---
title: 'Modelo de Dados de Entidade: Namespaces'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a403bcd459005ed9cea4a455fcde40c31c8caac9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738433"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="1db6e-102">Modelo de Dados de Entidade: Namespaces</span><span class="sxs-lookup"><span data-stu-id="1db6e-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="1db6e-103">Um namespace no Modelo de Dados de Entidade (EDM) é um contêiner abstrato para [tipos de entidade](entity-type.md), [tipos complexos](complex-type.md)e [associações](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="1db6e-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="1db6e-104">Namespaces em EDM são semelhantes aos espaços em uma linguagem de programação: fornecem o contexto para os objetos que contêm e fornecem uma maneira de torne os objetos que têm o mesmo nome (mas estão contidos em namespaces diferentes).</span><span class="sxs-lookup"><span data-stu-id="1db6e-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db6e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1db6e-105">Example</span></span>  
 <span data-ttu-id="1db6e-106">O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(linguagem de definição de esquema conceitual) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="1db6e-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="1db6e-107">O seguinte código de CSDL usar um namespace para identificar um tipo que é definido em um modelo conceitual diferente.</span><span class="sxs-lookup"><span data-stu-id="1db6e-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="1db6e-108">O exemplo define um tipo de entidade (`Publisher`) que tenha uma propriedade do tipo complexo (`Address`) que é importado do espaço de `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="1db6e-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="1db6e-109">Observe que o elemento de `Using` indica que um namespace foi importado.</span><span class="sxs-lookup"><span data-stu-id="1db6e-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="1db6e-110">Observe também que o tipo da propriedade de `Address` é definido usando seu nome totalmente qualificado (`ExtendedBooksModel.Address`), indicando que esse tipo está definido no namespace de `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="1db6e-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="1db6e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1db6e-111">See also</span></span>

- [<span data-ttu-id="1db6e-112">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="1db6e-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="1db6e-113">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="1db6e-113">Entity Data Model</span></span>](entity-data-model.md)
