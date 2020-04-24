---
title: Navegação do namespace XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: f35318b1439b762bf7c87cff217ed1787e8d007c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156316"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="dad1a-102">Navegação do namespace XPath</span><span class="sxs-lookup"><span data-stu-id="dad1a-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="dad1a-103">Para usar consultas XPath com documentos XML, você precisará endereçar corretamente namespaces XML e os elementos contidos por espaços.</span><span class="sxs-lookup"><span data-stu-id="dad1a-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="dad1a-104">Namespaces impedem ambiguidades que podem ocorrer quando os nomes são usados em mais de um contexto; por exemplo, o nome `ID` pode referir-se a mais de um identificador associado com os diferentes elementos de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="dad1a-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="dad1a-105">A sintaxe do namespace especifica URIs, nomes, e prefixos que distinguiem os elementos de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="dad1a-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="dad1a-106">O exemplo neste tópico demonstra o uso dos prefixos em navegar em um documento XML com <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="dad1a-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="dad1a-107">Para obter mais informações sobre namespaces e sintaxe, consulte [arquivos XML: Noções básicas sobre namespaces XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="dad1a-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="dad1a-108">Declarações de namespace</span><span class="sxs-lookup"><span data-stu-id="dad1a-108">Namespace Declarations</span></span>  
 <span data-ttu-id="dad1a-109">As declarações namespace tornam os elementos de um documento XML distinguíveis e endereçáveis ao usar uma instância de <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="dad1a-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="dad1a-110">Prefixos de namespace fornece uma breve sintaxe para namespaces de resolução.</span><span class="sxs-lookup"><span data-stu-id="dad1a-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="dad1a-111">Os prefixos são definidos pelo formulário: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` nesta sintaxe o prefixo “`e`” é uma abreviação para o URI formal de namespace.</span><span class="sxs-lookup"><span data-stu-id="dad1a-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="dad1a-112">Você pode identificar o elemento de `Body` como um membro de namespace de `Envelope` usando a sintaxe: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="dad1a-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="dad1a-113">O seguinte documento XML será referenciado como `response.xml` no exemplo de navegação na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="dad1a-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="dad1a-114">Navegação pelo prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="dad1a-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="dad1a-115">O código nesta seção usa <xref:System.Xml.XPath.XPathNavigator> e objetos de <xref:System.Xml.XmlNamespaceManager> para selecionar o elemento de `Search` de documento XML na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="dad1a-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="dad1a-116">A consulta `xpath` inclui prefixos de namespace em cada elemento no caminho.</span><span class="sxs-lookup"><span data-stu-id="dad1a-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="dad1a-117">Especificando a identidade precisa namespaces que contêm cada elemento garante a navegação correta para o elemento de `Search` pelo método de <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> .</span><span class="sxs-lookup"><span data-stu-id="dad1a-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="dad1a-118">A precisão de namespaces totalmente aplicáveis e de nomes é mais de uma conveniência.</span><span class="sxs-lookup"><span data-stu-id="dad1a-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="dad1a-119">Pouca experimentação com a definição de documento e o código nos exemplos anteriores verificarão a navegação sem exceções totalmente qualificados de gera os nomes de elemento.</span><span class="sxs-lookup"><span data-stu-id="dad1a-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="dad1a-120">Por exemplo, a definição de elemento: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, e consulta: a cadeia de caracteres `xpath = "/s:Envelope/s:Body/Search";` sem o prefixo do namespace no elemento de `Search` retorna `null` em vez do elemento de `Search` .</span><span class="sxs-lookup"><span data-stu-id="dad1a-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad1a-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="dad1a-121">See also</span></span>

- [<span data-ttu-id="dad1a-122">Acessando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dad1a-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="dad1a-123">Selecionando, avaliando e correspondente de dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dad1a-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
