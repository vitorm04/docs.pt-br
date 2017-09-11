---
title: 'Como: transmitir fragmentos XML de um XmlReader (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="afe40-102">Como: transmitir fragmentos XML de um XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afe40-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="afe40-103">Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="afe40-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="afe40-104">Este tópico mostra como transmitir fragmentos usando um <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="afe40-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="afe40-105">Uma das maneiras mais eficazes para usar um <xref:System.Xml.XmlReader>ler <xref:System.Xml.Linq.XElement>objetos é escrever seu próprio método personalizado do eixo.</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="afe40-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="afe40-106">Um método do eixo normalmente retorna uma coleção, como <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="afe40-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="afe40-107">No método personalizado do eixo, depois de criar o fragmento XML chamando o <xref:System.Xml.Linq.XNode.ReadFrom%2A>método, retornar a coleção usando `yield return`.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="afe40-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="afe40-108">Isso fornece a semântica de execução adiada ao método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="afe40-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="afe40-109">Quando você cria uma árvore XML de uma <xref:System.Xml.XmlReader>objeto, o <xref:System.Xml.XmlReader>deve ser posicionado em um elemento.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="afe40-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="afe40-110">O <xref:System.Xml.Linq.XNode.ReadFrom%2A>método não retorna até que ele tenha lido a marca de fechamento do elemento.</xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="afe40-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="afe40-111">Se você quiser criar uma árvore parcial, você pode instanciar um <xref:System.Xml.XmlReader>, posicione o leitor no nó que você deseja converter em um <xref:System.Xml.Linq.XElement>de árvore e, em seguida, crie o <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="afe40-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="afe40-112">O tópico [como: transmitir fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como passar um documento mais complexo.</span><span class="sxs-lookup"><span data-stu-id="afe40-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="afe40-113">O tópico [como: realizar Streaming de transformação de documentos XML extensos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de como usar LINQ to XML para transformar documentos XML muito grandes, mantendo uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="afe40-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe40-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afe40-114">Example</span></span>  
 <span data-ttu-id="afe40-115">Este exemplo cria um método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="afe40-115">This example creates a custom axis method.</span></span> <span data-ttu-id="afe40-116">Você pode consultá-lo usando um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta.</span><span class="sxs-lookup"><span data-stu-id="afe40-116">You can query it by using a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query.</span></span> <span data-ttu-id="afe40-117">O método personalizado do eixo, `StreamRootChildDoc`, é um método que foi projetado especificamente para ler um documento que tem uma repetição `Child` elemento.</span><span class="sxs-lookup"><span data-stu-id="afe40-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
<span data-ttu-id="afe40-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="afe40-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="afe40-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="afe40-119">This example produces the following output:</span></span>  
  
<span data-ttu-id="afe40-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="afe40-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="afe40-121">Nesse exemplo, o documento de origem é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="afe40-121">In this example, the source document is very small.</span></span> <span data-ttu-id="afe40-122">No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="afe40-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe40-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afe40-123">See Also</span></span>  
 <span data-ttu-id="afe40-124">[Passo a passo: Implementando IEnumerable(Of T) no Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span><span class="sxs-lookup"><span data-stu-id="afe40-124">[Walkthrough: Implementing IEnumerable(Of T) in Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span></span>  
<span data-ttu-id="afe40-125"> [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="afe40-125"> [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span></span>
