---
title: Declarações de entidade de leitura e referências a entidades em DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45748675"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="ff1b2-102">Declarações de entidade de leitura e referências a entidades em DOM</span><span class="sxs-lookup"><span data-stu-id="ff1b2-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="ff1b2-103">Uma entidade é uma declaração que indica um nome ser usado em XML no lugar do conteúdo ou marcação.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="ff1b2-104">Há duas partes a entidades.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-104">There are two parts to entities.</span></span> <span data-ttu-id="ff1b2-105">Primeiro, você deve a um nome ao conteúdo de substituição utilizando uma declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="ff1b2-106">Uma declaração de entidade é criada usando a sintaxe de `<!ENTITY name "value">` em um Document type definition (DTD) ou no esquema XML.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="ff1b2-107">Em segundo lugar, o nome definido na declaração de entidade é usado posteriormente em XML.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="ff1b2-108">Quando usado em XML, é chamado uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="ff1b2-109">Por exemplo, a seguinte declaração de entidade declara uma entidade de nome `publisher` que está sendo associado com o conteúdo de “de pressionamento Microsoft”.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="ff1b2-110">O exemplo a seguir mostra o uso dessa declaração de entidade em XML como uma referência de entidade.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="ff1b2-111">Alguns analisadores expandem automaticamente entidades quando um documento é carregado na memória.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="ff1b2-112">Portanto, quando XML está sendo lido na memória, as declarações de entidade são recordadas e salvas.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="ff1b2-113">Quando o analisador encontra posteriormente os caracteres de `&;` , que identifica uma referência de entidade geral, o analisador pesquisa que nome em uma tabela da declaração de entidade.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="ff1b2-114">A referência, `&publisher;` é substituído pelo conteúdo que representa.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="ff1b2-115">Usando o seguinte XML,</span><span class="sxs-lookup"><span data-stu-id="ff1b2-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="ff1b2-116">expanda a referência de entidade e substituir `&publisher;` com o conteúdo da Microsoft oferece seguinte XML expandido.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="ff1b2-117">**Saída**</span><span class="sxs-lookup"><span data-stu-id="ff1b2-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="ff1b2-118">Há muitos tipos das entidades.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-118">There are many kinds of entities.</span></span> <span data-ttu-id="ff1b2-119">O diagrama a seguir mostra a divisão dos tipos de entidade e da terminologia.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="ff1b2-120">![fluxograma da hierarquia de tipos de entidade](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="ff1b2-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="ff1b2-121">O padrão para a implementação do Microsoft .NET Framework o modelo de objeto (DOM) de documento XML é preservar as referências de entidades e não expandir quando as entidades XML é carregado.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="ff1b2-122">A implicação disso é como um documento é carregado em DOM, um nó de **XmlEntityReference** que contém a referência `&publisher;` variável é criado, com os nós filhos que representam o conteúdo no entidade declarada no DTD.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="ff1b2-123">Usando a declaração de entidade de `<!ENTITY publisher "Microsoft Press">`, o diagrama a seguir mostra os nós **XmlEntity** e **XmlText** criados dessa declaração.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="ff1b2-124">![nós criados da declaração de entidade](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="ff1b2-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="ff1b2-125">As diferenças quando as referências a entidades são expandidos e quando não são faz uma diferença no qual nós são gerados na árvore DOM, na memória.</span><span class="sxs-lookup"><span data-stu-id="ff1b2-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="ff1b2-126">A diferença em nós que são gerados é explicado nos tópicos [Referências a entidades são preservadas](../../../../docs/standard/data/xml/entity-references-are-preserved.md) e [Referências a entidades são expandidos e não preservadas](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="ff1b2-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1b2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff1b2-127">See also</span></span>

- [<span data-ttu-id="ff1b2-128">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="ff1b2-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
