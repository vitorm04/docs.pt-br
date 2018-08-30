---
title: Estendendo os DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58f32dcb76246bed1030f3d0a45db2541f381877
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908261"
---
# <a name="extending-the-dom"></a><span data-ttu-id="f627e-102">Estendendo os DOM</span><span class="sxs-lookup"><span data-stu-id="f627e-102">Extending the DOM</span></span>

<span data-ttu-id="f627e-103">O Microsoft .NET Framework inclui um conjunto básico de classes que fornece uma implementação de DOM (XML Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="f627e-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="f627e-104"><xref:System.Xml.XmlNode>, e suas classes derivadas, fornecem métodos e propriedades que permitem que você navega, consulte, e o conteúdo e a estrutura de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f627e-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="f627e-105">Quando o conteúdo XML é carregado na memória usando os DOM, os nós criados contêm informações como o nome de nó, tipo de nó, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f627e-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="f627e-106">Pode haver ocasiões as onde você requer informações específicas do nó que classes base não fornecem.</span><span class="sxs-lookup"><span data-stu-id="f627e-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="f627e-107">Por exemplo, você pode desejar consultar o número da linha e posição do nó.</span><span class="sxs-lookup"><span data-stu-id="f627e-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="f627e-108">Nesse caso, você pode derivar novas classes de classes DOM existentes e adicionar funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="f627e-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="f627e-109">Há duas diretrizes gerais para derivar novas classes:</span><span class="sxs-lookup"><span data-stu-id="f627e-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="f627e-110">É recomendável que você nunca deriva de classe de <xref:System.Xml.XmlNode> .</span><span class="sxs-lookup"><span data-stu-id="f627e-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="f627e-111">Em vez disso, é recomendável que você derivado classes de classe correspondente ao tipo de nó que você está interessado.</span><span class="sxs-lookup"><span data-stu-id="f627e-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="f627e-112">Por exemplo, se você quiser retornar informações adicionais em nós de atributo, você pode derivar da classe de <xref:System.Xml.XmlAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f627e-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="f627e-113">A exceção dos métodos de criação de nó, é recomendável que substituir uma função, você sempre deve chamar a versão de base de função e adicionar qualquer processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="f627e-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="f627e-114">Criando suas próprias instâncias do nó</span><span class="sxs-lookup"><span data-stu-id="f627e-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="f627e-115">A classe de <xref:System.Xml.XmlDocument> contém métodos de criação de nó.</span><span class="sxs-lookup"><span data-stu-id="f627e-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="f627e-116">Quando um arquivo XML é carregado, esses métodos são chamados para criar os nós.</span><span class="sxs-lookup"><span data-stu-id="f627e-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="f627e-117">Você pode substituir esses métodos de modo que as instâncias do nó são criados quando um documento é carregado.</span><span class="sxs-lookup"><span data-stu-id="f627e-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="f627e-118">Por exemplo, se você estendeu a classe de <xref:System.Xml.XmlElement> , você herdaria a classe de <xref:System.Xml.XmlDocument> e poderia substituir o método de <xref:System.Xml.XmlDocument.CreateElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="f627e-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="f627e-119">O exemplo a seguir mostra como substituir o método de <xref:System.Xml.XmlDocument.CreateElement%2A> retornar sua implementação da classe de <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="f627e-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument 
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI) 
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="f627e-120">Estendendo uma classe</span><span class="sxs-lookup"><span data-stu-id="f627e-120">Extending a Class</span></span>

<span data-ttu-id="f627e-121">Para estender uma classe derivada, a classe de uma das classes DOM existentes.</span><span class="sxs-lookup"><span data-stu-id="f627e-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="f627e-122">Você pode então substitua alguns dos métodos ou propriedades virtuais na classe base, ou adicione seus próprios.</span><span class="sxs-lookup"><span data-stu-id="f627e-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="f627e-123">No exemplo a seguir, uma nova classe é criada, que implementa a classe de <xref:System.Xml.XmlElement> e a interface de <xref:System.Xml.IXmlLineInfo> .</span><span class="sxs-lookup"><span data-stu-id="f627e-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="f627e-124">Os métodos e propriedades adicionais são definidos que permite que os usuários coleta a linha informações.</span><span class="sxs-lookup"><span data-stu-id="f627e-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="f627e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f627e-125">Example</span></span>

<span data-ttu-id="f627e-126">O exemplo a seguir conta o número de elementos em um documento XML:</span><span class="sxs-lookup"><span data-stu-id="f627e-126">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="f627e-127">Entrada</span><span class="sxs-lookup"><span data-stu-id="f627e-127">Input</span></span>

<span data-ttu-id="f627e-128">book.xml</span><span class="sxs-lookup"><span data-stu-id="f627e-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="f627e-129">Saída</span><span class="sxs-lookup"><span data-stu-id="f627e-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="f627e-130">Manipulador de eventos do nó</span><span class="sxs-lookup"><span data-stu-id="f627e-130">Node Event Handler</span></span>

<span data-ttu-id="f627e-131">A implementação do .NET Framework DOM também inclui um sistema de eventos que permite que você receber e manipular eventos quando os nós em um documento XML são alterados.</span><span class="sxs-lookup"><span data-stu-id="f627e-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="f627e-132">Usando as classes de <xref:System.Xml.XmlNodeChangedEventHandler> e de <xref:System.Xml.XmlNodeChangedEventArgs> , você pode capturar `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, e eventos de `NodeRemoving` .</span><span class="sxs-lookup"><span data-stu-id="f627e-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="f627e-133">Os trabalhos de processo de manipulação de eventos exatamente em classes derivadas como em DOM original de classe.</span><span class="sxs-lookup"><span data-stu-id="f627e-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="f627e-134">Para saber mais sobre a manipulação de eventos do nó, confira [Eventos](../../../../docs/standard/events/index.md) e <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f627e-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="f627e-135">Atributos padrões e o método de CreateElement</span><span class="sxs-lookup"><span data-stu-id="f627e-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="f627e-136">Se você está substituindo o método de <xref:System.Xml.XmlDocument.CreateElement%2A> em uma classe derivada, os atributos padrão não são adicionados quando você está criando novos elementos ao editar o documento.</span><span class="sxs-lookup"><span data-stu-id="f627e-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="f627e-137">Este é apenas um problema ao editar.</span><span class="sxs-lookup"><span data-stu-id="f627e-137">This is only an issue while editing.</span></span> <span data-ttu-id="f627e-138">Porque o método de <xref:System.Xml.XmlDocument.CreateElement%2A> é responsável para adicionar atributos padrão para <xref:System.Xml.XmlDocument>, você deve codificar essa funcionalidade no método de <xref:System.Xml.XmlDocument.CreateElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="f627e-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="f627e-139">Se você está carregando <xref:System.Xml.XmlDocument> que inclui atributos padrão, serão tratados corretamente.</span><span class="sxs-lookup"><span data-stu-id="f627e-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="f627e-140">Para saber mais sobre os atributos padrão, confira [Criando novos atributos para os elementos em DOM](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="f627e-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f627e-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f627e-141">See Also</span></span>

[<span data-ttu-id="f627e-142">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="f627e-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
