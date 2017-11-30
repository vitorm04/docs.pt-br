---
title: "Criação de documentos XML"
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
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="3e978-102">Criação de documentos XML</span><span class="sxs-lookup"><span data-stu-id="3e978-102">XML Document Creation</span></span>
<span data-ttu-id="3e978-103">Existem duas maneiras de criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e978-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="3e978-104">É uma maneira criar um **XmlDocument** sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3e978-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="3e978-105">A outra maneira é criar um **XmlDocument** e passá-lo um XmlNameTable como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3e978-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="3e978-106">O exemplo a seguir mostra como criar um novo e vazio **XmlDocument** usando sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3e978-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="3e978-107">Quando um documento é criado, você pode carregá-lo com dados de uma cadeia de caracteres, transmitir, URL, o leitor de texto, ou um **XmlReader** derivado da classe usando o **carregar** método.</span><span class="sxs-lookup"><span data-stu-id="3e978-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="3e978-108">Também há outro método de carga, o **LoadXML** método, que lê o XML de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3e978-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="3e978-109">Para obter mais informações sobre os vários **carga** métodos, consulte [ler um documento XML no DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="3e978-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="3e978-110">Há uma classe chamada a **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="3e978-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="3e978-111">Essa classe é uma tabela de objetos atomizados de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3e978-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="3e978-112">Essa tabela fornece uma forma eficiente para que o analisador XML use o mesmo objeto de cadeia de caracteres para todos os nomes repetidos de elementos e de atributos em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e978-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="3e978-113">Um **XmlNameTable** é criado automaticamente quando um documento é criado como mostrado acima e é carregado com nomes de atributo e elemento quando o documento é carregado.</span><span class="sxs-lookup"><span data-stu-id="3e978-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="3e978-114">Se você já tiver um documento com uma tabela de nome, e esses nomes pode ser útil em outro documento, você pode criar um novo documento usando o **carga** método que utiliza um **XmlNameTable** como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3e978-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="3e978-115">Quando o documento é criado com esse método, ele usa existente **XmlNameTable** todos os atributos e elementos já carregados do outro documento.</span><span class="sxs-lookup"><span data-stu-id="3e978-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="3e978-116">Ela pode ser usada para comparar nomes de elementos e de atributos de forma mais eficaz.</span><span class="sxs-lookup"><span data-stu-id="3e978-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="3e978-117">Para obter mais informações sobre o **XmlNameTable**, consulte [comparação de objeto usando XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="3e978-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="3e978-118">Para referência, consulte <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="3e978-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e978-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e978-119">See Also</span></span>  
 [<span data-ttu-id="3e978-120">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="3e978-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
