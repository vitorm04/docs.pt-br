---
title: "Declarações de entidade de leitura e referências a entidades em DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="1916b-102">Declarações de entidade de leitura e referências a entidades em DOM</span><span class="sxs-lookup"><span data-stu-id="1916b-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="1916b-103">Uma entidade é uma declaração que indica um nome ser usado em XML no lugar do conteúdo ou marcação.</span><span class="sxs-lookup"><span data-stu-id="1916b-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="1916b-104">Há duas partes a entidades.</span><span class="sxs-lookup"><span data-stu-id="1916b-104">There are two parts to entities.</span></span> <span data-ttu-id="1916b-105">Primeiro, você deve a um nome ao conteúdo de substituição utilizando uma declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="1916b-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="1916b-106">Uma declaração de entidade é criada usando a sintaxe de `<!ENTITY name "value">` em um Document type definition (DTD) ou no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="1916b-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="1916b-107">Em segundo lugar, o nome definido na declaração de entidade é usado posteriormente em XML.</span><span class="sxs-lookup"><span data-stu-id="1916b-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="1916b-108">Quando usado em XML, é chamado uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="1916b-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="1916b-109">Por exemplo, a seguinte declaração de entidade declara uma entidade de nome `publisher` que está sendo associado com o conteúdo de “de pressionamento Microsoft”.</span><span class="sxs-lookup"><span data-stu-id="1916b-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="1916b-110">O exemplo a seguir mostra o uso dessa declaração de entidade em XML como uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="1916b-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="1916b-111">Alguns analisadores expandem automaticamente entidades quando um documento é carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="1916b-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="1916b-112">Portanto, quando XML está sendo lido na memória, as declarações de entidade são recordadas e salvas.</span><span class="sxs-lookup"><span data-stu-id="1916b-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="1916b-113">Quando o analisador encontra posteriormente os caracteres de `&;` , que identifica uma referência de entidade geral, o analisador pesquisa que nome em uma tabela da declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="1916b-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="1916b-114">A referência, `&publisher;` é substituído pelo conteúdo que representa.</span><span class="sxs-lookup"><span data-stu-id="1916b-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="1916b-115">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="1916b-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="1916b-116">expanda a referência de entidade e substituir `&publisher;` com o conteúdo da Microsoft oferece seguinte XML expandido.</span><span class="sxs-lookup"><span data-stu-id="1916b-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="1916b-117">**Saída**</span><span class="sxs-lookup"><span data-stu-id="1916b-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="1916b-118">Há muitos tipos das entidades.</span><span class="sxs-lookup"><span data-stu-id="1916b-118">There are many kinds of entities.</span></span> <span data-ttu-id="1916b-119">O diagrama a seguir mostra a divisão dos tipos de entidade e da terminologia.</span><span class="sxs-lookup"><span data-stu-id="1916b-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="1916b-120">![Fluxograma da hierarquia de tipo de entidade](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="1916b-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="1916b-121">O padrão para a implementação do Microsoft .NET Framework do XML DOM Document Object Model () é preservar as referências de entidades e expandir as entidades quando o XML é carregado.</span><span class="sxs-lookup"><span data-stu-id="1916b-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="1916b-122">A implicação é que um documento é carregado no DOM, um **XmlEntityReference** nó que contém a variável de referência `&publisher;` é criada, conosco filho que representa o conteúdo da entidade declarada no DTD.</span><span class="sxs-lookup"><span data-stu-id="1916b-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="1916b-123">Usando o `<!ENTITY publisher "Microsoft Press">` declaração de entidade, o diagrama a seguir mostra o **XmlEntity** e **XmlText** nós criados a partir dessa declaração.</span><span class="sxs-lookup"><span data-stu-id="1916b-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="1916b-124">![nós criados na declaração de entidade](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="1916b-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="1916b-125">As diferenças quando as referências a entidades são expandidos e quando não são faz uma diferença no qual nós são gerados na árvore DOM, na memória.</span><span class="sxs-lookup"><span data-stu-id="1916b-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="1916b-126">A diferença em nós que são gerados é explicada nos tópicos [referências a entidades são preservadas](../../../../docs/standard/data/xml/entity-references-are-preserved.md) e [referências a entidades são expandidos e não preservadas](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="1916b-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1916b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1916b-127">See Also</span></span>  
 [<span data-ttu-id="1916b-128">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="1916b-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
