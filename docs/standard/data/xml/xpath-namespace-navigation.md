---
title: "Navegação do namespace XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8cc8d1f031b3f00cdf2b698514220c25c9fec7be
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="802b5-102">Navegação do namespace XPath</span><span class="sxs-lookup"><span data-stu-id="802b5-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="802b5-103">Para usar consultas XPath com documentos XML, você precisará endereçar corretamente namespaces XML e os elementos contidos por espaços.</span><span class="sxs-lookup"><span data-stu-id="802b5-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="802b5-104">Namespaces impedem ambiguidades que podem ocorrer quando os nomes são usados em mais de um contexto; por exemplo, o nome `ID` pode referir-se a mais de um identificador associado com os diferentes elementos de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="802b5-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="802b5-105">A sintaxe do namespace especifica URIs, nomes, e prefixos que distinguiem os elementos de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="802b5-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="802b5-106">O exemplo neste tópico demonstra o uso dos prefixos em navegar em um documento XML com <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="802b5-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="802b5-107">Para saber mais sobre namespaces e sintaxe, confira [Noções básicas sobre namespaces XML](https://msdn.microsoft.com/library/aa468565.aspx).</span><span class="sxs-lookup"><span data-stu-id="802b5-107">For more information about namespaces and syntax, see [Understanding XML Namespaces](https://msdn.microsoft.com/library/aa468565.aspx).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="802b5-108">Declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="802b5-108">Namespace Declarations</span></span>  
 <span data-ttu-id="802b5-109">As declarações namespace tornam os elementos de um documento XML distinguíveis e endereçáveis ao usar uma instância de <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="802b5-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="802b5-110">Prefixos de namespace fornece uma breve sintaxe para namespaces de resolução.</span><span class="sxs-lookup"><span data-stu-id="802b5-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="802b5-111">Os prefixos são definidos pelo formulário: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` nesta sintaxe o prefixo “`e`” é uma abreviação para o URI formal de namespace.</span><span class="sxs-lookup"><span data-stu-id="802b5-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="802b5-112">Você pode identificar o elemento de `Body` como um membro de namespace de `Envelope` usando a sintaxe: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="802b5-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="802b5-113">O seguinte documento XML será referenciado como `response.xml` no exemplo de navegação na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="802b5-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="802b5-114">Navegação pelo prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="802b5-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="802b5-115">O código nesta seção usa <xref:System.Xml.XPath.XPathNavigator> e objetos de <xref:System.Xml.XmlNamespaceManager> para selecionar o elemento de `Search` de documento XML na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="802b5-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="802b5-116">A consulta `xpath` inclui prefixos de namespace em cada elemento no caminho.</span><span class="sxs-lookup"><span data-stu-id="802b5-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="802b5-117">Especificando a identidade precisa namespaces que contêm cada elemento garante a navegação correta para o elemento de `Search` pelo método de <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> .</span><span class="sxs-lookup"><span data-stu-id="802b5-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 <span data-ttu-id="802b5-118">A precisão de namespaces totalmente aplicáveis e de nomes é mais de uma conveniência.</span><span class="sxs-lookup"><span data-stu-id="802b5-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="802b5-119">Pouca experimentação com a definição de documento e o código nos exemplos anteriores verificarão a navegação sem exceções totalmente qualificados de gera os nomes de elemento.</span><span class="sxs-lookup"><span data-stu-id="802b5-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="802b5-120">Por exemplo, a definição de elemento: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, e consulta: a cadeia de caracteres `xpath = "/s:Envelope/s:Body/Search";` sem o prefixo do namespace no elemento de `Search` retorna `null` em vez do elemento de `Search` .</span><span class="sxs-lookup"><span data-stu-id="802b5-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802b5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="802b5-121">See Also</span></span>  
 [<span data-ttu-id="802b5-122">Acessando dados XML usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="802b5-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="802b5-123">Selecionando, avaliando e correspondendo dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="802b5-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
