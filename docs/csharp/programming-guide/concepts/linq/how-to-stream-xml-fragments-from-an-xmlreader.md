---
title: Como transmitir fragmentos XML de um XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714649"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="45348-102">Como transmitir fragmentos XML de um XmlReader (C#)</span><span class="sxs-lookup"><span data-stu-id="45348-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="45348-103">Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória.</span><span class="sxs-lookup"><span data-stu-id="45348-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="45348-104">Este tópico mostra como passar informações usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="45348-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="45348-105">Um dos modos de efetivas usar <xref:System.Xml.XmlReader> para ler objetos de <xref:System.Xml.Linq.XElement> é escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="45348-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="45348-106">Um método do eixo normalmente retorna uma coleção como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="45348-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="45348-107">No método personalizado do eixo, depois de criar o fragmento XML chamando o método <xref:System.Xml.Linq.XNode.ReadFrom%2A> , retornar a coleção usando `yield return`.</span><span class="sxs-lookup"><span data-stu-id="45348-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="45348-108">Isso fornece a semântica de execução adiada ao método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="45348-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="45348-109">Quando você cria uma árvore XML de um objeto de <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReader> deve ser posicionado em um elemento.</span><span class="sxs-lookup"><span data-stu-id="45348-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="45348-110">O método de <xref:System.Xml.Linq.XNode.ReadFrom%2A> não retorna até que lê a marca do elemento.</span><span class="sxs-lookup"><span data-stu-id="45348-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="45348-111">Se você desejar criar uma árvore parcial, você pode criar uma instância <xref:System.Xml.XmlReader>, posiciona o leitor no nó que você deseja converter a <xref:System.Xml.Linq.XElement> uma árvore e em seguida, cria o objeto de <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="45348-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="45348-112">O tópico [Como transmitir fragmentos XML com acesso a informações de cabeçalho (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo sobre como transmitir um documento mais complexo.</span><span class="sxs-lookup"><span data-stu-id="45348-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="45348-113">O tópico [Como realizar a transformação de streaming de grandes documentos XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de uso de LINQ para XML para transformar documentos XML extremamente grandes, mantendo uma pequena pegada de memória.</span><span class="sxs-lookup"><span data-stu-id="45348-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45348-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45348-114">Example</span></span>  
 <span data-ttu-id="45348-115">Este exemplo cria um método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="45348-115">This example creates a custom axis method.</span></span> <span data-ttu-id="45348-116">Você pode consultar usando uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="45348-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="45348-117">O método de eixo personalizado `StreamRootChildDoc` é um método que foi projetado especificamente para ler um documento que tenha um elemento `Child` de repetição.</span><span class="sxs-lookup"><span data-stu-id="45348-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="45348-118">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="45348-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="45348-119">Nesse exemplo, o documento de origem é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="45348-119">In this example, the source document is very small.</span></span> <span data-ttu-id="45348-120">No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="45348-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
