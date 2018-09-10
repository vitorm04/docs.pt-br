---
title: Expressões XPath compilados
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7bb158331c1e03b18601dc553ed8ac0e8fa7930
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041389"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="8c52c-102">Expressões XPath compilados</span><span class="sxs-lookup"><span data-stu-id="8c52c-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="8c52c-103">Um objeto de <xref:System.Xml.XPath.XPathExpression> representa uma consulta XPath compilado retornada do método estático de <xref:System.Xml.XPath.XPathExpression.Compile%2A> da classe de <xref:System.Xml.XPath.XPathExpression> ou método de <xref:System.Xml.XPath.XPathNavigator.Compile%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="8c52c-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="8c52c-104">A classe de XPathExpression</span><span class="sxs-lookup"><span data-stu-id="8c52c-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="8c52c-105">Uma consulta XPath compilado é representada por um objeto de <xref:System.Xml.XPath.XPathExpression> é útil se a mesma consulta XPath está sendo usado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="8c52c-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="8c52c-106">Por exemplo, quando chamar o método de <xref:System.Xml.XPath.XPathNavigator.Select%2A> várias vezes, em vez de usar uma cadeia de caracteres que representa a consulta XPath cada vez, usa o método de <xref:System.Xml.XPath.XPathExpression.Compile%2A> da classe de <xref:System.Xml.XPath.XPathExpression> ou o método de <xref:System.Xml.XPath.XPathNavigator.Compile%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> para criar e armazenar em cachê a consulta XPath em um objeto de <xref:System.Xml.XPath.XPathExpression> para reutilização e melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="8c52c-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="8c52c-107">Uma vez que compilado, o objeto de <xref:System.Xml.XPath.XPathExpression> pode ser usado como entrada para os seguintes métodos da classe <xref:System.Xml.XPath.XPathNavigator> dependendo do tipo retornado de consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="8c52c-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="8c52c-108">A tabela a seguir descreve cada um dos tipos de retorno XPath W3C, suas equivalências do Microsoft.NET Framework, e métodos que o objeto de <xref:System.Xml.XPath.XPathExpression> pode ser usado com base no seu tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="8c52c-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="8c52c-109">Tipo de retorno XPath W3C</span><span class="sxs-lookup"><span data-stu-id="8c52c-109">W3C XPath Return Type</span></span>|<span data-ttu-id="8c52c-110">tipo equivalente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c52c-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="8c52c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c52c-111">Description</span></span>|<span data-ttu-id="8c52c-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="8c52c-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="8c52c-113">Uma coleção não ordenada de nós sem duplicatas criadas na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="8c52c-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="8c52c-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> ou <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="8c52c-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="8c52c-115">Um valor de `true` ou de `false` .</span><span class="sxs-lookup"><span data-stu-id="8c52c-115">A `true` or `false` value.</span></span>|<span data-ttu-id="8c52c-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> ou</span><span class="sxs-lookup"><span data-stu-id="8c52c-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="8c52c-117">Um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="8c52c-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="8c52c-118">Uma sequência de caracteres de UCS.</span><span class="sxs-lookup"><span data-stu-id="8c52c-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="8c52c-119">O método de <xref:System.Xml.XPath.XPathNavigator.Matches%2A> aceita uma expressão XPath como seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c52c-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="8c52c-120">O método de <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> retorna um objeto de <xref:System.Xml.XPath.XPathNavigator> , não um dos tipos de retorno XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="8c52c-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="8c52c-121">A propriedade ReturnType</span><span class="sxs-lookup"><span data-stu-id="8c52c-121">The ReturnType Property</span></span>  
 <span data-ttu-id="8c52c-122">Depois que uma consulta XPath foi compilada em um objeto de <xref:System.Xml.XPath.XPathExpression> , você pode usar a propriedade de <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> do objeto de <xref:System.Xml.XPath.XPathExpression> para determinar o que a consulta XPath retorna.</span><span class="sxs-lookup"><span data-stu-id="8c52c-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="8c52c-123">A propriedade de <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> retorna um dos seguintes valores de enumeração <xref:System.Xml.XPath.XPathResultType> que representam os tipos de retorno XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="8c52c-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="8c52c-124">O exemplo a seguir usa o objeto de <xref:System.Xml.XPath.XPathExpression> para retornar um número e um nó definidas do arquivo de `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="8c52c-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="8c52c-125">A propriedade de <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> de cada objeto de <xref:System.Xml.XPath.XPathExpression> bem como os resultados dos métodos de <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> e de <xref:System.Xml.XPath.XPathNavigator.Select%2A> são gravados no console.</span><span class="sxs-lookup"><span data-stu-id="8c52c-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="8c52c-126">O exemplo usa o arquivo `books.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="8c52c-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="8c52c-127">Expressões XPath de desempenho mais alto</span><span class="sxs-lookup"><span data-stu-id="8c52c-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="8c52c-128">Para melhor desempenho, use a expressão XPath a mais específica possível em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="8c52c-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="8c52c-129">Por exemplo, se o nó de `book` é um nó filho do nó de `bookstore` e o nó de `bookstore` é o elemento top-most em um documento XML, usar a expressão XPath `/bookstore/book` é mais rápido do que usar `//book`.</span><span class="sxs-lookup"><span data-stu-id="8c52c-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="8c52c-130">A expressão XPath de `//book` digitalizará cada nó na árvore XML para identificar nós compatíveis.</span><span class="sxs-lookup"><span data-stu-id="8c52c-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="8c52c-131">Além disso, usar os métodos definidos de navegação do nó fornecidos pela classe de <xref:System.Xml.XPath.XPathNavigator> pode resultar em melhor desempenho sobre os métodos de seleção fornecidos pela classe de <xref:System.Xml.XPath.XPathNavigator> em casos onde seus critérios de seleção são simples.</span><span class="sxs-lookup"><span data-stu-id="8c52c-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="8c52c-132">Por exemplo, se você precisar selecione o primeiro filho do nó atual, é mais rápido usar o método de <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> de usas a expressão XPath de `child::*[1]` e o método de <xref:System.Xml.XPath.XPathNavigator.Select%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c52c-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="8c52c-133">Para saber mais sobre os métodos de navegação de conjunto de nós da classe <xref:System.Xml.XPath.XPathNavigator>, confira [Navegação de conjunto de nós usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="8c52c-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c52c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c52c-134">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="8c52c-135">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="8c52c-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="8c52c-136">Selecionar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8c52c-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="8c52c-137">Avaliar as expressões XPath usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8c52c-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="8c52c-138">Correspondência de nós usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8c52c-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="8c52c-139">Tipos de nós reconhecidos com consultas XPath</span><span class="sxs-lookup"><span data-stu-id="8c52c-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="8c52c-140">Consultas e Namespaces de XPath</span><span class="sxs-lookup"><span data-stu-id="8c52c-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
