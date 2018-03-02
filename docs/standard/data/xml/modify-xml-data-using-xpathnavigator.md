---
title: Modificar dados XML usando XPathNavigator
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
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc46aeda6efe9f21bc094a4bc9d211fc282e9b65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="b5653-102">Modificar dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b5653-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="b5653-103">A classe <xref:System.Xml.XPath.XPathNavigator> fornece um conjunto de métodos usados para modificar nós e valores em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="b5653-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="b5653-104">Para usar esses métodos, o objeto <xref:System.Xml.XPath.XPathNavigator> deve ser editável, ou seja, sua propriedade <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> deve ser `true`.</span><span class="sxs-lookup"><span data-stu-id="b5653-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="b5653-105">Os objetos <xref:System.Xml.XPath.XPathNavigator> que podem editar um documento XML são criados pelo método <xref:System.Xml.XmlDocument.CreateNavigator%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="b5653-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b5653-106">Os objetos <xref:System.Xml.XPath.XPathNavigator> criados pela classe <xref:System.Xml.XPath.XPathDocument> são somente leitura e qualquer tentativa de usar os métodos de um objeto <xref:System.Xml.XPath.XPathNavigator> criado por um objeto <xref:System.Xml.XPath.XPathDocument> resultará em <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="b5653-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="b5653-107">Para saber mais sobre como criar objetos <xref:System.Xml.XPath.XPathNavigator> editáveis, confira [Leitura de dados XML usando XPathDocument e XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="b5653-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="b5653-108">Modificando nós</span><span class="sxs-lookup"><span data-stu-id="b5653-108">Modifying Nodes</span></span>  
 <span data-ttu-id="b5653-109">Uma técnica simples para alterar o valor de um nó é usar os métodos <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> e <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> da classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b5653-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="b5653-110">A tabela a seguir lista os efeitos desses métodos em tipos de nós diferentes.</span><span class="sxs-lookup"><span data-stu-id="b5653-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="b5653-111">Dados alterados</span><span class="sxs-lookup"><span data-stu-id="b5653-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="b5653-112">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="b5653-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="b5653-113">O conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="b5653-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="b5653-114">O valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="b5653-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="b5653-115">O conteúdo do texto.</span><span class="sxs-lookup"><span data-stu-id="b5653-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="b5653-116">O conteúdo, excluindo o destino.</span><span class="sxs-lookup"><span data-stu-id="b5653-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="b5653-117">O conteúdo do comentário.</span><span class="sxs-lookup"><span data-stu-id="b5653-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="b5653-118">Sem suporte.</span><span class="sxs-lookup"><span data-stu-id="b5653-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b5653-119">Não há suporte para a edição de nós <xref:System.Xml.XPath.XPathNodeType.Namespace> ou o nó <xref:System.Xml.XPath.XPathNodeType.Root>.</span><span class="sxs-lookup"><span data-stu-id="b5653-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="b5653-120">A classe <xref:System.Xml.XPath.XPathNavigator> também fornece um conjunto de métodos usados para inserir e remover nós.</span><span class="sxs-lookup"><span data-stu-id="b5653-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="b5653-121">Para saber mais sobre como inserir e remover nós de um documento XML, consulte os tópicos [Inserir dados XML usando XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) e [Remover dados XML usando XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="b5653-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="b5653-122">Modificando valores sem tipo</span><span class="sxs-lookup"><span data-stu-id="b5653-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="b5653-123">O método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> simplesmente insere o valor sem tipo de `string` passado como um parâmetro como o valor do nó no qual o objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="b5653-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="b5653-124">O valor é inserido sem nenhum tipo ou sem verificar se o novo valor é válido de acordo com o tipo de nó se as informações do esquema estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b5653-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="b5653-125">No exemplo a seguir, o método <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> é usado para atualizar todos os elementos `price` no arquivo `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="b5653-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="b5653-126">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="b5653-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="b5653-127">Modificando valores com tipo</span><span class="sxs-lookup"><span data-stu-id="b5653-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="b5653-128">Quando o tipo de um nó é um tipo simples de Esquema XML do W3C, o novo valor inserido pelo método <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> é verificado em relação às facetas do tipo simples antes que o valor seja definido.</span><span class="sxs-lookup"><span data-stu-id="b5653-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="b5653-129">Se o novo valor não for válido de acordo com o tipo de nó (por exemplo, definir um valor de `-1` em um elemento cujo tipo seja `xs:positiveInteger`), isso resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b5653-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="b5653-130">O exemplo a seguir tenta alterar o valor do elemento `price` do primeiro elemento `book` no arquivo `contosoBooks.xml` para um valor <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b5653-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="b5653-131">Como o tipo de esquema XML do elemento `price` está definido como `xs:decimal` nos arquivos `contosoBooks.xsd`, isso resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b5653-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="b5653-132">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="b5653-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b5653-133">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="b5653-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="b5653-134">Os efeitos de editar dados XML fortemente tipados</span><span class="sxs-lookup"><span data-stu-id="b5653-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="b5653-135">A classe <xref:System.Xml.XPath.XPathNavigator> usa o Esquema XML do W3C como base para a descrição de XML fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="b5653-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="b5653-136">Elementos e atributos podem ser anotados com informações de tipo com base na validação em relação a um documento de Esquema XML do W3C.</span><span class="sxs-lookup"><span data-stu-id="b5653-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="b5653-137">Os elementos que podem conter outros elementos ou atributos são chamados de tipos complexos, enquanto os que podem conter apenas texto são chamados de tipos simples.</span><span class="sxs-lookup"><span data-stu-id="b5653-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5653-138">Os atributos podem ter apenas tipos simples.</span><span class="sxs-lookup"><span data-stu-id="b5653-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="b5653-139">Um elemento ou atributo poderá ser considerado como válido para esquema se estiver de acordo com as regras específicas para sua definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="b5653-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="b5653-140">Um elemento que tem o tipo simples `xs:int` precisa conter um valor numérico entre -2147483648 e 2147483647 para ser válido para esquema.</span><span class="sxs-lookup"><span data-stu-id="b5653-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="b5653-141">Para tipos complexos, a validade do esquema do elemento dependente da validade do esquema de seus elementos filho e atributos.</span><span class="sxs-lookup"><span data-stu-id="b5653-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="b5653-142">Sendo assim, se um elemento é válido em relação a sua definição de tipo complexo, todos os seus elementos filho e atributos serão válidos com suas definições de tipo.</span><span class="sxs-lookup"><span data-stu-id="b5653-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="b5653-143">Da mesma forma, mesmo que um dos elementos filho ou atributos de um elemento não seja válido em relação a sua definição de tipo, ou se tiver uma validade desconhecida, o elemento também será inválido ou de validade desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b5653-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="b5653-144">Considerando que a validade de um elemento depende da validade de seus elementos filho e atributos, as alterações em algum deles resultará em alteração da validade do elemento se tiver sido válido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b5653-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="b5653-145">Especificamente, se os elementos filho ou atributos de um elemento forem inseridos, atualizados ou excluídos, a validade do elemento se tornará desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b5653-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="b5653-146">Isso é representado pela propriedade <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> da propriedade <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> do elemento que está sendo definida como <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="b5653-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="b5653-147">Além disso, este efeito propaga-se para cima recursivamente no documento XML, porque a validade do elemento pai do elemento (e seu elemento pai, e assim por diante) também se tornará desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b5653-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="b5653-148">Para saber mais sobre validação do esquema e sobre a classe <xref:System.Xml.XPath.XPathNavigator>, consulte [Validação de esquema usando XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="b5653-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="b5653-149">Modificando atributos</span><span class="sxs-lookup"><span data-stu-id="b5653-149">Modifying Attributes</span></span>  
 <span data-ttu-id="b5653-150">Os métodos <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> e <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> podem ser usados para modificar nós de atributo sem tipo e tipados bem como outros tipos de nós listados na seção “Modificando nós”.</span><span class="sxs-lookup"><span data-stu-id="b5653-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="b5653-151">O exemplo a seguir altera o valor do atributo `genre` do primeiro elemento `book` no arquivo `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="b5653-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="b5653-152">Para obter mais informações sobre os métodos <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> e <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, consulte as seções "Modificando valores sem tipo" e "Modificando valores com tipo"</span><span class="sxs-lookup"><span data-stu-id="b5653-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="b5653-153">Propriedades InnerXml e OuterXml</span><span class="sxs-lookup"><span data-stu-id="b5653-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="b5653-154">As propriedades <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> e <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> da classe <xref:System.Xml.XPath.XPathNavigator> alteram a marcação XML dos nós nos quais um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento.</span><span class="sxs-lookup"><span data-stu-id="b5653-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="b5653-155">A propriedade <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento com o conteúdo analisado da `string` do XML determinada.</span><span class="sxs-lookup"><span data-stu-id="b5653-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="b5653-156">Da mesma maneira, a propriedade <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> altera a marcação XML dos nós filho no qual um objeto <xref:System.Xml.XPath.XPathNavigator> está posicionado no momento além do próprio nó atual.</span><span class="sxs-lookup"><span data-stu-id="b5653-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="b5653-157">O exemplo a seguir usa a propriedade <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> para modificar o valor do elemento `price` e inserir um novo atributo `discount` no primeiro elemento `book` no arquivo `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="b5653-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="b5653-158">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="b5653-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="b5653-159">Modificando nós de namespace</span><span class="sxs-lookup"><span data-stu-id="b5653-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="b5653-160">No DOM (Document Object Model), as declarações de namespace são tratadas como se fossem atributos normais que podem ser inseridos, atualizados e excluídos.</span><span class="sxs-lookup"><span data-stu-id="b5653-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="b5653-161">A classe <xref:System.Xml.XPath.XPathNavigator> não permite essas operações em nós de namespace porque alterar o valor de um nó de namespace pode modificar a identidade dos elementos e dos atributos dentro do escopo do nó do namespace conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5653-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="b5653-162">Se o exemplo de XML anterior for modificado da seguinte forma, isso efetivamente renomeará cada elemento no documento porque o valor da URI do namespace de cada elemento será alterado.</span><span class="sxs-lookup"><span data-stu-id="b5653-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="b5653-163">Inserir os nós de namespace que não entrem em conflito com as declarações de namespace no escopo em que estão inseridos dentro é permitido pela classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="b5653-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="b5653-164">Nesse caso, as declarações de namespace não são declaradas em escopos menores no documento XML e não resultam em renomeação conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5653-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="b5653-165">Se o exemplo de XML acima for modificado da seguinte forma, as declarações de namespace serão propagadas corretamente no documento XML abaixo do escopo de outra declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="b5653-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="b5653-166">No exemplo de XML acima, o atributo `a:parent-id` é inserido no elemento `parent` no namespace `http://www.contoso.com/parent-id`.</span><span class="sxs-lookup"><span data-stu-id="b5653-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="b5653-167">O método <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> é usado para inserir o atributo enquanto estiver posicionado no elemento `parent`.</span><span class="sxs-lookup"><span data-stu-id="b5653-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="b5653-168">A declaração do namespace `http://www.contoso.com` é inserida automaticamente pela classe <xref:System.Xml.XPath.XPathNavigator> para manter a consistência do restante do documento XML.</span><span class="sxs-lookup"><span data-stu-id="b5653-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="b5653-169">Modificando nós de referência da entidade</span><span class="sxs-lookup"><span data-stu-id="b5653-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="b5653-170">Os nós de referência de entidade em um objeto <xref:System.Xml.XmlDocument> são somente leitura e não podem ser editados usando as classes <xref:System.Xml.XPath.XPathNavigator> ou <xref:System.Xml.XmlNode>.</span><span class="sxs-lookup"><span data-stu-id="b5653-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="b5653-171">Qualquer tentativa de modificar um nó de referência de entidade resulta em um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="b5653-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="b5653-172">Modificando nós xsi:nil</span><span class="sxs-lookup"><span data-stu-id="b5653-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="b5653-173">A recomendação do Esquema XML do W3C apresenta o conceito de um elemento ser nillable.</span><span class="sxs-lookup"><span data-stu-id="b5653-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="b5653-174">Quando um elemento é nillable, é possível que ele não tenha nenhum conteúdo e ainda ser válido.</span><span class="sxs-lookup"><span data-stu-id="b5653-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="b5653-175">O conceito de um elemento ser nillable é semelhante ao conceito de um objeto ser `null`.</span><span class="sxs-lookup"><span data-stu-id="b5653-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="b5653-176">A principal diferença é que um objeto `null` não pode ser acessado de nenhuma forma, enquanto que um elemento `xsi:nil` ainda tem propriedades como atributos que podem ser acessados, mas não tem conteúdo (elementos filho ou texto).</span><span class="sxs-lookup"><span data-stu-id="b5653-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="b5653-177">A existência do atributo `xsi:nil` com um valor `true` em um elemento em um documento XML é usada para indicar que um elemento não tem conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b5653-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="b5653-178">Se um objeto <xref:System.Xml.XPath.XPathNavigator> for usado para adicionar conteúdo a um elemento válido com um atributo `xsi:nil` com um valor `true`, o valor do seu atributo `xsi:nil` será definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="b5653-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5653-179">Se o conteúdo de um elemento com um atributo `xsi:nil` definido como `false` for excluído, o valor do atributo não será alterado para `true`.</span><span class="sxs-lookup"><span data-stu-id="b5653-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="b5653-180">Salvando um documento XML</span><span class="sxs-lookup"><span data-stu-id="b5653-180">Saving an XML Document</span></span>  
 <span data-ttu-id="b5653-181">Salvar as alterações feitas em um objeto <xref:System.Xml.XmlDocument> como resultado dos métodos de edição descritos neste tópico é realizado usando os métodos da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="b5653-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b5653-182">Para saber mais sobre como salvar as alterações feitas em um objeto <xref:System.Xml.XmlDocument>, confira [Salvar e gravar um documento](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="b5653-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5653-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5653-183">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="b5653-184">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="b5653-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="b5653-185">Inserir dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b5653-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="b5653-186">Remover os dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b5653-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
