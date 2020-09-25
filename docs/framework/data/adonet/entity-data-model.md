---
title: Modelo de Dados de Entidade
description: O Modelo de Dados de Entidade descreve a estrutura de dados, independentemente de sua forma armazenada, que aborda os desafios resultantes do armazenamento de dados em muitas formas.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 9323f652d1cfa27d442d45bd01e546f3b81d7e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200765"
---
# <a name="entity-data-model"></a><span data-ttu-id="c0b4e-103">Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="c0b4e-103">Entity Data Model</span></span>

<span data-ttu-id="c0b4e-104">O EDM (Modelo de Dados de Entidade) é um conjunto de conceitos que descrevem a estrutura de dados, independentemente do formato armazenado.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-104">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="c0b4e-105">O EDM pede emprestado o modelo de relacionamento entre entidades descrito por Peter Chen em 1976, mas também cria a partir desse modelo e estende seus usos tradicionais.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-105">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="c0b4e-106">O EDM resolve os desafios que ocorrem de ter dados armazenados em vários formatos.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-106">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="c0b4e-107">Por exemplo, considere um negócio que armazena dados em bancos de dados relacionais, arquivos de texto, arquivos XML, planilhas e relatórios.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-107">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="c0b4e-108">Isso representa desafios significativos na modelagem, na criação de aplicativos e no acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-108">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="c0b4e-109">Ao criar um aplicativo orientado a dados, o desafio é escrever código eficiente e sustentável sem sacrificar o acesso eficiente a dados, o armazenamento e a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-109">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="c0b4e-110">Quando os dados têm uma estrutura relacional, o acesso a dados, o armazenamento e a escalabilidade são muito eficientes, mas a escrita de código eficiente e sustentável torna-se mais difícil.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-110">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="c0b4e-111">Quando os dados têm uma estrutura de objeto, os conflitos são inversos: escrever código eficiente e sustentável sacrifica o acesso a dados eficiente, o armazenamento e a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-111">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="c0b4e-112">Mesmo que o equilíbrio correto entre esses conflitos seja encontrado, novos desafios surgem quando os dados são movidos de um formato para outro.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-112">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="c0b4e-113">O Modelo de Dados de Entidade resolve esses desafios descrevendo a estrutura dos dados em termos de entidades e relacionamentos que são independentes de qualquer esquema de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-113">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="c0b4e-114">Isso torna o formato de dados armazenado de dados irrelevante para a criação e o desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-114">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="c0b4e-115">E, como as entidades e os relacionamentos descrevem a estrutura de dados como é usada em um aplicativo (não o formato armazenado), eles podem evoluir junto com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-115">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="c0b4e-116">Um `conceptual model` é uma representação específica da estrutura de dados como entidades e relações, e é definido geralmente em um DSL (linguagem específica do domínio) que implementa os conceitos do EDM.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-116">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="c0b4e-117">O [CSDL (linguagem de definição de esquema conceitual)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) é um exemplo de tal linguagem específica de domínio.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-117">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="c0b4e-118">Entidades e relacionamentos descritos em um modelo conceitual podem ser consideradas abstrações de objetos e associações em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-118">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="c0b4e-119">Isso permite que os desenvolvedores concentrem-se no modelo conceitual sem se preocuparem com o esquema de armazenamento, e permite que eles escrevam o código pensando em eficiência e facilidade de manutenção.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-119">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="c0b4e-120">Enquanto isso, os designers de esquema de armazenamento podem se concentrar na eficiência de acesso a dados, armazenamento e escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-120">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0b4e-121">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c0b4e-121">In This Section</span></span>  

 <span data-ttu-id="c0b4e-122">Os tópicos nesta seção descrevem os conceitos do Modelo de Dados de Entidade.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-122">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="c0b4e-123">Qualquer DSL que implemente o EDM deve incluir os conceitos descritos aqui.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-123">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="c0b4e-124">Observe que o [Entity Framework ADO.net](./ef/index.md) usa CSDL para definir modelos conceituais.</span><span class="sxs-lookup"><span data-stu-id="c0b4e-124">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="c0b4e-125">Para obter mais informações, consulte [especificação CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="c0b4e-125">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="c0b4e-126">Conceitos chave do Modelo de Dados de Entidade</span><span class="sxs-lookup"><span data-stu-id="c0b4e-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="c0b4e-127">Modelo de Dados de Entidade: Namespaces</span><span class="sxs-lookup"><span data-stu-id="c0b4e-127">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="c0b4e-128">Modelo de Dados de Entidade: Tipos de dados primitivos</span><span class="sxs-lookup"><span data-stu-id="c0b4e-128">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="c0b4e-129">Modelo de Dados de Entidade: Herança</span><span class="sxs-lookup"><span data-stu-id="c0b4e-129">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="c0b4e-130">extremidade de associação</span><span class="sxs-lookup"><span data-stu-id="c0b4e-130">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="c0b4e-131">multiplicidade da extremidade da associação</span><span class="sxs-lookup"><span data-stu-id="c0b4e-131">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="c0b4e-132">conjunto de associações</span><span class="sxs-lookup"><span data-stu-id="c0b4e-132">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="c0b4e-133">extremidade do conjunto de associação</span><span class="sxs-lookup"><span data-stu-id="c0b4e-133">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="c0b4e-134">tipo de associação</span><span class="sxs-lookup"><span data-stu-id="c0b4e-134">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="c0b4e-135">tipo complexo</span><span class="sxs-lookup"><span data-stu-id="c0b4e-135">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="c0b4e-136">contêiner da entidade</span><span class="sxs-lookup"><span data-stu-id="c0b4e-136">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="c0b4e-137">chave de entidade</span><span class="sxs-lookup"><span data-stu-id="c0b4e-137">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="c0b4e-138">conjunto de entidades</span><span class="sxs-lookup"><span data-stu-id="c0b4e-138">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="c0b4e-139">tipo de entidade</span><span class="sxs-lookup"><span data-stu-id="c0b4e-139">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="c0b4e-140">particular</span><span class="sxs-lookup"><span data-stu-id="c0b4e-140">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="c0b4e-141">propriedade de chave estrangeira</span><span class="sxs-lookup"><span data-stu-id="c0b4e-141">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="c0b4e-142">função declarada por modelo</span><span class="sxs-lookup"><span data-stu-id="c0b4e-142">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="c0b4e-143">função definida por modelo</span><span class="sxs-lookup"><span data-stu-id="c0b4e-143">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="c0b4e-144">propriedade de navegação</span><span class="sxs-lookup"><span data-stu-id="c0b4e-144">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="c0b4e-145">property</span><span class="sxs-lookup"><span data-stu-id="c0b4e-145">property</span></span>](property.md)  
  
 [<span data-ttu-id="c0b4e-146">restrição de integridade referencial</span><span class="sxs-lookup"><span data-stu-id="c0b4e-146">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0b4e-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="c0b4e-147">See also</span></span>

- <span data-ttu-id="c0b4e-148">[Ferramentas de Modelo de Dados de Entidade de ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0b4e-148">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="c0b4e-149">[Visão geral do arquivo. edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0b4e-149">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="c0b4e-150">Especificação de CSDL</span><span class="sxs-lookup"><span data-stu-id="c0b4e-150">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
