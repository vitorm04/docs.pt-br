---
title: "Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 293e8de848f83517211e3f3ed640102a2c534764
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="43e76-102">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="43e76-103">Este tutorial mostra como aplicar a abordagem transformacional funcional e o LINQ to XML para manipular documentos XML.</span><span class="sxs-lookup"><span data-stu-id="43e76-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="43e76-104">Os exemplos de C# consultam e manipulam informações em documentos do Office Open XML WordprocessingML que são salvos pelo Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="43e76-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="43e76-105">Para obter mais informações, consulte o site [Desenvolvedor de OpenXML](http://go.microsoft.com/fwlink/?LinkID=95573).</span><span class="sxs-lookup"><span data-stu-id="43e76-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43e76-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="43e76-106">In This Section</span></span>  
  
|<span data-ttu-id="43e76-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="43e76-107">Topic</span></span>|<span data-ttu-id="43e76-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="43e76-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="43e76-109">Formato de documentos de WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="43e76-110">Fornece uma explicação rápida dos detalhes de um documento WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="43e76-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="43e76-111">Criando o documento do Office Open XML de origem (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="43e76-112">Fornece instruções passo a passo para criar o documento de origem para consultas neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="43e76-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="43e76-113">Localizando o estilo de parágrafo padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="43e76-114">Mostra uma consulta para localizar o nome do estilo padrão para um documento.</span><span class="sxs-lookup"><span data-stu-id="43e76-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="43e76-115">Recuperando os parágrafos e seus estilos (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="43e76-116">Mostra uma consulta que recupera uma coleção de parágrafos de um documento.</span><span class="sxs-lookup"><span data-stu-id="43e76-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="43e76-117">Recuperando o texto dos parágrafos (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="43e76-118">Aumenta a consulta anterior para recuperar o texto de cada parágrafo.</span><span class="sxs-lookup"><span data-stu-id="43e76-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="43e76-119">Refatoração usando um método de extensão (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="43e76-120">Simplifica o código refatorando e usando um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="43e76-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="43e76-121">Refatoração usando uma função pura (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="43e76-122">Simplifica ainda mais o código refatorando e usando uma função pura.</span><span class="sxs-lookup"><span data-stu-id="43e76-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="43e76-123">Projetando XML em uma forma diferente (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="43e76-124">Conclui uma transformação XML projetando XML em um formato diferente do documento original.</span><span class="sxs-lookup"><span data-stu-id="43e76-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="43e76-125">Localizando texto em documentos do Word (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="43e76-126">Usa as consultas anteriores para localizar uma cadeia de caracteres de texto especificado em um documento.</span><span class="sxs-lookup"><span data-stu-id="43e76-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="43e76-127">Detalhes de documentos do Office Open XML WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="43e76-128">Fornece alguns detalhes de documentos do Office Open XML WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="43e76-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43e76-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43e76-129">See Also</span></span>  
 <span data-ttu-id="43e76-130">[Transformações funcionais puras de XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="43e76-130">[Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
 [<span data-ttu-id="43e76-131">Introdução às transformações funcionais puras (C#)</span><span class="sxs-lookup"><span data-stu-id="43e76-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)

