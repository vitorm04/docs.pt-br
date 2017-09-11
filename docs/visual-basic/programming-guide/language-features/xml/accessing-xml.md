---
title: Acessando XML no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fe096d3686adc2386235944b59b51fb7442dd096
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="eb892-102">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb892-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="eb892-103">fornece propriedades de eixo XML para acessar e navegar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] estruturas.</span><span class="sxs-lookup"><span data-stu-id="eb892-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] structures.</span></span> <span data-ttu-id="eb892-104">Essas propriedades usam uma sintaxe especial para que você possa acessar elementos e atributos, especificando os nomes XML.</span><span class="sxs-lookup"><span data-stu-id="eb892-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="eb892-105">A tabela a seguir lista os recursos de linguagem que permitem que você acesse elementos e atributos no XML [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb892-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="eb892-106">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="eb892-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="eb892-107">Descrição da propriedade</span><span class="sxs-lookup"><span data-stu-id="eb892-107">Property description</span></span>|<span data-ttu-id="eb892-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb892-108">Example</span></span>|<span data-ttu-id="eb892-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb892-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="eb892-110">*eixo filho*</span><span class="sxs-lookup"><span data-stu-id="eb892-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="eb892-111">Obtém todos os `phone` elementos que são elementos filho do `contact` elemento.</span><span class="sxs-lookup"><span data-stu-id="eb892-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="eb892-112">*eixo de atributo*</span><span class="sxs-lookup"><span data-stu-id="eb892-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="eb892-113">Obtém todos os `type` atributos do `phone` elemento.</span><span class="sxs-lookup"><span data-stu-id="eb892-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="eb892-114">*eixo descendente*</span><span class="sxs-lookup"><span data-stu-id="eb892-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="eb892-115">Obtém todos os `name` elementos do `contacts` elemento, independentemente da profundidade da hierarquia que ocorrem.</span><span class="sxs-lookup"><span data-stu-id="eb892-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="eb892-116">*indexador de extensão*</span><span class="sxs-lookup"><span data-stu-id="eb892-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="eb892-117">Obtém o primeiro `name` elemento da sequência.</span><span class="sxs-lookup"><span data-stu-id="eb892-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="eb892-118">*value*</span><span class="sxs-lookup"><span data-stu-id="eb892-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="eb892-119">Obtém a representação de cadeia de caracteres do primeiro objeto na sequência, ou `Nothing` se a sequência for vazia.</span><span class="sxs-lookup"><span data-stu-id="eb892-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="eb892-120">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="eb892-120">In This Section</span></span>  
 [<span data-ttu-id="eb892-121">Como acessar elementos descendentes XML</span><span class="sxs-lookup"><span data-stu-id="eb892-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="eb892-122">Mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML especificado.</span><span class="sxs-lookup"><span data-stu-id="eb892-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="eb892-123">Como acessar elementos filho XML</span><span class="sxs-lookup"><span data-stu-id="eb892-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="eb892-124">Mostra como usar um filho propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="eb892-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="eb892-125">Como acessar atributos XML</span><span class="sxs-lookup"><span data-stu-id="eb892-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="eb892-126">Mostra como usar uma propriedade de eixo de atributo para acessar todos os atributos XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="eb892-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="eb892-127">Como declarar e usar prefixos de namespace de XML</span><span class="sxs-lookup"><span data-stu-id="eb892-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="eb892-128">Mostra como declarar um prefixo de namespace XML e usá-lo para criar e acessar elementos XML.</span><span class="sxs-lookup"><span data-stu-id="eb892-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eb892-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="eb892-129">Related Sections</span></span>  
 [<span data-ttu-id="eb892-130">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="eb892-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="eb892-131">Fornece links para seções que descrevem as várias propriedades de acesso do XML.</span><span class="sxs-lookup"><span data-stu-id="eb892-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="eb892-132">Visão geral de LINQ to XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb892-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="eb892-133">Fornece uma introdução ao uso [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb892-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="eb892-134">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb892-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="eb892-135">Fornece uma introdução ao uso de literais XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb892-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="eb892-136">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb892-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="eb892-137">Fornece links para seções sobre como carregar e modificar XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb892-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="eb892-138">XML</span><span class="sxs-lookup"><span data-stu-id="eb892-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="eb892-139">Fornece links para seções que descrevem como usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb892-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>
