---
title: Analisando XML (C#)
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
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 13807e57b3616d51bd88b37d0acc703a18445a02
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="parsing-xml-c"></a><span data-ttu-id="274f1-102">Analisando XML (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-102">Parsing XML (C#)</span></span>
<span data-ttu-id="274f1-103">Os tópicos nesta seção descrevem como analisar documentos XML.</span><span class="sxs-lookup"><span data-stu-id="274f1-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="274f1-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="274f1-104">In This Section</span></span>  
  
|<span data-ttu-id="274f1-105">Tópico</span><span class="sxs-lookup"><span data-stu-id="274f1-105">Topic</span></span>|<span data-ttu-id="274f1-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="274f1-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="274f1-107">Como analisar uma cadeia de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="274f1-108">Mostra como analisar uma cadeia de caracteres para criar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="274f1-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="274f1-109">Como carregar XML de um arquivo (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="274f1-110">Mostra como carregar XML de um URI usando o método <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="274f1-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="274f1-111">Preservar espaço em branco para carregar ou ao analisar XML</span><span class="sxs-lookup"><span data-stu-id="274f1-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="274f1-112">Descreve como controlar o comportamento de espaço em branco de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ao carregar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="274f1-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="274f1-113">Como capturar erros de análise (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="274f1-114">Mostra como detectar XML malformado ou inválido.</span><span class="sxs-lookup"><span data-stu-id="274f1-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="274f1-115">Como criar uma árvore de um XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="274f1-116">Mostra como criar uma árvore XML diretamente de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="274f1-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="274f1-117">Como transmitir fragmentos XML de um XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="274f1-118">Mostra como transmitir fragmentos XML usando um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="274f1-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="274f1-119">Quando você precisa processar arbitrariamente grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="274f1-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="274f1-120">Em vez disso, você pode transmitir fragmentos XML.</span><span class="sxs-lookup"><span data-stu-id="274f1-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="274f1-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="274f1-121">See Also</span></span>  
 [<span data-ttu-id="274f1-122">Criando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="274f1-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

