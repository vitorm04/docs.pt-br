---
title: Salvando e escrevendo um documento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad656e2db17e44733b5718fe2e3a2a48afcb1381
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="5bce9-102">Salvando e escrevendo um documento</span><span class="sxs-lookup"><span data-stu-id="5bce9-102">Saving and Writing a Document</span></span>
<span data-ttu-id="5bce9-103">Quando você carrega e salvar <xref:System.Xml.XmlDocument>, o documento salvo pode diferir do original das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5bce9-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
-   <span data-ttu-id="5bce9-104">Se a propriedade <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> for definida como `true` antes que o método <xref:System.Xml.XmlDocument.Save%2A> seja chamado, o espaço em branco no documento será preservado na saída; se essa propriedade for `false`, o <xref:System.Xml.XmlDocument> recua automaticamente a saída.</span><span class="sxs-lookup"><span data-stu-id="5bce9-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
-   <span data-ttu-id="5bce9-105">Todos os espaços em branco entre atributos são reduzidos a um único caractere de espaço.</span><span class="sxs-lookup"><span data-stu-id="5bce9-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
-   <span data-ttu-id="5bce9-106">O espaço em branco entre elementos é alterado.</span><span class="sxs-lookup"><span data-stu-id="5bce9-106">The white space between elements is changed.</span></span> <span data-ttu-id="5bce9-107">O espaço em branco significativo é preservado e o espaço em branco insignificante não é.</span><span class="sxs-lookup"><span data-stu-id="5bce9-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="5bce9-108">Mas quando o documento é salvo, ele usará o <xref:System.Xml.XmlTextWriter> **recuo** modo por padrão se imprimir a saída para torná-lo mais legível.</span><span class="sxs-lookup"><span data-stu-id="5bce9-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
-   <span data-ttu-id="5bce9-109">O caractere de aspas usado ao redor de valores de atributo é alterado para aspas duplas por padrão.</span><span class="sxs-lookup"><span data-stu-id="5bce9-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="5bce9-110">Você pode usar a propriedade <xref:System.Xml.XmlTextReader.QuoteChar%2A> em <xref:System.Xml.XmlTextWriter> para definir o caractere de aspas para aspas duplas ou aspas simples.</span><span class="sxs-lookup"><span data-stu-id="5bce9-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
-   <span data-ttu-id="5bce9-111">Por padrão, as entidades de caracteres numéricos como `{` são expandidas.</span><span class="sxs-lookup"><span data-stu-id="5bce9-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
-   <span data-ttu-id="5bce9-112">A marca de ordem de byte encontrada no documento de entrada não é preservada.</span><span class="sxs-lookup"><span data-stu-id="5bce9-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="5bce9-113">O UCS-2 é salvo como UTF-8 a menos que você crie explicitamente uma declaração XML que especifica uma codificação diferente.</span><span class="sxs-lookup"><span data-stu-id="5bce9-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
-   <span data-ttu-id="5bce9-114">Se você quiser escrever o <xref:System.Xml.XmlDocument> em um arquivo ou um fluxo, a saída escreve o mesmo que o conteúdo do documento.</span><span class="sxs-lookup"><span data-stu-id="5bce9-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="5bce9-115">Isto é, o <xref:System.Xml.XmlDeclaration> é escrito somente se houver um contido no documento e a codificação usada ao escrever o documento é a mesma fornecida no nó de declaração.</span><span class="sxs-lookup"><span data-stu-id="5bce9-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="5bce9-116">Escrevendo um XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="5bce9-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="5bce9-117">Os membros <xref:System.Xml.XmlDocument> e <xref:System.Xml.XmlDeclaration> de <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A> e <xref:System.Xml.XmlNode.WriteTo%2A>, além dos métodos <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlDocument.Save%2A> e de <xref:System.Xml.XmlDocument.WriteContentTo%2A>, criam uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="5bce9-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="5bce9-118">Para as propriedades <xref:System.Xml.XmlDocument> de <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A> e <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, e os métodos <xref:System.Xml.XmlDocument.WriteContentTo%2A>, a codificação escrita na declaração XML é obtida do nó <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="5bce9-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="5bce9-119">Se não houver nenhum nó <xref:System.Xml.XmlDeclaration>, o <xref:System.Xml.XmlDeclaration> não será escrito. Se não houver codificação no nó <xref:System.Xml.XmlDeclaration>, a codificação não será escrita na declaração XML.</span><span class="sxs-lookup"><span data-stu-id="5bce9-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="5bce9-120">Os métodos <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> e <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> sempre escrevem <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="5bce9-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="5bce9-121">Esses métodos utilizam a codificação do escritor para o qual eles estão escrevendo.</span><span class="sxs-lookup"><span data-stu-id="5bce9-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="5bce9-122">Isto é, o valor de codificação no escritor substitui a codificação no documento e no <xref:System.Xml.XmlDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="5bce9-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="5bce9-123">Por exemplo, o código a seguir não escreve uma codificação na declaração XML encontrada no arquivo de saída `out.xml`.</span><span class="sxs-lookup"><span data-stu-id="5bce9-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="5bce9-124">Para o método <xref:System.Xml.XmlDocument.Save%2A>, a declaração XML é escrita usando o método <xref:System.Xml.XmlWriter.WriteStartDocument%2A> na classe <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5bce9-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="5bce9-125">Portanto, substituir o método <xref:System.Xml.XmlWriter.WriteStartDocument%2A> altera o modo como o início do documento é escrito.</span><span class="sxs-lookup"><span data-stu-id="5bce9-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="5bce9-126">Para os membros <xref:System.Xml.XmlDeclaration> de <xref:System.Xml.XmlNode.OuterXml%2A>, de <xref:System.Xml.XmlDeclaration.WriteTo%2A> e <xref:System.Xml.XmlNode.InnerXml%2A>, se a propriedade <xref:System.Xml.XmlDeclaration.Encoding%2A> não estiver definida, nenhuma codificação será escrita. Caso contrário, a codificação escrita na declaração XML será a mesma que a codificação localizada na propriedade <xref:System.Xml.XmlDeclaration.Encoding%2A>.</span><span class="sxs-lookup"><span data-stu-id="5bce9-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="5bce9-127">Escrevendo o conteúdo do documento usando a propriedade OuterXml</span><span class="sxs-lookup"><span data-stu-id="5bce9-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="5bce9-128">A propriedade <xref:System.Xml.XmlNode.OuterXml%2A> é uma extensão da Microsoft para os padrões DOM (Document Object Model) de XML do W3C (World Wide Web Consortium).</span><span class="sxs-lookup"><span data-stu-id="5bce9-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="5bce9-129">A propriedade <xref:System.Xml.XmlNode.OuterXml%2A> é usada para obter a marcação do documento XML inteiro ou apenas a marcação de um único nó e seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="5bce9-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="5bce9-130"><xref:System.Xml.XmlNode.OuterXml%2A> retorna a marcação que representa o nó determinado e todos os seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="5bce9-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="5bce9-131">O exemplo de código a seguir mostra como salvar um documento em sua totalidade como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5bce9-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="5bce9-132">O exemplo de código a seguir mostra como salvar apenas o elemento do documento.</span><span class="sxs-lookup"><span data-stu-id="5bce9-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="5bce9-133">Ao contrário, você pode usar a propriedade <xref:System.Xml.XmlNode.InnerText%2A> se quiser o conteúdo dos nós filho.</span><span class="sxs-lookup"><span data-stu-id="5bce9-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bce9-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bce9-134">See Also</span></span>  
 [<span data-ttu-id="5bce9-135">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="5bce9-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
