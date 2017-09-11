---
title: "Visão geral da classe XDocument (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f51808a64d51fb354159df1a7323ad2fc26eedc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="65d50-102">Visão geral da classe XDocument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d50-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="65d50-103">Este tópico apresenta a <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="65d50-104">Visão geral da classe XDocument</span><span class="sxs-lookup"><span data-stu-id="65d50-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="65d50-105">O <xref:System.Xml.Linq.XDocument>classe contém as informações necessárias para um documento XML válido.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="65d50-106">Isso inclui uma declaração XML, instruções de processamento e comentários.</span><span class="sxs-lookup"><span data-stu-id="65d50-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="65d50-107">Observe que você só precisa criar <xref:System.Xml.Linq.XDocument>objetos, se você precisar da funcionalidade específica fornecida pela <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="65d50-108">Em muitas circunstâncias, você pode trabalhar diretamente com <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="65d50-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="65d50-109">Trabalhar diretamente com <xref:System.Xml.Linq.XElement>é um modelo de programação mais simples.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="65d50-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="65d50-110"><xref:System.Xml.Linq.XDocument>deriva de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="65d50-111">Portanto, pode conter nós filho.</span><span class="sxs-lookup"><span data-stu-id="65d50-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="65d50-112">No entanto, <xref:System.Xml.Linq.XDocument>objetos podem ter apenas um filho <xref:System.Xml.Linq.XElement>nó.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="65d50-113">Isso reflete o padrão XML de que pode haver apenas um elemento raiz em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="65d50-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="65d50-114">Componentes de XDocument</span><span class="sxs-lookup"><span data-stu-id="65d50-114">Components of XDocument</span></span>  
 <span data-ttu-id="65d50-115">Um <xref:System.Xml.Linq.XDocument>pode conter os seguintes elementos:</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="65d50-116">Um <xref:System.Xml.Linq.XDeclaration>objeto.</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="65d50-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="65d50-117"><xref:System.Xml.Linq.XDeclaration>permite que você especifique as partes pertinentes de uma declaração XML: a versão XML, a codificação do documento, e se o documento XML é autônomo.</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="65d50-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="65d50-118">Um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="65d50-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="65d50-119">Esse é o nó raiz do documento XML.</span><span class="sxs-lookup"><span data-stu-id="65d50-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="65d50-120">Qualquer número de <xref:System.Xml.Linq.XProcessingInstruction>objetos.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="65d50-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="65d50-121">Uma instrução de processamento comunica informações a um aplicativo que processa o XML.</span><span class="sxs-lookup"><span data-stu-id="65d50-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="65d50-122">Qualquer número de <xref:System.Xml.Linq.XComment>objetos.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="65d50-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="65d50-123">Os comentários serão irmãos do elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="65d50-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="65d50-124">O <xref:System.Xml.Linq.XComment>objeto não pode ser o primeiro argumento na lista, porque ele não é válido para um documento XML iniciar com um comentário.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="65d50-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="65d50-125">Um <xref:System.Xml.Linq.XDocumentType>para o DTD.</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="65d50-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="65d50-126">Quando você serializa um <xref:System.Xml.Linq.XDocument>, mesmo se `XDocument.Declaration` é `null`, a saída terá uma declaração XML se o gravador tiver `Writer.Settings.OmitXmlDeclaration` definida como `false` (o padrão).</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="65d50-127">Por padrão, o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] define a versão como “1.0 " e a codificação como “utf-8”.</span><span class="sxs-lookup"><span data-stu-id="65d50-127">By default, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="65d50-128">Usando XElement sem XDocument</span><span class="sxs-lookup"><span data-stu-id="65d50-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="65d50-129">Como mencionado anteriormente, a <xref:System.Xml.Linq.XElement>classe é a classe principal do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programação.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="65d50-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface.</span></span> <span data-ttu-id="65d50-130">Em muitos casos, seu aplicativo não exigirá que você cria um documento.</span><span class="sxs-lookup"><span data-stu-id="65d50-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="65d50-131">Usando o <xref:System.Xml.Linq.XElement>classe, criar uma árvore XML, adicionar outras árvores XML a ela, modificar a árvore XML e salvá-la</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="65d50-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="65d50-132">Usando XDocument</span><span class="sxs-lookup"><span data-stu-id="65d50-132">Using XDocument</span></span>  
 <span data-ttu-id="65d50-133">Para construir um <xref:System.Xml.Linq.XDocument>, use a construção funcional exatamente como você faz para construir <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="65d50-134">O código a seguir cria um <xref:System.Xml.Linq.XDocument>objeto e seus associados objetos contidos.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="65d50-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="65d50-135">Quando você examina o arquivo test.xml, obtém a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="65d50-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="65d50-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65d50-136">See Also</span></span>  
 [<span data-ttu-id="65d50-137">LINQ para visão geral da programação XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65d50-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
