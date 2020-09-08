---
title: Visão geral da classe XDocument
description: A classe LINQ to XML XDocument contém as informações necessárias para um documento XML válido. Em muitos casos, você não precisa da funcionalidade de um objeto XDocument e pode usar um objeto XElement em vez disso.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551853"
---
# <a name="xdocument-class-overview"></a><span data-ttu-id="5c3e7-104">Visão geral da classe XDocument</span><span class="sxs-lookup"><span data-stu-id="5c3e7-104">XDocument class overview</span></span>

<span data-ttu-id="5c3e7-105">A <xref:System.Xml.Linq.XDocument> classe contém as informações necessárias para um documento XML válido, que inclui uma declaração XML, instruções de processamento e comentários.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document, which includes an XML declaration, processing instructions, and comments.</span></span>

<span data-ttu-id="5c3e7-106">Você só precisa criar <xref:System.Xml.Linq.XDocument> objetos se precisar da funcionalidade específica fornecida pela <xref:System.Xml.Linq.XDocument> classe.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-106">You only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="5c3e7-107">Em muitas circunstâncias, você pode trabalhar diretamente com <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-107">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="5c3e7-108">Trabalhar diretamente com <xref:System.Xml.Linq.XElement> é um modelo de programação mais simples.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-108">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>

<span data-ttu-id="5c3e7-109"><xref:System.Xml.Linq.XDocument> deriva de <xref:System.Xml.Linq.XContainer> , portanto, ele pode conter nós filho.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-109"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>, so it can contain child nodes.</span></span> <span data-ttu-id="5c3e7-110">Entretanto, os objetos <xref:System.Xml.Linq.XDocument> podem ter apenas um nó <xref:System.Xml.Linq.XElement> filho.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-110">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="5c3e7-111">Isso reflete o padrão XML de que pode haver apenas um elemento raiz em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-111">This reflects the XML standard that there can be only one root element in an XML document.</span></span>

## <a name="components-of-xdocument"></a><span data-ttu-id="5c3e7-112">Componentes de XDocument</span><span class="sxs-lookup"><span data-stu-id="5c3e7-112">Components of XDocument</span></span>

<span data-ttu-id="5c3e7-113">Um <xref:System.Xml.Linq.XDocument> pode conter os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="5c3e7-113">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>

- <span data-ttu-id="5c3e7-114">Um objeto <xref:System.Xml.Linq.XDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-114">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="5c3e7-115"><xref:System.Xml.Linq.XDeclaration> permite que você especifique as partes pertinentes de uma declaração XML: a versão XML, a codificação do documento e se o documento XML é autônomo.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-115"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is standalone.</span></span>
- <span data-ttu-id="5c3e7-116">Um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-116">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="5c3e7-117">Esse objeto é o nó raiz do documento XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-117">This object is the root node of the XML document.</span></span>
- <span data-ttu-id="5c3e7-118">Qualquer número de objetos <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-118">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="5c3e7-119">Uma instrução de processamento comunica informações a um aplicativo que processa o XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-119">A processing instruction communicates information to an application that processes the XML.</span></span>
- <span data-ttu-id="5c3e7-120">Qualquer número de objetos <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-120">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="5c3e7-121">Os comentários serão irmãos do elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-121">The comments will be siblings to the root element.</span></span> <span data-ttu-id="5c3e7-122">O <xref:System.Xml.Linq.XComment> objeto não pode ser o primeiro argumento na lista, porque não é válido para um documento XML começar com um comentário.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-122">The <xref:System.Xml.Linq.XComment> object can't be the first argument in the list, because it's not valid for an XML document to start with a comment.</span></span>
- <span data-ttu-id="5c3e7-123">Um <xref:System.Xml.Linq.XDocumentType> para o DTD.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-123">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>

<span data-ttu-id="5c3e7-124">Quando você serializa um <xref:System.Xml.Linq.XDocument>, mesmo que `XDocument.Declaration` seja `null`, a saída terá uma declaração XML se o gravador tiver `Writer.Settings.OmitXmlDeclaration` definido como `false` (o padrão).</span><span class="sxs-lookup"><span data-stu-id="5c3e7-124">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>

<span data-ttu-id="5c3e7-125">Por padrão, LINQ to XML define a versão como "1,0" e define a codificação como "UTF-8".</span><span class="sxs-lookup"><span data-stu-id="5c3e7-125">By default, LINQ to XML sets the version to "1.0", and sets the encoding to "utf-8".</span></span>

## <a name="use-xelement-without-xdocument"></a><span data-ttu-id="5c3e7-126">Usar XElement sem XDocument</span><span class="sxs-lookup"><span data-stu-id="5c3e7-126">Use XElement without XDocument</span></span>

<span data-ttu-id="5c3e7-127">Como mencionado anteriormente, a <xref:System.Xml.Linq.XElement> classe é a classe principal na interface de programação de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-127">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the LINQ to XML programming interface.</span></span> <span data-ttu-id="5c3e7-128">Em muitos casos, seu aplicativo não exigirá que você crie um documento.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-128">In many cases, your application won't require that you create a document.</span></span> <span data-ttu-id="5c3e7-129">Usando a <xref:System.Xml.Linq.XElement> classe, você pode:</span><span class="sxs-lookup"><span data-stu-id="5c3e7-129">By using the <xref:System.Xml.Linq.XElement> class, you can:</span></span>

- <span data-ttu-id="5c3e7-130">Crie uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-130">Create an XML tree.</span></span>
- <span data-ttu-id="5c3e7-131">Adicione outras árvores XML a ela.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-131">Add other XML trees to it.</span></span>
- <span data-ttu-id="5c3e7-132">Modifique a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-132">Modify the XML tree.</span></span>
- <span data-ttu-id="5c3e7-133">Salve-o.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-133">Save it.</span></span>

## <a name="use-xdocument"></a><span data-ttu-id="5c3e7-134">Usar XDocument</span><span class="sxs-lookup"><span data-stu-id="5c3e7-134">Use XDocument</span></span>

<span data-ttu-id="5c3e7-135">Para construir um <xref:System.Xml.Linq.XDocument>, use a construção funcional exatamente como você faz para criar objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-135">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="5c3e7-136">O exemplo a seguir cria um <xref:System.Xml.Linq.XDocument> objeto e seus objetos contidos associados.</span><span class="sxs-lookup"><span data-stu-id="5c3e7-136">The following example creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

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

<span data-ttu-id="5c3e7-137">O exemplo produz essa saída no test.xml:</span><span class="sxs-lookup"><span data-stu-id="5c3e7-137">The example produces this output in test.xml:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5c3e7-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c3e7-138">See also</span></span>

- [<span data-ttu-id="5c3e7-139">Visão geral de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5c3e7-139">LINQ to XML overview</span></span>](linq-xml-overview.md)
