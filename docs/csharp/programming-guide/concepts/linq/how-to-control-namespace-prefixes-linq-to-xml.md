---
title: 'Como: Controlar prefixos de namespace (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 37fb604a9b66f4da2b1722808b2c79f8fbf097bf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485977"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="54b48-102">Como: Controlar prefixos de namespace (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="54b48-102">How to: Control Namespace Prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="54b48-103">Este tópico descreve como você pode controlar prefixos de namespace ao serializar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="54b48-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="54b48-104">Em muitas situações, não é necessário controlar prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="54b48-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="54b48-105">No entanto, determinadas ferramentas de programação XML requerem controle específico de prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="54b48-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="54b48-106">Por exemplo, você pode manipular uma folha de estilos XSLT ou um documento XAML que contenha as expressões XPath inseridas que se referem a prefixos de namespace específicos. Nesse caso, é importante que o documento seja serializado com esses prefixos específicos.</span><span class="sxs-lookup"><span data-stu-id="54b48-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="54b48-107">Esse é o motivo mais comum para controlar prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="54b48-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="54b48-108">Outra razão comum para controlar prefixos de namespace é que você deseja que os usuários editem manualmente o documento XML e deseja criar prefixos de namespace que sejam convenientes para o usuário digitar.</span><span class="sxs-lookup"><span data-stu-id="54b48-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="54b48-109">Por exemplo, você pode estar gerando um documento XSD.</span><span class="sxs-lookup"><span data-stu-id="54b48-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="54b48-110">As convenções de esquemas sugerem que você use `xs` ou `xsd` como o prefixo do namespace do esquema.</span><span class="sxs-lookup"><span data-stu-id="54b48-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="54b48-111">Para controlar prefixos de namespace, você insere os atributos que declaram os namespaces.</span><span class="sxs-lookup"><span data-stu-id="54b48-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="54b48-112">Se você declarar namespaces com prefixos específicos, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tentará respeitar os prefixos de namespace ao serializar.</span><span class="sxs-lookup"><span data-stu-id="54b48-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="54b48-113">Para criar um atributo que declare um namespace com um prefixo, você cria um atributo onde o namespace do nome do atributo é <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, e o nome do atributo é o prefixo do namespace.</span><span class="sxs-lookup"><span data-stu-id="54b48-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="54b48-114">O valor do atributo é o URI do namespace.</span><span class="sxs-lookup"><span data-stu-id="54b48-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54b48-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54b48-115">Example</span></span>  
 <span data-ttu-id="54b48-116">Esse exemplo declara dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="54b48-116">This example declares two namespaces.</span></span> <span data-ttu-id="54b48-117">Ele especifica que o namespace `http://www.adventure-works.com` tem o prefixo `aw` e que o namespace `www.fourthcoffee.com` tem o prefixo `fc`.</span><span class="sxs-lookup"><span data-stu-id="54b48-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="54b48-118">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="54b48-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54b48-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54b48-119">See also</span></span>

- [<span data-ttu-id="54b48-120">Trabalhando com namespaces XML (C#)</span><span class="sxs-lookup"><span data-stu-id="54b48-120">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)
