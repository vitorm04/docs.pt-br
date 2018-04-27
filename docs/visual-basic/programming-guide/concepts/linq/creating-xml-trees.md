---
title: Criando árvores XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08efc9a9b519d2b56f8503e050b9332be580d124
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="c6a3f-102">Criando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="c6a3f-103">Uma das tarefas XML mais comuns é construir uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="c6a3f-104">Esta seção descreve várias maneiras de criá-las.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6a3f-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c6a3f-105">In This Section</span></span>  
  
|<span data-ttu-id="c6a3f-106">Tópico</span><span class="sxs-lookup"><span data-stu-id="c6a3f-106">Topic</span></span>|<span data-ttu-id="c6a3f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6a3f-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c6a3f-108">Construção funcional (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="c6a3f-109">Fornece uma visão geral da construção funcional em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6a3f-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="c6a3f-110">A construção funcional habilita você a criar toda ou parte da árvore XML em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="c6a3f-111">Este tópico também mostra como inserir consultas ao construir uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="c6a3f-112">Introdução a literais XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6a3f-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="c6a3f-113">Fornece uma breve introdução à criação de árvores no Visual Basic usando literais XML.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-113">Provides a quick introduction to creating trees in Visual Basic by using XML literals.</span></span> <span data-ttu-id="c6a3f-114">Este tópico inclui links para documentação do Visual Basic dos literais XML.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-114">This topic includes links to the Visual Basic documentation of XML literals.</span></span>|  
|[<span data-ttu-id="c6a3f-115">Clonagem versus Anexando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="c6a3f-116">Demonstra a diferença entre adicionar nós de uma árvore XML existente (os nós são clonados e depois adicionados) e adicionar nós sem o pai (eles são simplesmente anexados).</span><span class="sxs-lookup"><span data-stu-id="c6a3f-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="c6a3f-117">Análise de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="c6a3f-118">Mostra como analisar o XML de uma variedade de fontes.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-118">Shows how to parse XML from a variety of sources.</span></span> <span data-ttu-id="c6a3f-119">O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é disposto em camadas sobre <xref:System.Xml.XmlReader>, que é usado para analisar o XML.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-119">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="c6a3f-120">Como: preencher uma árvore XML com um XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="c6a3f-121">Mostra como popular uma árvore XML usando um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="c6a3f-122">Como: validar usando XSD (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="c6a3f-123">Mostra como validar uma árvore XML usando XSD.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="c6a3f-124">Conteúdo válido de objetos XElement e XDocument</span><span class="sxs-lookup"><span data-stu-id="c6a3f-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="c6a3f-125">Descreve os argumentos válidos que podem ser passados para os construtores e os métodos que são usados para adicionar conteúdo a elementos e documentos.</span><span class="sxs-lookup"><span data-stu-id="c6a3f-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6a3f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6a3f-126">See Also</span></span>  
 [<span data-ttu-id="c6a3f-127">Guia de programação (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6a3f-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
