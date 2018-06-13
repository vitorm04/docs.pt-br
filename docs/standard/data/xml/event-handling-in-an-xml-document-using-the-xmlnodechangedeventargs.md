---
title: Tratamento de eventos em um documento XML usando o XmlNodeChangedEventArgs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00ed0437f51650cd335d528632f9f0cc14af6422
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569727"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="79f35-102">Tratamento de eventos em um documento XML usando o XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="79f35-102">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>
<span data-ttu-id="79f35-103">**XmlNodeChangedEventArgs** encapsula os argumentos passados para manipuladores de eventos registrados no objeto **XmlDocument** para manipular eventos.</span><span class="sxs-lookup"><span data-stu-id="79f35-103">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="79f35-104">Os eventos e uma descrição de quando são acionados dados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="79f35-104">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="79f35-105">evento</span><span class="sxs-lookup"><span data-stu-id="79f35-105">Event</span></span>|<span data-ttu-id="79f35-106">Acionado</span><span class="sxs-lookup"><span data-stu-id="79f35-106">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="79f35-107">Quando um nó que pertence ao documento atual está prestes a ser inserido em outro nó.</span><span class="sxs-lookup"><span data-stu-id="79f35-107">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="79f35-108">Quando um nó que pertence ao documento atual está inserido em outro nó.</span><span class="sxs-lookup"><span data-stu-id="79f35-108">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="79f35-109">Quando um nó que pertence ao documento está prestes a ser removido do documento.</span><span class="sxs-lookup"><span data-stu-id="79f35-109">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="79f35-110">Quando um nó que pertence a este documento é removido do seu pai.</span><span class="sxs-lookup"><span data-stu-id="79f35-110">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="79f35-111">Quando o valor de um nó esteja prestes a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="79f35-111">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="79f35-112">Quando o valor de um nó é alterado.</span><span class="sxs-lookup"><span data-stu-id="79f35-112">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="79f35-113">Se o uso de memória de **XmlDataDocument** for completamente otimizado para utilizar o armazenamento de **DataSet**, **XmlDataDocument** poderá não disparar nenhum dos eventos listados acima quando alterações forem feitas no **conjunto de dados** subjacente.</span><span class="sxs-lookup"><span data-stu-id="79f35-113">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="79f35-114">Se precisar esses eventos, você deverá atravessar o **XmlDocument** inteiro uma vez para tornar o uso de memória não totalmente otimizado.</span><span class="sxs-lookup"><span data-stu-id="79f35-114">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="79f35-115">O exemplo de código a seguir mostra como definir um manipulador de eventos e como adicionar o manipulador de eventos a um evento.</span><span class="sxs-lookup"><span data-stu-id="79f35-115">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="79f35-116">Algumas operações de (DOM) o modelo de objeto de documento XML são as operações compostas que podem resultar em vários eventos que estão sendo acionados.</span><span class="sxs-lookup"><span data-stu-id="79f35-116">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="79f35-117">Por exemplo, **AppendChild** também pode ter que remover o nó que está sendo acrescentado de seu pai anterior.</span><span class="sxs-lookup"><span data-stu-id="79f35-117">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="79f35-118">Nesse caso, um evento **NodeRemoved** será disparado primeiro, seguido de um evento **NodeInserted**.</span><span class="sxs-lookup"><span data-stu-id="79f35-118">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="79f35-119">Operações como definir **InnerXml** podem resultar em vários eventos.</span><span class="sxs-lookup"><span data-stu-id="79f35-119">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="79f35-120">O exemplo de código a seguir mostra a criação do manipulador de eventos e a manipulação do evento **NodeInserted**.</span><span class="sxs-lookup"><span data-stu-id="79f35-120">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 <span data-ttu-id="79f35-121">Para obter mais informações, consulte <xref:System.Xml.XmlNodeChangedEventArgs> e <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="79f35-121">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f35-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79f35-122">See Also</span></span>  
 [<span data-ttu-id="79f35-123">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="79f35-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
