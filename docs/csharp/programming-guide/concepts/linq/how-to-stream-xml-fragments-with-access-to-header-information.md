---
title: "Como transmitir fragmentos XML com acesso a informações de cabeçalho (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b7a83c9fc88b6e59cc1c8308d92464591896d312
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="5b37c-102">Como transmitir fragmentos XML com acesso a informações de cabeçalho (C#)</span><span class="sxs-lookup"><span data-stu-id="5b37c-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="5b37c-103">Às vezes você precisará ler arbitrariamente grandes arquivos XML, e escreve seu aplicativo para que os vestígio de memória do aplicativo seja previsível.</span><span class="sxs-lookup"><span data-stu-id="5b37c-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="5b37c-104">Se você tentar preencher uma árvore XML com um grande arquivo XML, seu uso de memória será proporcionalmente o tamanho do arquivo que é, excessivo.</span><span class="sxs-lookup"><span data-stu-id="5b37c-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="5b37c-105">Portanto, você deve usar uma técnica de streaming em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5b37c-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="5b37c-106">Uma opção é escrever seu aplicativo usando <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="5b37c-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="5b37c-107">No entanto, talvez você queira usar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para consultar a árvore XML.</span><span class="sxs-lookup"><span data-stu-id="5b37c-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="5b37c-108">Se esse for o caso, você pode escrever seu próprio método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="5b37c-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="5b37c-109">Para obter mais informações, consulte [Como gravar um método do eixo LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b37c-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="5b37c-110">Para escrever seu próprio método do eixo, você escreve um pequeno método que usa <xref:System.Xml.XmlReader> para ler nós até que atingiu um dos nós em que você está interessado.</span><span class="sxs-lookup"><span data-stu-id="5b37c-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="5b37c-111">O método chama em <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lê de <xref:System.Xml.XmlReader> e cria uma instância de um fragmento XML.</span><span class="sxs-lookup"><span data-stu-id="5b37c-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="5b37c-112">Resulta em cada fragmento com `yield return` o método que está enumerando o método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="5b37c-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="5b37c-113">Você pode escrever consultas LINQ no método personalizado do eixo.</span><span class="sxs-lookup"><span data-stu-id="5b37c-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="5b37c-114">As técnicas de streaming são melhor aplicadas em situações onde você precisa processar o documento de origem apenas uma vez e você pode processar os elementos na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="5b37c-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="5b37c-115">Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletam todos os dados, classificam e, em seguida, geram finalmente o primeiro item na sequência.</span><span class="sxs-lookup"><span data-stu-id="5b37c-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="5b37c-116">Observe que se você usar um operador de consulta que materialize sua origem antes de como o primeiro item, você não manterá pegada uma pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="5b37c-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b37c-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b37c-117">Example</span></span>  
 <span data-ttu-id="5b37c-118">Às vezes o problema é apenas um pouco mais interessante.</span><span class="sxs-lookup"><span data-stu-id="5b37c-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="5b37c-119">No documento XML a seguir, o consumidor do método personalizado do eixo também precisa saber o nome do cliente que cada item pertence.</span><span class="sxs-lookup"><span data-stu-id="5b37c-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="5b37c-120">A abordagem que este exemplo usa é inspecione também para essas informações de cabeçalho, salvar informações de cabeçalho, e então cria uma árvore XML pequena que contém informações de cabeçalho e o detalhe que você está enumerando.</span><span class="sxs-lookup"><span data-stu-id="5b37c-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="5b37c-121">O método do eixo resulta nessa nova árvore, pequena XML.</span><span class="sxs-lookup"><span data-stu-id="5b37c-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="5b37c-122">A consulta possui o acesso a informações de cabeçalho bem como para informações detalhadas.</span><span class="sxs-lookup"><span data-stu-id="5b37c-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="5b37c-123">Essa abordagem tem uma pegada pequena de memória.</span><span class="sxs-lookup"><span data-stu-id="5b37c-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="5b37c-124">Como cada fragmento XML de detalhe é rendido, nenhuma referência é mantido para o fragmento anterior, e está disponível para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5b37c-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="5b37c-125">Observe que essa técnica cria uma breve muitos objetos na heap.</span><span class="sxs-lookup"><span data-stu-id="5b37c-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="5b37c-126">O exemplo a seguir mostra como implementar e usar um método personalizado do eixo que passa fragmentos XML do arquivo especificado por um URI.</span><span class="sxs-lookup"><span data-stu-id="5b37c-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="5b37c-127">Esse eixo personalizado é escrito especificamente para que espera um documento que tem `Customer`, `Name`, e os elementos de `Item` , e que esses elementos serão organizados como no documento anterior de `Source.xml` .</span><span class="sxs-lookup"><span data-stu-id="5b37c-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="5b37c-128">É uma implementação simplista.</span><span class="sxs-lookup"><span data-stu-id="5b37c-128">It is a simplistic implementation.</span></span> <span data-ttu-id="5b37c-129">Uma implementação mais robusta seria preparada para analisar um documento válido.</span><span class="sxs-lookup"><span data-stu-id="5b37c-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="5b37c-130">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5b37c-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b37c-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b37c-131">See Also</span></span>  
 [<span data-ttu-id="5b37c-132">Programação LINQ to XML avançada (C#)</span><span class="sxs-lookup"><span data-stu-id="5b37c-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

