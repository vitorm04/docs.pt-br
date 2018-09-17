---
title: 'Como: Transformar um fragmento do nó'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb258b61664e1fdbf6604afdf69074c48cf5bda4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45597261"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="eb9ba-102">Como: Transformar um fragmento do nó</span><span class="sxs-lookup"><span data-stu-id="eb9ba-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="eb9ba-103">Quando você transforma os dados contidos em um objeto de <xref:System.Xml.XmlDocument> ou de <xref:System.Xml.XPath.XPathDocument> as transformações XSLT se aplicam a um documento no dataset.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="eb9ba-104">Ou seja se você passar em um nó que não seja o nó de diretório base, isso não impede que o processo de transformação acessar todos os nós do documento carregado.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="eb9ba-105">Para transformar um fragmento de nó, você deve criar um objeto separado que contém apenas o fragmento de nó, e passa esse objeto para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="eb9ba-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="eb9ba-106">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="eb9ba-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="eb9ba-107">Para transformar um fragmento do nó</span><span class="sxs-lookup"><span data-stu-id="eb9ba-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="eb9ba-108">Crie um objeto que contém o documento de origem.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="eb9ba-109">Localize o nó de fragmento que você deseja que a transformação.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="eb9ba-110">Crie o objeto separado com apenas o fragmento de nó.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="eb9ba-111">Passe o fragmento do nó para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="eb9ba-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb9ba-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb9ba-112">Example</span></span>  
 <span data-ttu-id="eb9ba-113">O exemplo transforma um fragmento e saída do nó os resultados no console.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="eb9ba-114">Entrada</span><span class="sxs-lookup"><span data-stu-id="eb9ba-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="eb9ba-115">books.xml</span><span class="sxs-lookup"><span data-stu-id="eb9ba-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="eb9ba-116">single.xsl</span><span class="sxs-lookup"><span data-stu-id="eb9ba-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="eb9ba-117">Saída</span><span class="sxs-lookup"><span data-stu-id="eb9ba-117">Output</span></span>  
 <span data-ttu-id="eb9ba-118">O título de livro é o homem de confiança.</span><span class="sxs-lookup"><span data-stu-id="eb9ba-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9ba-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb9ba-119">See also</span></span>

- [<span data-ttu-id="eb9ba-120">Usando a classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="eb9ba-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
