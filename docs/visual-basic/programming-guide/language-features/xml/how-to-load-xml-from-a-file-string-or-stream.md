---
title: 'Como: Carregar XML de um arquivo, cadeia de caracteres ou Stream (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 2b9da2062068ef25c5df97ef19b1502999ea78ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052528"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="18a79-102">Como: Carregar XML de um arquivo, cadeia de caracteres ou Stream (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a79-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="18a79-103">Você pode criar [literais XML](../../../../visual-basic/language-reference/xml-literals/index.md) e preenchê-los com o conteúdo de uma fonte externa, como um arquivo, uma cadeia de caracteres ou um fluxo usando vários métodos.</span><span class="sxs-lookup"><span data-stu-id="18a79-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="18a79-104">Esses métodos são mostrados nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="18a79-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="18a79-105">Para carregar XML de um arquivo</span><span class="sxs-lookup"><span data-stu-id="18a79-105">To load XML from a file</span></span>  
  
- <span data-ttu-id="18a79-106">Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto a partir de um arquivo, use o `Load` método.</span><span class="sxs-lookup"><span data-stu-id="18a79-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="18a79-107">Esse método pode usar um caminho de arquivo, fluxo de texto ou fluxo XML como entrada.</span><span class="sxs-lookup"><span data-stu-id="18a79-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="18a79-108">O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XDocument.Load%28System.String%29> método para preencher um <xref:System.Xml.Linq.XDocument> objeto com XML de um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="18a79-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="18a79-109">Para carregar XML de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="18a79-109">To load XML from a string</span></span>  
  
- <span data-ttu-id="18a79-110">Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto de cadeia de caracteres, você pode usar o `Parse` método.</span><span class="sxs-lookup"><span data-stu-id="18a79-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="18a79-111">O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> método para preencher um <xref:System.Xml.Linq.XDocument> objeto com XML de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="18a79-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="18a79-112">Para carregar XML de um fluxo</span><span class="sxs-lookup"><span data-stu-id="18a79-112">To load XML from a stream</span></span>  
  
- <span data-ttu-id="18a79-113">Para popular um literal XML como um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto de um fluxo, você pode usar o `Load` método ou o <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="18a79-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="18a79-114">O exemplo de código a seguir mostra o uso do <xref:System.Xml.Linq.XNode.ReadFrom%2A> método para preencher um <xref:System.Xml.Linq.XDocument> objeto com XML de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="18a79-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="18a79-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18a79-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="18a79-116">Literais XML</span><span class="sxs-lookup"><span data-stu-id="18a79-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="18a79-117">XML</span><span class="sxs-lookup"><span data-stu-id="18a79-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="18a79-118">Manipulando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18a79-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
