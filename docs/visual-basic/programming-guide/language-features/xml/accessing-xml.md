---
title: Acessar XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410303"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="ae260-102">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae260-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="ae260-103">Visual Basic fornece propriedades de eixo XML para acessar e navegar em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="ae260-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="ae260-104">Essas propriedades usam uma sintaxe especial para permitir que você acesse elementos e atributos especificando os nomes XML.</span><span class="sxs-lookup"><span data-stu-id="ae260-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="ae260-105">A tabela a seguir lista os recursos de linguagem que permitem acessar elementos e atributos XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae260-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="ae260-106">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="ae260-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="ae260-107">Descrição da propriedade</span><span class="sxs-lookup"><span data-stu-id="ae260-107">Property description</span></span>|<span data-ttu-id="ae260-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae260-108">Example</span></span>|<span data-ttu-id="ae260-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae260-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="ae260-110">*eixo filho*</span><span class="sxs-lookup"><span data-stu-id="ae260-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="ae260-111">Obtém todos os `phone` elementos que são elementos filho do `contact` elemento.</span><span class="sxs-lookup"><span data-stu-id="ae260-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="ae260-112">*eixo de atributo*</span><span class="sxs-lookup"><span data-stu-id="ae260-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="ae260-113">Obtém todos os `type` atributos do `phone` elemento.</span><span class="sxs-lookup"><span data-stu-id="ae260-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="ae260-114">*eixo descendente*</span><span class="sxs-lookup"><span data-stu-id="ae260-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="ae260-115">Obtém todos os `name` elementos do `contacts` elemento, independentemente da profundidade na hierarquia que eles ocorrem.</span><span class="sxs-lookup"><span data-stu-id="ae260-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="ae260-116">*indexador de extensão*</span><span class="sxs-lookup"><span data-stu-id="ae260-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="ae260-117">Obtém o primeiro `name` elemento da sequência.</span><span class="sxs-lookup"><span data-stu-id="ae260-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="ae260-118">*value*</span><span class="sxs-lookup"><span data-stu-id="ae260-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="ae260-119">Obtém a representação da cadeia de caracteres do primeiro objeto na sequência ou `Nothing` se a sequência está vazia.</span><span class="sxs-lookup"><span data-stu-id="ae260-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="ae260-120">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ae260-120">In This Section</span></span>  
 [<span data-ttu-id="ae260-121">Como acessar elementos descendentes XML</span><span class="sxs-lookup"><span data-stu-id="ae260-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="ae260-122">Mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidos em um elemento XML especificado.</span><span class="sxs-lookup"><span data-stu-id="ae260-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="ae260-123">Como acessar elementos filho XML</span><span class="sxs-lookup"><span data-stu-id="ae260-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="ae260-124">Mostra como usar uma propriedade de eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ae260-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="ae260-125">Como acessar atributos XML</span><span class="sxs-lookup"><span data-stu-id="ae260-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="ae260-126">Mostra como usar uma propriedade de eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ae260-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="ae260-127">Como declarar e usar prefixos de namespace XML</span><span class="sxs-lookup"><span data-stu-id="ae260-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="ae260-128">Mostra como declarar um prefixo de namespace XML e usá-lo para criar e acessar elementos XML.</span><span class="sxs-lookup"><span data-stu-id="ae260-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ae260-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ae260-129">Related Sections</span></span>  
 [<span data-ttu-id="ae260-130">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="ae260-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="ae260-131">Fornece links para seções que descrevem as várias propriedades de acesso de XML.</span><span class="sxs-lookup"><span data-stu-id="ae260-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="ae260-132">Visão geral de LINQ to XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae260-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="ae260-133">Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae260-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ae260-134">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae260-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="ae260-135">Fornece uma introdução ao uso de literais XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae260-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ae260-136">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae260-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="ae260-137">Fornece links para seções sobre como carregar e modificar XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae260-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="ae260-138">XML</span><span class="sxs-lookup"><span data-stu-id="ae260-138">XML</span></span>](index.md)  
 <span data-ttu-id="ae260-139">Fornece links para seções que descrevem como usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ae260-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
