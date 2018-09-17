---
title: Dados XML de inserção usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b9eedfab68dc6aeacf9ed51ffc7205b73c062ca
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45617351"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="490c9-102">Dados XML de inserção usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="490c9-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="490c9-103">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para irmão, o filho, e nós de atributo de inserção em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="490c9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="490c9-104">Para usar esses métodos, o objeto <xref:System.Xml.XPath.XPathNavigator> deve ser editável, ou seja, sua propriedade <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> deve ser `true`.</span><span class="sxs-lookup"><span data-stu-id="490c9-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="490c9-105">Os objetos <xref:System.Xml.XPath.XPathNavigator> que podem editar um documento XML são criados pelo método <xref:System.Xml.XmlDocument.CreateNavigator%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="490c9-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="490c9-106">os objetos de<xref:System.Xml.XPath.XPathNavigator> criados pela classe de <xref:System.Xml.XPath.XPathDocument> são somente leitura e qualquer tentativa de usar os métodos de um objeto de <xref:System.Xml.XPath.XPathNavigator> criado por <xref:System.Xml.XPath.XPathDocument> objetos resultados em <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="490c9-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="490c9-107">Para saber mais sobre como criar objetos <xref:System.Xml.XPath.XPathNavigator> editáveis, confira [Leitura de dados XML usando XPathDocument e XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="490c9-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="490c9-108">Inserindo nós</span><span class="sxs-lookup"><span data-stu-id="490c9-108">Inserting Nodes</span></span>  
 <span data-ttu-id="490c9-109">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece métodos para irmão, o filho, e nós de atributo de inserção em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="490c9-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="490c9-110">Esses métodos permitem que você insira nós e atributos em locais diferentes com relação a posição atual de <xref:System.Xml.XPath.XPathNavigator> objeto e são descritas nas seções.</span><span class="sxs-lookup"><span data-stu-id="490c9-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="490c9-111">Inserindo nós irmãos</span><span class="sxs-lookup"><span data-stu-id="490c9-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="490c9-112">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece os seguintes métodos para nós irmãos de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="490c9-113">Esses nós irmãos de inserção dos métodos antes e após o nó um objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado atualmente.</span><span class="sxs-lookup"><span data-stu-id="490c9-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="490c9-114">Os métodos de <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> e de <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> são sobrecarregados e aceitam `string`, um objeto de <xref:System.Xml.XmlReader> , ou um objeto de <xref:System.Xml.XPath.XPathNavigator> que contém o nó irmãos para adicionar como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="490c9-115">Ambos os métodos também retornam um objeto de <xref:System.Xml.XmlWriter> usado para nós irmãos de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="490c9-116">Os métodos de <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> e de <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> inserirem um único nó irmãos antes e após o nó que um objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado atualmente em usar o prefixo do namespace, o nome local, URI de namespace, e o valor especificado como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="490c9-117">No exemplo a seguir um novo elemento de `pages` é inserido antes que o elemento filho de `price` do primeiro elemento de `book` no arquivo de `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="490c9-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="490c9-118">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="490c9-119">Para obter mais informações sobre a <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> , consulte a documentação de referência da classe <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="490c9-120">Inserindo nós filho</span><span class="sxs-lookup"><span data-stu-id="490c9-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="490c9-121">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece os seguintes métodos para nós filho de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="490c9-122">Esses métodos append preceda e nós filho ao final de e a lista de nós filho do nó um objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado atualmente.</span><span class="sxs-lookup"><span data-stu-id="490c9-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="490c9-123">Como os métodos “que inserção na seção de nós irmãos”, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> aceitam `string`, um objeto de <xref:System.Xml.XmlReader> , ou um objeto de <xref:System.Xml.XPath.XPathNavigator> que contém o nó filho para adicionar como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="490c9-124">Ambos os métodos também retornam um objeto de <xref:System.Xml.XmlWriter> usado para nós filho de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="490c9-125">Também como os métodos “que inserção na seção de nós irmãos”, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> inserirem um único nó filho e fim da lista de nós filho do nó um objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado atualmente em usar o prefixo de namespace, o nome local, o URI de namespace, e o valor especificado como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="490c9-126">No exemplo a seguir, um novo elemento filho de `pages` é acrescentado à lista de elementos filho do primeiro elemento de `book` no arquivo de `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="490c9-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="490c9-127">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="490c9-128">Para obter mais informações sobre a <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> , consulte a documentação de referência da classe <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="490c9-129">Inserindo nós de atributo</span><span class="sxs-lookup"><span data-stu-id="490c9-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="490c9-130">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece os seguintes métodos para nós de atributo de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="490c9-131">Esses nós de atributo de inserção dos métodos no nó do elemento um objeto de <xref:System.Xml.XPath.XPathNavigator> são posicionados atualmente.</span><span class="sxs-lookup"><span data-stu-id="490c9-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="490c9-132">O método de <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> cria um nó de atributo no nó do elemento de <xref:System.Xml.XPath.XPathNavigator> um objeto é posicionado atualmente em usar o prefixo do namespace, o nome local, o URI de namespace, e o valor especificado como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="490c9-133">O método de <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> retorna um objeto de <xref:System.Xml.XmlWriter> usado para nós de atributo de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="490c9-134">No exemplo a seguir, um novo `discount` e atributos de `currency` são criados no elemento filho de `price` do primeiro elemento de `book` no arquivo de `contosoBooks.xml` usando o objeto de <xref:System.Xml.XmlWriter> retornado pelo método de <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="490c9-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="490c9-135">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="490c9-136">Para obter mais informações sobre métodos de <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> e de <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> , consulte a documentação de referência da classe <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="490c9-137">Copiando nós</span><span class="sxs-lookup"><span data-stu-id="490c9-137">Copying Nodes</span></span>  
 <span data-ttu-id="490c9-138">Em alguns casos você pode desejar preencher um documento XML com o conteúdo de um outro documento XML.</span><span class="sxs-lookup"><span data-stu-id="490c9-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="490c9-139">Ambas a classe de <xref:System.Xml.XPath.XPathNavigator> e a classe de <xref:System.Xml.XmlWriter> podem copiar nós em um objeto de <xref:System.Xml.XmlDocument> de um objeto existente de <xref:System.Xml.XmlReader> ou do objeto de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="490c9-140">Todos <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> de <xref:System.Xml.XPath.XPathNavigator> classe tem sobrecargas que podem aceitar um objeto de <xref:System.Xml.XPath.XPathNavigator> ou um objeto de <xref:System.Xml.XmlReader> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="490c9-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="490c9-141">O método de <xref:System.Xml.XmlWriter.WriteNode%2A> da classe de <xref:System.Xml.XmlWriter> possui sobrecargas que podem aceitar <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, ou o objeto de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="490c9-142">O exemplo a seguir copia todos os elementos de `book` de um documento para outro.</span><span class="sxs-lookup"><span data-stu-id="490c9-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="490c9-143">Inserindo valores</span><span class="sxs-lookup"><span data-stu-id="490c9-143">Inserting Values</span></span>  
 <span data-ttu-id="490c9-144">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> a valores de inserção para um nó em <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="490c9-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="490c9-145">Inserindo valores sem tipo</span><span class="sxs-lookup"><span data-stu-id="490c9-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="490c9-146">O método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> simplesmente insere o valor sem tipo de `string` passado como um parâmetro como o valor do nó no qual o objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="490c9-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="490c9-147">O valor é inserido sem nenhum tipo ou sem verificar se o novo valor é válido de acordo com o tipo de nó se as informações do esquema estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="490c9-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="490c9-148">No exemplo a seguir, o método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> é usado para atualizar todos os elementos `price` no arquivo `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="490c9-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="490c9-149">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="490c9-150">Inserindo valores tipados</span><span class="sxs-lookup"><span data-stu-id="490c9-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="490c9-151">Quando o tipo de um nó é um tipo simples de Esquema XML do W3C, o novo valor inserido pelo método <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> é verificado em relação às facetas do tipo simples antes que o valor seja definido.</span><span class="sxs-lookup"><span data-stu-id="490c9-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="490c9-152">Se o novo valor não for válido de acordo com o tipo de nó (por exemplo, definir um valor de `-1` em um elemento cujo tipo seja `xs:positiveInteger`), isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="490c9-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="490c9-153">O exemplo a seguir tenta alterar o valor do elemento `price` do primeiro elemento `book` no arquivo `contosoBooks.xml` para um valor <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="490c9-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="490c9-154">Como o tipo de esquema XML do elemento `price` está definido como `xs:decimal` nos arquivos `contosoBooks.xsd`, isso resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="490c9-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="490c9-155">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="490c9-156">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="490c9-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="490c9-157">As propriedades de InnerXml e de OuterXml</span><span class="sxs-lookup"><span data-stu-id="490c9-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="490c9-158">As propriedades <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> da classe <xref:System.Xml.XPath.XPathNavigator> alteram a marcação XML dos nós nos quais um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="490c9-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="490c9-159">A propriedade <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento com o conteúdo analisado da `string` do XML determinada.</span><span class="sxs-lookup"><span data-stu-id="490c9-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="490c9-160">Da mesma maneira, a propriedade <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento além do próprio nó atual.</span><span class="sxs-lookup"><span data-stu-id="490c9-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="490c9-161">Além dos métodos descritos neste tópico, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e as propriedades de <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> podem ser usados para inserir nós e valores em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="490c9-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="490c9-162">Para saber mais sobre como usar as propriedades <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> para inserir nós e valores, confira o tópico [Modificar dados XML usando XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="490c9-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="490c9-163">Namespace e XML: conflitos de idioma</span><span class="sxs-lookup"><span data-stu-id="490c9-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="490c9-164">Alguns conflitos relacionados ao escopo de namespace e declarações de `xml:lang` podem ocorrer ao inserir dados XML usando <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> de <xref:System.Xml.XPath.XPathNavigator> classe que utiliza objetos de <xref:System.Xml.XmlReader> como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="490c9-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="490c9-165">Estes são os conflitos possíveis de namespace.</span><span class="sxs-lookup"><span data-stu-id="490c9-165">The following are the possible namespace conflicts.</span></span>  
  
-   <span data-ttu-id="490c9-166">Se houver um em- escopo de namespace no contexto de objeto de <xref:System.Xml.XmlReader> , onde o prefixo para mapear URI de namespace não está no contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , uma nova declaração de namespace é adicionada ao nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="490c9-167">Se o mesmo URI de namespace é em- escopo dentro do contexto de objeto de <xref:System.Xml.XmlReader> e o contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , mas tem um prefixo diferente mapeado a ele em ambos os contextos, uma nova declaração de namespace é adicionada ao nó recentemente inserido, com o prefixo e o URI de namespace tirado de <xref:System.Xml.XmlReader> objetos.</span><span class="sxs-lookup"><span data-stu-id="490c9-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="490c9-168">Se o mesmo prefixo de namespace é em- escopo dentro do contexto de objeto de <xref:System.Xml.XmlReader> e o contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , mas tem URI diferente de um namespace mapeado a ele em ambos os contextos, uma nova declaração de namespace é adicionada ao nó recentemente inserido que a declara que um URI com o prefixo do namespace extraído do objeto de <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="490c9-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="490c9-169">Se o prefixo bem como o URI de namespace no contexto de objeto de <xref:System.Xml.XmlReader> e no contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> são o mesmo, nenhuma nova declaração de namespace é adicionada ao nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="490c9-170">A descrição anterior também se aplica às declarações namespace com `string` vazia como um prefixo (por exemplo, a declaração de namespace padrão).</span><span class="sxs-lookup"><span data-stu-id="490c9-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="490c9-171">Estes são os conflitos possíveis de `xml:lang` .</span><span class="sxs-lookup"><span data-stu-id="490c9-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
-   <span data-ttu-id="490c9-172">Se houver um em- escopo de atributo de `xml:lang` dentro do contexto de objeto de <xref:System.Xml.XmlReader> mas não no contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , um atributo de `xml:lang` cujo valor é extraído do objeto de <xref:System.Xml.XmlReader> é adicionado ao nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="490c9-173">Se houver um em- escopo de atributo de `xml:lang` dentro do contexto de objeto de <xref:System.Xml.XmlReader> e o contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , mas cada um possui um valor diferente, um atributo de `xml:lang` cujo valor é extraído do objeto de <xref:System.Xml.XmlReader> é adicionado ao nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="490c9-174">Se houver um em- escopo de atributo de `xml:lang` dentro do contexto de objeto de <xref:System.Xml.XmlReader> e o contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , mas cada um com o mesmo valor, nenhum novo atributo de `xml:lang` é adicionado no nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
-   <span data-ttu-id="490c9-175">Se houver um em- escopo de atributo de `xml:lang` dentro do contexto de objeto de <xref:System.Xml.XPath.XPathNavigator> , mas nenhum que existem no contexto de objeto de <xref:System.Xml.XmlReader> , nenhum atributo de `xml:lang` é adicionado ao nó recentemente inserido.</span><span class="sxs-lookup"><span data-stu-id="490c9-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="490c9-176">Inserindo nós com XmlWriter</span><span class="sxs-lookup"><span data-stu-id="490c9-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="490c9-177">Os métodos usados para inserir o irmão, o filho e os nós de atributo “inserindo descritos na seção de nós e valores são sobrecarregados.”</span><span class="sxs-lookup"><span data-stu-id="490c9-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="490c9-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> retornam um objeto de <xref:System.Xml.XmlWriter> usado para nós de inserção.</span><span class="sxs-lookup"><span data-stu-id="490c9-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="490c9-179">Métodos sem suporte de XmlWriter</span><span class="sxs-lookup"><span data-stu-id="490c9-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="490c9-180">Nem todos os métodos usados para gravar informações em um documento XML que usa a classe de <xref:System.Xml.XmlWriter> são suportados pela classe de <xref:System.Xml.XPath.XPathNavigator> devido a diferença entre o modelo de dados XPath e o Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="490c9-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="490c9-181">A tabela a seguir descreve os métodos da classe <xref:System.Xml.XmlWriter> não suportados pela classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="490c9-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="490c9-182">Método</span><span class="sxs-lookup"><span data-stu-id="490c9-182">Method</span></span>|<span data-ttu-id="490c9-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="490c9-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="490c9-184">Gerencie uma exceção de <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="490c9-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="490c9-185">Ignorado no nível raiz e em gera uma exceção de <xref:System.NotSupportedException> se chamado em qualquer outro o nível no documento XML.</span><span class="sxs-lookup"><span data-stu-id="490c9-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="490c9-186">Tratado como uma chamada para o método de <xref:System.Xml.XmlWriter.WriteString%2A> para o caractere ou os caracteres equivalentes.</span><span class="sxs-lookup"><span data-stu-id="490c9-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="490c9-187">Tratado como uma chamada para o método de <xref:System.Xml.XmlWriter.WriteString%2A> para o caractere ou os caracteres equivalentes.</span><span class="sxs-lookup"><span data-stu-id="490c9-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="490c9-188">Tratado como uma chamada para o método de <xref:System.Xml.XmlWriter.WriteString%2A> para o caractere ou os caracteres equivalentes.</span><span class="sxs-lookup"><span data-stu-id="490c9-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="490c9-189">Para obter mais informações sobre a classe de <xref:System.Xml.XmlWriter> , consulte a documentação de referência da classe <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="490c9-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="490c9-190">Vários objetos de XmlWriter</span><span class="sxs-lookup"><span data-stu-id="490c9-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="490c9-191">É possível ter vários objetos de <xref:System.Xml.XPath.XPathNavigator> que apontam para partes diferentes de um documento XML com um ou mais objetos abertos de <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="490c9-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="490c9-192">Vários objetos de <xref:System.Xml.XmlWriter> são permitidos e suportados em cenários de único thread.</span><span class="sxs-lookup"><span data-stu-id="490c9-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="490c9-193">Os seguintes são notas importantes a considerar ao usar vários <xref:System.Xml.XmlWriter> objeto.</span><span class="sxs-lookup"><span data-stu-id="490c9-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
-   <span data-ttu-id="490c9-194">Os fragmentos XML escritos por objetos de <xref:System.Xml.XmlWriter> são adicionados ao documento XML quando o método de <xref:System.Xml.XmlWriter.Close%2A> de cada objeto de <xref:System.Xml.XmlWriter> é chamado.</span><span class="sxs-lookup"><span data-stu-id="490c9-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="490c9-195">Até esse ponto, o objeto de <xref:System.Xml.XmlWriter> estiver escrevendo um fragmento desconectados.</span><span class="sxs-lookup"><span data-stu-id="490c9-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="490c9-196">Se uma operação é executada no documento XML, quaisquer informações que estão sendo gravados por um objeto de <xref:System.Xml.XmlWriter> , antes que <xref:System.Xml.XmlWriter.Close%2A> é chamado, não são afetados.</span><span class="sxs-lookup"><span data-stu-id="490c9-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
-   <span data-ttu-id="490c9-197">Se houver um objeto de abertura de <xref:System.Xml.XmlWriter> em uma subárvore específico XML e a subárvore é excluída, o objeto de <xref:System.Xml.XmlWriter> ainda pode adicionar à subárvore.</span><span class="sxs-lookup"><span data-stu-id="490c9-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="490c9-198">A subárvore transformações somente um fragmento excluído.</span><span class="sxs-lookup"><span data-stu-id="490c9-198">The subtree simply becomes a deleted fragment.</span></span>  
  
-   <span data-ttu-id="490c9-199">Se vários objetos de <xref:System.Xml.XmlWriter> são abertos no mesmo ponto no documento XML, são adicionados ao documento XML na ordem em que os objetos de <xref:System.Xml.XmlWriter> são fechados, não na ordem em que foram abertos.</span><span class="sxs-lookup"><span data-stu-id="490c9-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="490c9-200">O seguinte exemplo cria um objeto de <xref:System.Xml.XmlDocument> , cria um objeto de <xref:System.Xml.XPath.XPathNavigator> em seguida, usa o objeto de <xref:System.Xml.XmlWriter> retornado pelo método de <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> para criar a estrutura do primeiro livro no arquivo de `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="490c9-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="490c9-201">O exemplo salvá-los em como o arquivo de `book.xml` .</span><span class="sxs-lookup"><span data-stu-id="490c9-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="490c9-202">Salvando um documento XML</span><span class="sxs-lookup"><span data-stu-id="490c9-202">Saving an XML Document</span></span>  
 <span data-ttu-id="490c9-203">Salvando as alterações feitas a um objeto de <xref:System.Xml.XmlDocument> como resultado dos métodos descritos neste tópico é executado usando os métodos da classe <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="490c9-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="490c9-204">Para saber mais sobre como salvar as alterações feitas em um objeto <xref:System.Xml.XmlDocument>, confira [Salvar e gravar um documento](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="490c9-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490c9-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="490c9-205">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="490c9-206">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="490c9-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="490c9-207">Modificar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="490c9-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="490c9-208">Remover os dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="490c9-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
