---
title: Acessando XML no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="57350-102">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57350-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="57350-103">fornece propriedades de eixo XML para acessar e navegar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="57350-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="57350-104">Essas propriedades usam uma sintaxe especial para que você possa acessar os elementos e atributos, especificando os nomes XML.</span><span class="sxs-lookup"><span data-stu-id="57350-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="57350-105">A tabela a seguir lista os recursos de linguagem que permitem acessar elementos e atributos no XML [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57350-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="57350-106">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="57350-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="57350-107">Descrição da propriedade</span><span class="sxs-lookup"><span data-stu-id="57350-107">Property description</span></span>|<span data-ttu-id="57350-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57350-108">Example</span></span>|<span data-ttu-id="57350-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="57350-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="57350-110">*eixo filho*</span><span class="sxs-lookup"><span data-stu-id="57350-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="57350-111">Obtém todos os `phone` elementos que são elementos filho do `contact` elemento.</span><span class="sxs-lookup"><span data-stu-id="57350-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="57350-112">*eixo de atributo*</span><span class="sxs-lookup"><span data-stu-id="57350-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="57350-113">Obtém todos os `type` atributos do `phone` elemento.</span><span class="sxs-lookup"><span data-stu-id="57350-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="57350-114">*eixo descendente*</span><span class="sxs-lookup"><span data-stu-id="57350-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="57350-115">Obtém todos os `name` elementos do `contacts` elemento, independentemente da profundidade da hierarquia que eles ocorrem.</span><span class="sxs-lookup"><span data-stu-id="57350-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="57350-116">*indexador de extensão*</span><span class="sxs-lookup"><span data-stu-id="57350-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="57350-117">Obtém a primeira `name` elemento da sequência.</span><span class="sxs-lookup"><span data-stu-id="57350-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="57350-118">*value*</span><span class="sxs-lookup"><span data-stu-id="57350-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="57350-119">Obtém a representação de cadeia de caracteres do primeiro objeto na sequência, ou `Nothing` se a sequência for vazia.</span><span class="sxs-lookup"><span data-stu-id="57350-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="57350-120">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="57350-120">In This Section</span></span>  
 [<span data-ttu-id="57350-121">Como acessar elementos descendentes XML</span><span class="sxs-lookup"><span data-stu-id="57350-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="57350-122">Mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML especificado.</span><span class="sxs-lookup"><span data-stu-id="57350-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="57350-123">Como acessar elementos filho XML</span><span class="sxs-lookup"><span data-stu-id="57350-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="57350-124">Mostra como usar um filho propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="57350-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="57350-125">Como acessar atributos XML</span><span class="sxs-lookup"><span data-stu-id="57350-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="57350-126">Mostra como usar uma propriedade de eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="57350-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="57350-127">Como declarar e usar prefixos de namespace de XML</span><span class="sxs-lookup"><span data-stu-id="57350-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="57350-128">Mostra como declarar um prefixo de namespace XML e usá-lo para criar e acessar elementos XML.</span><span class="sxs-lookup"><span data-stu-id="57350-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="57350-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="57350-129">Related Sections</span></span>  
 [<span data-ttu-id="57350-130">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="57350-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="57350-131">Fornece links para seções que descrevem as várias propriedades de acesso do XML.</span><span class="sxs-lookup"><span data-stu-id="57350-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="57350-132">Visão geral do LINQ to XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57350-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="57350-133">Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57350-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="57350-134">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57350-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="57350-135">Fornece uma introdução ao uso de literais XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57350-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="57350-136">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57350-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="57350-137">Fornece links para seções sobre como carregar e modificar o XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57350-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="57350-138">XML</span><span class="sxs-lookup"><span data-stu-id="57350-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="57350-139">Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="57350-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
