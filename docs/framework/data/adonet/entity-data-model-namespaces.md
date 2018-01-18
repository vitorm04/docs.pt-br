---
title: 'Modelo de Dados de Entidade: Namespaces'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b3e69017b5f617cff9bf2c159d5538a8c41e4cc0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="8127c-102">Modelo de Dados de Entidade: Namespaces</span><span class="sxs-lookup"><span data-stu-id="8127c-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="8127c-103">Um namespace de modelo de dados na entidade (EDM) é um contêiner abstrato de [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md), [tipos complexos](../../../../docs/framework/data/adonet/complex-type.md), e [associações](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="8127c-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="8127c-104">Namespaces em EDM são semelhantes aos espaços em uma linguagem de programação: fornecem o contexto para os objetos que contêm e fornecem uma maneira de torne os objetos que têm o mesmo nome (mas estão contidos em namespaces diferentes).</span><span class="sxs-lookup"><span data-stu-id="8127c-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8127c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8127c-105">Example</span></span>  
 <span data-ttu-id="8127c-106">O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="8127c-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="8127c-107">O seguinte código de CSDL usar um namespace para identificar um tipo que é definido em um modelo conceitual diferente.</span><span class="sxs-lookup"><span data-stu-id="8127c-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="8127c-108">O exemplo define um tipo de entidade (`Publisher`) que tenha uma propriedade do tipo complexo (`Address`) que é importado do espaço de `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="8127c-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="8127c-109">Observe que o elemento de `Using` indica que um namespace foi importado.</span><span class="sxs-lookup"><span data-stu-id="8127c-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="8127c-110">Observe também que o tipo da propriedade de `Address` é definido usando seu nome totalmente qualificado (`ExtendedBooksModel.Address`), indicando que esse tipo está definido no namespace de `ExtendedBooksModel` .</span><span class="sxs-lookup"><span data-stu-id="8127c-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="8127c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8127c-111">See Also</span></span>  
 [<span data-ttu-id="8127c-112">Principais conceitos do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="8127c-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="8127c-113">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="8127c-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
