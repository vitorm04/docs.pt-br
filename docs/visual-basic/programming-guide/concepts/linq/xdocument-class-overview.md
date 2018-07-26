---
title: Visão geral da classe XDocument (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 98ab095d67add2375eaf912ade71114c022b2ebb
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220942"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="b029b-102">Visão geral da classe XDocument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b029b-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b029b-103">Este tópico apresenta a classe <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="b029b-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="b029b-104">Visão geral da classe XDocument</span><span class="sxs-lookup"><span data-stu-id="b029b-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="b029b-105">A classe <xref:System.Xml.Linq.XDocument> contém as informações necessárias para um documento XML válido.</span><span class="sxs-lookup"><span data-stu-id="b029b-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="b029b-106">Isso inclui uma declaração XML, instruções de processamento e comentários.</span><span class="sxs-lookup"><span data-stu-id="b029b-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="b029b-107">Observe que você só precisará criar objetos <xref:System.Xml.Linq.XDocument> se precisar da funcionalidade específica fornecida pela classe <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="b029b-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="b029b-108">Em muitas circunstâncias, você pode trabalhar diretamente com <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b029b-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b029b-109">Trabalhar diretamente com <xref:System.Xml.Linq.XElement> é um modelo de programação mais simples.</span><span class="sxs-lookup"><span data-stu-id="b029b-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="b029b-110"><xref:System.Xml.Linq.XDocument> deriva de <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="b029b-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="b029b-111">Portanto, pode conter nós filho.</span><span class="sxs-lookup"><span data-stu-id="b029b-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="b029b-112">Entretanto, os objetos <xref:System.Xml.Linq.XDocument> podem ter apenas um nó <xref:System.Xml.Linq.XElement> filho.</span><span class="sxs-lookup"><span data-stu-id="b029b-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="b029b-113">Isso reflete o padrão XML de que pode haver apenas um elemento raiz em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b029b-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="b029b-114">Componentes de XDocument</span><span class="sxs-lookup"><span data-stu-id="b029b-114">Components of XDocument</span></span>  
 <span data-ttu-id="b029b-115">Um <xref:System.Xml.Linq.XDocument> pode conter os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="b029b-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="b029b-116">Um objeto <xref:System.Xml.Linq.XDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="b029b-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="b029b-117"><xref:System.Xml.Linq.XDeclaration> permite que você especifique as partes pertinentes de uma declaração XML: a versão XML, a codificação do documento e se o documento XML é autônomo.</span><span class="sxs-lookup"><span data-stu-id="b029b-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="b029b-118">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b029b-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b029b-119">Esse é o nó raiz do documento XML.</span><span class="sxs-lookup"><span data-stu-id="b029b-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="b029b-120">Qualquer número de objetos <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="b029b-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="b029b-121">Uma instrução de processamento comunica informações a um aplicativo que processa o XML.</span><span class="sxs-lookup"><span data-stu-id="b029b-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="b029b-122">Qualquer número de objetos <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="b029b-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="b029b-123">Os comentários serão irmãos do elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="b029b-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="b029b-124">O objeto <xref:System.Xml.Linq.XComment> não pode ser o primeiro argumento da lista, pois não é válido um documento XML iniciar com um comentário.</span><span class="sxs-lookup"><span data-stu-id="b029b-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="b029b-125">Um <xref:System.Xml.Linq.XDocumentType> para o DTD.</span><span class="sxs-lookup"><span data-stu-id="b029b-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="b029b-126">Quando você serializa um <xref:System.Xml.Linq.XDocument>, mesmo que `XDocument.Declaration` seja `null`, a saída terá uma declaração XML se o gravador tiver `Writer.Settings.OmitXmlDeclaration` definido como `false` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="b029b-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="b029b-127">Por padrão, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] define a versão como “1.0 " e a codificação como “utf-8”.</span><span class="sxs-lookup"><span data-stu-id="b029b-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="b029b-128">Usando XElement sem XDocument</span><span class="sxs-lookup"><span data-stu-id="b029b-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="b029b-129">Conforme mencionado anteriormente, a classe <xref:System.Xml.Linq.XElement> é a classe principal da interface de programação [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b029b-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="b029b-130">Em muitos casos, seu aplicativo não exigirá que você crie um documento.</span><span class="sxs-lookup"><span data-stu-id="b029b-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="b029b-131">Usando a classe <xref:System.Xml.Linq.XElement>, você poderá criar uma árvore XML, adicionar outras árvores XML a ela, modificar a árvore XML e salvá-la.</span><span class="sxs-lookup"><span data-stu-id="b029b-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="b029b-132">Usando XDocument</span><span class="sxs-lookup"><span data-stu-id="b029b-132">Using XDocument</span></span>  
 <span data-ttu-id="b029b-133">Para construir um <xref:System.Xml.Linq.XDocument>, use a construção funcional exatamente como você faz para criar objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b029b-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b029b-134">O código a seguir cria um objeto <xref:System.Xml.Linq.XDocument> e seus objetos independentes associados.</span><span class="sxs-lookup"><span data-stu-id="b029b-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="b029b-135">Quando você examina o arquivo test.xml, obtém a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="b029b-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b029b-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b029b-136">See Also</span></span>  
 [<span data-ttu-id="b029b-137">LINQ to XML visão geral da programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b029b-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
