---
title: Mapeando a hierarquia do objeto para dados XML
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
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2191cb15a85e9b16ff0a21084668e80d3c197bfa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="934bf-102">Mapeando a hierarquia do objeto para dados XML</span><span class="sxs-lookup"><span data-stu-id="934bf-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="934bf-103">Quando um documento XML está na memória, a representação conceitual é uma árvore.</span><span class="sxs-lookup"><span data-stu-id="934bf-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="934bf-104">Para programar, você tem uma hierarquia de objeto para acessar os nós da árvore.</span><span class="sxs-lookup"><span data-stu-id="934bf-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="934bf-105">O exemplo a seguir mostra como o conteúdo XML torna-se nós.</span><span class="sxs-lookup"><span data-stu-id="934bf-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="934bf-106">Como o XML é lido no DOM (Document Object Model) XML, as partes são traduzidas em nós e esses nós mantêm metadados adicionais sobre si mesmos, como seu tipo de nó e valores.</span><span class="sxs-lookup"><span data-stu-id="934bf-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="934bf-107">O tipo de nó é seu objeto e é o que determina quais ações podem ser executadas e quais propriedades podem ser definidas ou recuperadas.</span><span class="sxs-lookup"><span data-stu-id="934bf-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="934bf-108">Se você tiver o XML simples a seguir:</span><span class="sxs-lookup"><span data-stu-id="934bf-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="934bf-109">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="934bf-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="934bf-110">A entrada é representada na memória como a árvore de nó a seguir com a propriedade de tipo de nó atribuída:</span><span class="sxs-lookup"><span data-stu-id="934bf-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="934bf-111">![árvore do nó de exemplo](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="934bf-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="934bf-112">Representação da árvore do nó do livro e do título</span><span class="sxs-lookup"><span data-stu-id="934bf-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="934bf-113">O elemento `book` torna-se um objeto **XmlElement**, o elemento a seguir, `title`, também se torna **XmlElement**, enquanto o conteúdo do elemento se torna um objeto **XmlText**.</span><span class="sxs-lookup"><span data-stu-id="934bf-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="934bf-114">Ao analisar os métodos e as propriedades **XmlElement**, eles são diferentes dos métodos e das propriedades disponíveis em um objeto **XmlText**.</span><span class="sxs-lookup"><span data-stu-id="934bf-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="934bf-115">Portanto, saber qual tipo de nó a marcação XML se torna é vital, porque o tipo de nó determina as ações que podem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="934bf-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="934bf-116">O exemplo a seguir lê dados XML e remove o texto diferente, dependendo do tipo de nó.</span><span class="sxs-lookup"><span data-stu-id="934bf-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="934bf-117">Usando o seguinte arquivo de dados XML como entrada, **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="934bf-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="934bf-118">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="934bf-118">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="934bf-119">O exemplo de código a seguir lê o arquivo **items.xml** e exibe informações para cada tipo de nó.</span><span class="sxs-lookup"><span data-stu-id="934bf-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="934bf-120">A saída do exemplo revela o mapeamento dos dados para os tipos de nó.</span><span class="sxs-lookup"><span data-stu-id="934bf-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="934bf-121">**Saída**</span><span class="sxs-lookup"><span data-stu-id="934bf-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="934bf-122">Utilizando a entrada uma linha de cada vez e usando a saída gerada do código, você poderá usar a tabela a seguir para analisar qual teste do nó gerou as linhas de saída, entendendo, portanto, quais dados XML se transformaram em qual tipo de nó.</span><span class="sxs-lookup"><span data-stu-id="934bf-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="934bf-123">Entrada</span><span class="sxs-lookup"><span data-stu-id="934bf-123">Input</span></span>|<span data-ttu-id="934bf-124">Saída</span><span class="sxs-lookup"><span data-stu-id="934bf-124">Output</span></span>|<span data-ttu-id="934bf-125">Teste de tipo de nó</span><span class="sxs-lookup"><span data-stu-id="934bf-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="934bf-126">\<?xml version="1.0"?></span><span class="sxs-lookup"><span data-stu-id="934bf-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="934bf-127">\<?xml version='1.0'?></span><span class="sxs-lookup"><span data-stu-id="934bf-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="934bf-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="934bf-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="934bf-129">\<!--Este é um documento XML de exemplo --></span><span class="sxs-lookup"><span data-stu-id="934bf-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="934bf-130">\<!--Este é um documento XML de exemplo --></span><span class="sxs-lookup"><span data-stu-id="934bf-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="934bf-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="934bf-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="934bf-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span><span class="sxs-lookup"><span data-stu-id="934bf-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="934bf-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="934bf-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="934bf-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="934bf-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="934bf-135">\<Items></span><span class="sxs-lookup"><span data-stu-id="934bf-135">\<Items></span></span>|<span data-ttu-id="934bf-136">\<Items></span><span class="sxs-lookup"><span data-stu-id="934bf-136">\<Items></span></span>|<span data-ttu-id="934bf-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-138">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-138">\<Item></span></span>|<span data-ttu-id="934bf-139">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-139">\<Item></span></span>|<span data-ttu-id="934bf-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-141">Teste com uma entidade: &number;</span><span class="sxs-lookup"><span data-stu-id="934bf-141">Test with an entity: &number;</span></span>|<span data-ttu-id="934bf-142">Teste com uma entidade: 123</span><span class="sxs-lookup"><span data-stu-id="934bf-142">Test with an entity: 123</span></span>|<span data-ttu-id="934bf-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-144">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-144">\</Item></span></span>|<span data-ttu-id="934bf-145">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-145">\</Item></span></span>|<span data-ttu-id="934bf-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="934bf-147">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-147">\<Item></span></span>|<span data-ttu-id="934bf-148">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-148">\<Item></span></span>|<span data-ttu-id="934bf-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-150">teste com um elemento filho</span><span class="sxs-lookup"><span data-stu-id="934bf-150">test with a child element</span></span>|<span data-ttu-id="934bf-151">teste com um elemento filho</span><span class="sxs-lookup"><span data-stu-id="934bf-151">test with a child element</span></span>|<span data-ttu-id="934bf-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-153">\<more></span><span class="sxs-lookup"><span data-stu-id="934bf-153">\<more></span></span>|<span data-ttu-id="934bf-154">\<more></span><span class="sxs-lookup"><span data-stu-id="934bf-154">\<more></span></span>|<span data-ttu-id="934bf-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-156">material</span><span class="sxs-lookup"><span data-stu-id="934bf-156">stuff</span></span>|<span data-ttu-id="934bf-157">material</span><span class="sxs-lookup"><span data-stu-id="934bf-157">stuff</span></span>|<span data-ttu-id="934bf-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-159">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-159">\</Item></span></span>|<span data-ttu-id="934bf-160">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-160">\</Item></span></span>|<span data-ttu-id="934bf-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="934bf-162">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-162">\<Item></span></span>|<span data-ttu-id="934bf-163">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-163">\<Item></span></span>|<span data-ttu-id="934bf-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-165">teste com uma seção CDATA</span><span class="sxs-lookup"><span data-stu-id="934bf-165">test with a CDATA section</span></span>|<span data-ttu-id="934bf-166">teste com uma seção CDATA</span><span class="sxs-lookup"><span data-stu-id="934bf-166">test with a CDATA section</span></span>|<span data-ttu-id="934bf-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="934bf-168"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="934bf-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="934bf-169"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="934bf-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="934bf-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="934bf-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="934bf-171">def</span><span class="sxs-lookup"><span data-stu-id="934bf-171">def</span></span>|<span data-ttu-id="934bf-172">def</span><span class="sxs-lookup"><span data-stu-id="934bf-172">def</span></span>|<span data-ttu-id="934bf-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-174">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-174">\</Item></span></span>|<span data-ttu-id="934bf-175">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-175">\</Item></span></span>|<span data-ttu-id="934bf-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="934bf-177">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-177">\<Item></span></span>|<span data-ttu-id="934bf-178">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-178">\<Item></span></span>|<span data-ttu-id="934bf-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-180">Teste com uma entidade de caracteres: &\#65;</span><span class="sxs-lookup"><span data-stu-id="934bf-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="934bf-181">Teste com uma entidade de caracteres: A</span><span class="sxs-lookup"><span data-stu-id="934bf-181">Test with a char entity: A</span></span>|<span data-ttu-id="934bf-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-183">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-183">\</Item></span></span>|<span data-ttu-id="934bf-184">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-184">\</Item></span></span>|<span data-ttu-id="934bf-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="934bf-186">\<!-- Quatorze caracteres nesse elemento. --></span><span class="sxs-lookup"><span data-stu-id="934bf-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="934bf-187">\<--Quatorze caracteres nesse elemento. --></span><span class="sxs-lookup"><span data-stu-id="934bf-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="934bf-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="934bf-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="934bf-189">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-189">\<Item></span></span>|<span data-ttu-id="934bf-190">\<Item></span><span class="sxs-lookup"><span data-stu-id="934bf-190">\<Item></span></span>|<span data-ttu-id="934bf-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="934bf-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="934bf-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="934bf-192">1234567890ABCD</span></span>|<span data-ttu-id="934bf-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="934bf-193">1234567890ABCD</span></span>|<span data-ttu-id="934bf-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="934bf-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="934bf-195">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-195">\</Item></span></span>|<span data-ttu-id="934bf-196">\</Item></span><span class="sxs-lookup"><span data-stu-id="934bf-196">\</Item></span></span>|<span data-ttu-id="934bf-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="934bf-198">\</Items></span><span class="sxs-lookup"><span data-stu-id="934bf-198">\</Items></span></span>|<span data-ttu-id="934bf-199">\</Items></span><span class="sxs-lookup"><span data-stu-id="934bf-199">\</Items></span></span>|<span data-ttu-id="934bf-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="934bf-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="934bf-201">Você deve saber qual tipo de nó é atribuído, porque o tipo de nó controla quais tipos de ações são válidos e qual tipo de propriedades você pode definir e recuperar.</span><span class="sxs-lookup"><span data-stu-id="934bf-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="934bf-202">A criação do nó para o espaço em branco é controlada quando os dados são carregados no DOM pelo sinalizador **PreserveWhitespace**.</span><span class="sxs-lookup"><span data-stu-id="934bf-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="934bf-203">Para saber mais, confira [Espaço em branco e tratamento de espaço em branco significativo ao carregar o DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="934bf-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="934bf-204">Para adicionar novos nós para o DOM, consulte [Inserir nós em um documento XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="934bf-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="934bf-205">Para remover os nós do DOM, consulte [Remover nós, conteúdo e valores de um documento XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="934bf-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="934bf-206">Para modificar o conteúdo de nós no DOM, consulte [Modificar nós, conteúdo e valores em um documento XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="934bf-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934bf-207">Consulte também</span><span class="sxs-lookup"><span data-stu-id="934bf-207">See Also</span></span>  
 [<span data-ttu-id="934bf-208">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="934bf-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
