---
title: "Comparação de objeto usando XmlNameTable"
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
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f6c65581437bfb22cf771d66716b3dbb62dbafae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="2aceb-102">Comparação de objeto usando XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="2aceb-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="2aceb-103">**XmlDocuments**, quando criado, possui uma tabela de nome especificamente projetada para esse documento.</span><span class="sxs-lookup"><span data-stu-id="2aceb-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="2aceb-104">Quando XML é carregado no documento, ou novos elementos ou atributos são criados, os nomes de atributo e de elemento são colocados em **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="2aceb-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="2aceb-105">Você também pode criar **XmlDocument** usando **NameTable** existente de outro documento.</span><span class="sxs-lookup"><span data-stu-id="2aceb-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="2aceb-106">Quando **XmlDocuments** é criado com o constructo que aceita um parâmetro **XmlNameTable**, o documento tem acesso aos nomes de nó, namespaces e prefixos já armazenados em **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="2aceb-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="2aceb-107">Independentemente de como a tabela de nome é carregada com nomes, uma vez que os nomes são armazenados na tabela, os nomes podem ser comparados rapidamente usando a comparação de objeto em vez de comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2aceb-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="2aceb-108">As cadeias de caracteres também podem ser adicionadas à tabela de nome usando o <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="2aceb-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="2aceb-109">O exemplo de código a seguir mostra uma tabela de nome que está sendo criada e a cadeia de caracteres **MyString** sendo adicionada à tabela.</span><span class="sxs-lookup"><span data-stu-id="2aceb-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="2aceb-110">Em seguida, um **XmlDocument** é criado usando a tabela e os nomes de elementos e atributos de **Myfile.xml** serão adicionados à tabela de nome existente.</span><span class="sxs-lookup"><span data-stu-id="2aceb-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="2aceb-111">O exemplo de código a seguir mostra a criação de um documento, dois novos elementos que estão sendo adicionados ao documento, que também os adiciona à tabela do nome do documento, e a comparação de objeto em nomes.</span><span class="sxs-lookup"><span data-stu-id="2aceb-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="2aceb-112">A situação acima de uma tabela de nome transmitida entre dois documentos é típico quando o mesmo tipo de documento está sendo processado repetidamente, como documentos de ordem em um site de comércio eletrônico, que atendem a um esquema de linguagem de definição de esquema XML (XSD) ou Document type definition (DTD) e as mesmas cadeias de caracteres são repetidas.</span><span class="sxs-lookup"><span data-stu-id="2aceb-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="2aceb-113">Usar a mesma tabela de nome fornece uma melhoria de desempenho, porque o mesmo nome de elemento ocorre em vários documentos.</span><span class="sxs-lookup"><span data-stu-id="2aceb-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aceb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2aceb-114">See Also</span></span>  
 [<span data-ttu-id="2aceb-115">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="2aceb-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
