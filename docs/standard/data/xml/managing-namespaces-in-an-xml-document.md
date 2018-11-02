---
title: Gerenciando namespaces em um documento XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 620f9e59d65630895c01aff7d47c76876f3319d1
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347793"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="d72ae-102">Gerenciando namespaces em um documento XML</span><span class="sxs-lookup"><span data-stu-id="d72ae-102">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="d72ae-103">Namespaces XML e nomes de elementos e atributos em um documento XML com o URIs personalizado e predefinido.</span><span class="sxs-lookup"><span data-stu-id="d72ae-103">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="d72ae-104">Para criar essas associações, você define prefixos para URIs de namespace e usa os prefixos para qualificar nomes de atributo e elemento nos dados XML.</span><span class="sxs-lookup"><span data-stu-id="d72ae-104">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="d72ae-105">Namespaces impedem conflitos de nomes de elementos e atributos e permitem que elementos e atributos de mesmo nome sejam tratados e validados de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="d72ae-105">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a><span data-ttu-id="d72ae-106">Declaração de namespaces</span><span class="sxs-lookup"><span data-stu-id="d72ae-106">Declaring namespaces</span></span>  
 <span data-ttu-id="d72ae-107">Para declarar um namespace em um elemento, você usa o atributo `xmlns:`:</span><span class="sxs-lookup"><span data-stu-id="d72ae-107">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="d72ae-108">em que `<name>` é o prefixo de namespace e `<"uri">` é o URI que identifica o namespace.</span><span class="sxs-lookup"><span data-stu-id="d72ae-108">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="d72ae-109">Após declarar o prefixo, você pode usá-lo para qualificar os elementos e atributos em um documento XML e associá-los ao URI de namespace.</span><span class="sxs-lookup"><span data-stu-id="d72ae-109">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="d72ae-110">Porque o prefixo de namespace é usado em todo um documento, deve ser curto de tamanho.</span><span class="sxs-lookup"><span data-stu-id="d72ae-110">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="d72ae-111">Este exemplo define dois elementos `BOOK`.</span><span class="sxs-lookup"><span data-stu-id="d72ae-111">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="d72ae-112">O primeiro elemento é qualificado pelo prefixo, `mybook`, e o segundo elemento é qualificado pelo prefixo, `bb`.</span><span class="sxs-lookup"><span data-stu-id="d72ae-112">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="d72ae-113">Cada prefixo está associado a um URI de namespace diferente:</span><span class="sxs-lookup"><span data-stu-id="d72ae-113">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 <span data-ttu-id="d72ae-114">Para indicar que um elemento é uma parte de um namespace específico, adicione o prefixo de namespace a ele.</span><span class="sxs-lookup"><span data-stu-id="d72ae-114">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="d72ae-115">Por exemplo, se um elemento `Author` pertence ao namespace `mybook`, ele é declarado como `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="d72ae-115">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a><span data-ttu-id="d72ae-116">Escopo de declaração</span><span class="sxs-lookup"><span data-stu-id="d72ae-116">Declaration scope</span></span>  
 <span data-ttu-id="d72ae-117">Um namespace é efetivo do ponto de declaração até o fim do elemento em que foi declarado.</span><span class="sxs-lookup"><span data-stu-id="d72ae-117">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="d72ae-118">Neste exemplo, o namespace definido no elemento `BOOK` não se aplica a elementos fora do elemento `BOOK`, como o elemento `Publisher`:</span><span class="sxs-lookup"><span data-stu-id="d72ae-118">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="d72ae-119">Um namespace deve ser declarado para poder ser usado, mas não precisa aparecer na parte superior do documento XML.</span><span class="sxs-lookup"><span data-stu-id="d72ae-119">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="d72ae-120">Ao usar vários namespaces em um documento XML, você pode definir um namespace como o namespace padrão para criar um documento com aparência mais clara.</span><span class="sxs-lookup"><span data-stu-id="d72ae-120">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="d72ae-121">O namespace padrão é declarado no elemento raiz e se aplica a todos os elementos não qualificados no documento.</span><span class="sxs-lookup"><span data-stu-id="d72ae-121">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="d72ae-122">Namespaces padrão se aplicam apenas a elementos, não a atributos.</span><span class="sxs-lookup"><span data-stu-id="d72ae-122">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="d72ae-123">Para usar o namespace padrão, omita o prefixo e os dois-pontos da declaração no elemento:</span><span class="sxs-lookup"><span data-stu-id="d72ae-123">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="d72ae-124">Gerenciando namespaces</span><span class="sxs-lookup"><span data-stu-id="d72ae-124">Managing namespaces</span></span>  
 <span data-ttu-id="d72ae-125">A classe <xref:System.Xml.XmlNamespaceManager> armazena uma coleção de URIs de namespace e seus prefixos e permite que você veja, adicione e remova namespaces dessa coleção.</span><span class="sxs-lookup"><span data-stu-id="d72ae-125">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="d72ae-126">Em determinados contextos, essa classe é necessária para fornecer melhor desempenho de processamento de XML.</span><span class="sxs-lookup"><span data-stu-id="d72ae-126">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="d72ae-127">Por exemplo, a classe <xref:System.Xml.Xsl.XsltContext> usa <xref:System.Xml.XmlNamespaceManager> para suporte a XPath.</span><span class="sxs-lookup"><span data-stu-id="d72ae-127">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="d72ae-128">O gerenciador de namespace não executa nenhuma validação nos namespaces, mas presume que namespaces e prefixos já tenham sido verificados e estejam de acordo com a especificação [Namespaces do W3C](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="d72ae-128">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d72ae-129">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) não usa <xref:System.Xml.XmlNamespaceManager> para gerenciar namespaces.</span><span class="sxs-lookup"><span data-stu-id="d72ae-129">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) doesn't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="d72ae-130">Confira [Trabalhando com namespaces XML](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) na documentação do LINQ para obter informações sobre como gerenciar namespaces ao usar LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d72ae-130">See [Working with XML Namespaces](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="d72ae-131">Aqui estão algumas das tarefas de gerenciamento e de pesquisa podem ser executadas com a classe <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="d72ae-131">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="d72ae-132">Para saber mais e exemplos, siga os links para a página de referência para cada método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="d72ae-132">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="d72ae-133">Para</span><span class="sxs-lookup"><span data-stu-id="d72ae-133">To</span></span>|<span data-ttu-id="d72ae-134">Use</span><span class="sxs-lookup"><span data-stu-id="d72ae-134">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="d72ae-135">Adicionar um namespace</span><span class="sxs-lookup"><span data-stu-id="d72ae-135">Add a namespace</span></span>|<span data-ttu-id="d72ae-136">Método <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-136"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="d72ae-137">Remover um namespace</span><span class="sxs-lookup"><span data-stu-id="d72ae-137">Remove a namespace</span></span>|<span data-ttu-id="d72ae-138">Método <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-138"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="d72ae-139">Localizar o URI do namespace padrão</span><span class="sxs-lookup"><span data-stu-id="d72ae-139">Find the URI for the default namespace</span></span>|<span data-ttu-id="d72ae-140">Propriedade <xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-140"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="d72ae-141">Localizar o URI para um prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="d72ae-141">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="d72ae-142">Método <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-142"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="d72ae-143">Localizar o prefixo para um URI de namespace</span><span class="sxs-lookup"><span data-stu-id="d72ae-143">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="d72ae-144">Método <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-144"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="d72ae-145">Obter uma lista de namespaces do nó atual</span><span class="sxs-lookup"><span data-stu-id="d72ae-145">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="d72ae-146">Método <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-146"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="d72ae-147">Definir o escopo de um namespace</span><span class="sxs-lookup"><span data-stu-id="d72ae-147">Scope a namespace</span></span>|<span data-ttu-id="d72ae-148">Métodos <xref:System.Xml.XmlNamespaceManager.PushScope%2A> e <xref:System.Xml.XmlNamespaceManager.PopScope%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-148"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="d72ae-149">Verificar se um prefixo é definido no escopo atual</span><span class="sxs-lookup"><span data-stu-id="d72ae-149">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="d72ae-150">Método <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-150"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="d72ae-151">Obter a tabela de nomes usada para pesquisar URIs e prefixos</span><span class="sxs-lookup"><span data-stu-id="d72ae-151">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="d72ae-152">Propriedade <xref:System.Xml.XmlNamespaceManager.NameTable%2A></span><span class="sxs-lookup"><span data-stu-id="d72ae-152"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d72ae-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d72ae-153">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>  
- [<span data-ttu-id="d72ae-154">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="d72ae-154">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
