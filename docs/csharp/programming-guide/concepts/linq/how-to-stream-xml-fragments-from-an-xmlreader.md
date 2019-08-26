---
title: 'Como: Transmitir fragmentos XML de um XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: c27c2165af95b8b781564e14efc0668f596e3057
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592400"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="a2611-102">Como: Transmitir fragmentos XML de um XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="a2611-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="a2611-103">Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="a2611-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="a2611-104">Este tópico mostra como passar informações usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="a2611-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="a2611-105">Um dos modos de efetivas usar <xref:System.Xml.XmlReader> para ler objetos de <xref:System.Xml.Linq.XElement> é escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="a2611-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="a2611-106">Um método do eixo normalmente retorna uma coleção como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a2611-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="a2611-107">No método personalizado do eixo, depois de criar o fragmento XML chamando o método <xref:System.Xml.Linq.XNode.ReadFrom%2A> , retornar a coleção usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="a2611-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="a2611-108">Isso fornece a semântica de execução adiada ao método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="a2611-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="a2611-109">Quando você cria uma árvore XML de um objeto de <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReader> deve ser posicionado em um elemento.</span><span class="sxs-lookup"><span data-stu-id="a2611-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="a2611-110">O método de <xref:System.Xml.Linq.XNode.ReadFrom%2A> não retorna até que lê a marca do elemento.</span><span class="sxs-lookup"><span data-stu-id="a2611-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="a2611-111">Se você desejar criar uma árvore parcial, você pode criar uma instância <xref:System.Xml.XmlReader>, posiciona o leitor no nó que você deseja converter a <xref:System.Xml.Linq.XElement> uma árvore e em seguida, cria o objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="a2611-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="a2611-112">O tópico [Como: Transmitir fragmentos XML com acesso a informações de cabeçalho (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como transmitir um documento mais complexo.</span><span class="sxs-lookup"><span data-stu-id="a2611-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="a2611-113">O tópico [Como: Executar a transformação de streaming de documentos XML grandes (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de como usar o LINQ to XML para transformar documentos XML muito grandes, mantendo um volume de memória pequeno.</span><span class="sxs-lookup"><span data-stu-id="a2611-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2611-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2611-114">Example</span></span>  
 <span data-ttu-id="a2611-115">Este exemplo cria um método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="a2611-115">This example creates a custom axis method.</span></span> <span data-ttu-id="a2611-116">Você pode consultá-lo usando uma consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2611-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="a2611-117">O método de eixo personalizado `StreamRootChildDoc` é um método que foi projetado especificamente para ler um documento que tenha um elemento `Child` de repetição.</span><span class="sxs-lookup"><span data-stu-id="a2611-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="a2611-118">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a2611-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="a2611-119">Nesse exemplo, o documento de origem é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="a2611-119">In this example, the source document is very small.</span></span> <span data-ttu-id="a2611-120">No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="a2611-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  