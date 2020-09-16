---
title: Gerenciando namespaces em um documento XML
description: Saiba como gerenciar namespaces em um documento XML. Namespaces XML e nomes de elementos e atributos em um documento XML com o URIs personalizado e predefinido.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 500c477eaa98b2858573e1012c62db4bc6c68137
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548085"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="fe0c2-104">Gerenciando namespaces em um documento XML</span><span class="sxs-lookup"><span data-stu-id="fe0c2-104">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="fe0c2-105">Namespaces XML e nomes de elementos e atributos em um documento XML com o URIs personalizado e predefinido.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="fe0c2-106">Para criar essas associações, você define prefixos para URIs de namespace e usa os prefixos para qualificar nomes de atributo e elemento nos dados XML.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="fe0c2-107">Namespaces impedem conflitos de nomes de elementos e atributos e permitem que elementos e atributos de mesmo nome sejam tratados e validados de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="fe0c2-108">Declaração de namespaces</span><span class="sxs-lookup"><span data-stu-id="fe0c2-108">Declaring namespaces</span></span>  
 <span data-ttu-id="fe0c2-109">Para declarar um namespace em um elemento, você usa o atributo `xmlns:`:</span><span class="sxs-lookup"><span data-stu-id="fe0c2-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="fe0c2-110">em que `<name>` é o prefixo de namespace e `<"uri">` é o URI que identifica o namespace.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="fe0c2-111">Após declarar o prefixo, você pode usá-lo para qualificar os elementos e atributos em um documento XML e associá-los ao URI de namespace.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="fe0c2-112">Porque o prefixo de namespace é usado em todo um documento, deve ser curto de tamanho.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="fe0c2-113">Este exemplo define dois elementos `BOOK`.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="fe0c2-114">O primeiro elemento é qualificado pelo prefixo, `mybook`, e o segundo elemento é qualificado pelo prefixo, `bb`.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="fe0c2-115">Cada prefixo está associado a um URI de namespace diferente:</span><span class="sxs-lookup"><span data-stu-id="fe0c2-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="fe0c2-116">Para indicar que um elemento é uma parte de um namespace específico, adicione o prefixo de namespace a ele.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="fe0c2-117">Por exemplo, se um elemento `Author` pertence ao namespace `mybook`, ele é declarado como `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="fe0c2-118">Escopo de declaração</span><span class="sxs-lookup"><span data-stu-id="fe0c2-118">Declaration scope</span></span>  
 <span data-ttu-id="fe0c2-119">Um namespace é efetivo do ponto de declaração até o fim do elemento em que foi declarado.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="fe0c2-120">Neste exemplo, o namespace definido no elemento `BOOK` não se aplica a elementos fora do elemento `BOOK`, como o elemento `Publisher`:</span><span class="sxs-lookup"><span data-stu-id="fe0c2-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
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
  
 <span data-ttu-id="fe0c2-121">Um namespace deve ser declarado para poder ser usado, mas não precisa aparecer na parte superior do documento XML.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="fe0c2-122">Ao usar vários namespaces em um documento XML, você pode definir um namespace como o namespace padrão para criar um documento com aparência mais clara.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="fe0c2-123">O namespace padrão é declarado no elemento raiz e se aplica a todos os elementos não qualificados no documento.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="fe0c2-124">Namespaces padrão se aplicam apenas a elementos, não a atributos.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="fe0c2-125">Para usar o namespace padrão, omita o prefixo e os dois-pontos da declaração no elemento:</span><span class="sxs-lookup"><span data-stu-id="fe0c2-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="fe0c2-126">Gerenciando namespaces</span><span class="sxs-lookup"><span data-stu-id="fe0c2-126">Managing namespaces</span></span>  
 <span data-ttu-id="fe0c2-127">A classe <xref:System.Xml.XmlNamespaceManager> armazena uma coleção de URIs de namespace e seus prefixos e permite que você veja, adicione e remova namespaces dessa coleção.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="fe0c2-128">Em determinados contextos, essa classe é necessária para fornecer melhor desempenho de processamento de XML.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="fe0c2-129">Por exemplo, a classe <xref:System.Xml.Xsl.XsltContext> usa <xref:System.Xml.XmlNamespaceManager> para suporte a XPath.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="fe0c2-130">O gerenciador de namespace não executa nenhuma validação nos namespaces, mas presume que namespaces e prefixos já tenham sido verificados e estejam de acordo com a especificação [Namespaces do W3C](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="fe0c2-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe0c2-131">LINQ TO XML no [C#](../../linq/linq-xml-overview.md) e [Visual Basic](../../linq/linq-xml-overview.md) não usam <xref:System.Xml.XmlNamespaceManager> para gerenciar namespaces.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-131">LINQ TO XML in [C#](../../linq/linq-xml-overview.md) and [Visual Basic](../../linq/linq-xml-overview.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="fe0c2-132">Confira [Trabalhando com namespaces de XML(C#)](../../linq/namespaces-overview.md) e [Trabalhando com namespaces de XML (Visual Basic)](../../linq/namespaces-overview.md) na documentação do LINQ para obter informações sobre como gerenciar namespaces ao usar o LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-132">See [Working with XML Namespaces (C#)](../../linq/namespaces-overview.md) and [Working with XML Namespaces (Visual Basic)](../../linq/namespaces-overview.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="fe0c2-133">Aqui estão algumas das tarefas de gerenciamento e de pesquisa podem ser executadas com a classe <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="fe0c2-134">Para saber mais e exemplos, siga os links para a página de referência para cada método ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe0c2-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="fe0c2-135">Para</span><span class="sxs-lookup"><span data-stu-id="fe0c2-135">To</span></span>|<span data-ttu-id="fe0c2-136">Uso</span><span class="sxs-lookup"><span data-stu-id="fe0c2-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="fe0c2-137">Adicionar um namespace</span><span class="sxs-lookup"><span data-stu-id="fe0c2-137">Add a namespace</span></span>|<span data-ttu-id="fe0c2-138">Método <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-139">Remover um namespace</span><span class="sxs-lookup"><span data-stu-id="fe0c2-139">Remove a namespace</span></span>|<span data-ttu-id="fe0c2-140">Método <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-141">Localizar o URI do namespace padrão</span><span class="sxs-lookup"><span data-stu-id="fe0c2-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="fe0c2-142">Propriedade <xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="fe0c2-143">Localizar o URI para um prefixo de namespace</span><span class="sxs-lookup"><span data-stu-id="fe0c2-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="fe0c2-144">Método <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-145">Localizar o prefixo para um URI de namespace</span><span class="sxs-lookup"><span data-stu-id="fe0c2-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="fe0c2-146">Método <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-147">Obter uma lista de namespaces do nó atual</span><span class="sxs-lookup"><span data-stu-id="fe0c2-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="fe0c2-148">Método <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-149">Definir o escopo de um namespace</span><span class="sxs-lookup"><span data-stu-id="fe0c2-149">Scope a namespace</span></span>|<span data-ttu-id="fe0c2-150">Métodos <xref:System.Xml.XmlNamespaceManager.PushScope%2A> e <xref:System.Xml.XmlNamespaceManager.PopScope%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="fe0c2-151">Verificar se um prefixo é definido no escopo atual</span><span class="sxs-lookup"><span data-stu-id="fe0c2-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="fe0c2-152">Método <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="fe0c2-153">Obter a tabela de nomes usada para pesquisar URIs e prefixos</span><span class="sxs-lookup"><span data-stu-id="fe0c2-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="fe0c2-154">Propriedade <xref:System.Xml.XmlNamespaceManager.NameTable%2A></span><span class="sxs-lookup"><span data-stu-id="fe0c2-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe0c2-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe0c2-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="fe0c2-156">Documentos e dados XML</span><span class="sxs-lookup"><span data-stu-id="fe0c2-156">XML Documents and Data</span></span>](index.md)
