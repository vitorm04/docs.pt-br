---
title: XmlDocument inseriu a XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: e990c8ca3bb2a7145157fcedd06da4ea769c6ad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290247"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="88aed-102">XmlDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="88aed-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="88aed-103">A classe de <xref:System.Xml.XmlDocument> fornece recursos de edição de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="88aed-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="88aed-104">Se o XML precisa ser editado ou alterado antes de ser enviado para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> , carregar XML em <xref:System.Xml.XmlDocument>, editá-lo, e enviá-lo na <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="88aed-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88aed-105">A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="88aed-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="88aed-106">Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="88aed-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="88aed-107">Confira [Usar a classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](migrating-from-the-xsltransform-class.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="88aed-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="88aed-108"><xref:System.Xml.XmlDocument> implementa a interface de <xref:System.Xml.XPath.IXPathNavigable> , o documento pode ser passado para o método de <xref:System.Xml.Xsl.XslTransform.Transform%2A> após editar.</span><span class="sxs-lookup"><span data-stu-id="88aed-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="88aed-109">Devido ao recurso de <xref:System.Xml.XmlDocument>, use a classe de <xref:System.Xml.XmlDocument> como entrada uma transformação é mais lento do que usar <xref:System.Xml.XPath.XPathDocument> para o idioma extensível de folha de estilos para transformações de transformações (XSLT), porque <xref:System.Xml.XPath.XPathDocument> é otimizado para consultas de idioma do caminho de XML (XPath) devido ao armazenamento interno.</span><span class="sxs-lookup"><span data-stu-id="88aed-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88aed-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88aed-110">Example</span></span>  
 <span data-ttu-id="88aed-111">O exemplo de código a seguir mostra como <xref:System.Xml.XmlDocument> pode ser fornecido para <xref:System.Xml.Xsl.XslTransform>, com a saída enviadas a <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="88aed-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="88aed-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="88aed-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="88aed-113">Transformações XSLT com a classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="88aed-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="88aed-114">A classe XslTransform implementa do processador XSLT</span><span class="sxs-lookup"><span data-stu-id="88aed-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="88aed-115">XPathNavigator nas transformações</span><span class="sxs-lookup"><span data-stu-id="88aed-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="88aed-116">XPathNodeIterator nas transformações</span><span class="sxs-lookup"><span data-stu-id="88aed-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="88aed-117">XPathDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="88aed-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="88aed-118">XmlDataDocument inseriu a XslTransform</span><span class="sxs-lookup"><span data-stu-id="88aed-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
