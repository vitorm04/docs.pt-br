---
title: Serializar com uma declaração XML-LINQ to XML
description: Você pode controlar se uma declaração XML é gerada ao serializar XML em C# ou Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 8d25d199b149ac6aeb2aa37dc248523e79847220
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551864"
---
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a><span data-ttu-id="ca76a-103">Serializar com uma declaração XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ca76a-103">Serialize with an XML declaration (LINQ to XML)</span></span>

<span data-ttu-id="ca76a-104">Este artigo descreve como controlar se uma declaração XML é gerada quando você serializa o XML em C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ca76a-104">This article describes how to control whether an XML declaration is generated when you serialize XML in C# or Visual Basic.</span></span>

<span data-ttu-id="ca76a-105">Serializar para um <xref:System.IO.File> ou <xref:System.IO.TextWriter> usando o método <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou o método <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="ca76a-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="ca76a-106">Quando você serializa para um <xref:System.Xml.XmlWriter> , as configurações do gravador (especificadas em um <xref:System.Xml.XmlWriterSettings> objeto) determinam se uma declaração XML é gerada.</span><span class="sxs-lookup"><span data-stu-id="ca76a-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated.</span></span>

<span data-ttu-id="ca76a-107">Se você estiver serializando para uma cadeia de caracteres usando o `ToString` método, o XML resultante não incluirá uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="ca76a-107">If you're serializing to a string using the `ToString` method, the resulting XML won't include an XML declaration.</span></span>

## <a name="example-serialize-with-an-xml-declaration"></a><span data-ttu-id="ca76a-108">Exemplo: serializar com uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="ca76a-108">Example: Serialize with an XML declaration</span></span>

<span data-ttu-id="ca76a-109">O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e imprime o arquivo no console:</span><span class="sxs-lookup"><span data-stu-id="ca76a-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child", "child content")
);
root.Save("Root.xml");
string str = File.ReadAllText("Root.xml");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root>
                           <Child>child content</Child>
                       </Root>
root.Save("Root.xml")
Dim str As String = File.ReadAllText("Root.xml")
Console.WriteLine(str)
```

<span data-ttu-id="ca76a-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="ca76a-110">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a><span data-ttu-id="ca76a-111">Exemplo: serializar sem uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="ca76a-111">Example: Serialize without an XML declaration</span></span>

<span data-ttu-id="ca76a-112">O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement> em um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="ca76a-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>

```csharp
StringBuilder sb = new StringBuilder();
XmlWriterSettings xws = new XmlWriterSettings();
xws.OmitXmlDeclaration = true;

using (XmlWriter xw = XmlWriter.Create(sb, xws)) {
    XElement root = new XElement("Root",
        new XElement("Child", "child content")
    );
    root.Save(xw);
}
Console.WriteLine(sb.ToString());
```

```vb
Dim sb As StringBuilder = New StringBuilder()
Dim xws As XmlWriterSettings = New XmlWriterSettings()
xws.OmitXmlDeclaration = True

Using xw As XmlWriter = XmlWriter.Create(sb, xws)
    Dim root = <Root>
                   <Child>child content</Child>
               </Root>
    root.Save(xw)
End Using
Console.WriteLine(sb.ToString())
```

<span data-ttu-id="ca76a-113">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="ca76a-113">This example produces the following output:</span></span>

```xml
<Root><Child>child content</Child></Root>
```
