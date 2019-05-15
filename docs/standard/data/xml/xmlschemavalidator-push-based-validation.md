---
title: XmlSchemaValidator Envio- de validação
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e2b6ca8ef04ad6ff637a59f03f3b4cf04cb06ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615359"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="05c3c-102">XmlSchemaValidator Envio- de validação</span><span class="sxs-lookup"><span data-stu-id="05c3c-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="05c3c-103">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> fornece um mecanismo eficiente, de alto desempenho validar dados XML com esquemas XML de uma maneira envio- base.</span><span class="sxs-lookup"><span data-stu-id="05c3c-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="05c3c-104">Por exemplo, a classe de <xref:System.Xml.Schema.XmlSchemaValidator> permite que você valide um infoset XML no local sem ter que para serializá-lo como um documento XML e então um nova análise o documento usando um leitor validando XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="05c3c-105">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> pode ser usada em cenários avançados como mecanismos de validação de compilação sobre fontes de dados XML personalizados ou como uma maneira de criar um gravador validando XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="05c3c-106">A seguir está um exemplo de uso da classe de <xref:System.Xml.Schema.XmlSchemaValidator> para validar o arquivo de `contosoBooks.xml` com o esquema de `contosoBooks.xsd` .</span><span class="sxs-lookup"><span data-stu-id="05c3c-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="05c3c-107">O exemplo usa a classe de <xref:System.Xml.Serialization.XmlSerializer> para desserializar o arquivo de `contosoBooks.xml` e passar o valor de nós métodos de classe de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-108">Este exemplo é usado em todo as seções deste tópico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="05c3c-109">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="05c3c-110">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="bookstore">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element maxOccurs="unbounded" name="book">  
                    <xs:complexType>  
                        <xs:sequence>  
                            <xs:element name="title" type="xs:string" />  
                            <xs:element name="author">  
                                <xs:complexType>  
                                    <xs:sequence>  
                                        <xs:element minOccurs="0" name="name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />  
                                    </xs:sequence>  
                                </xs:complexType>  
                            </xs:element>  
                            <xs:element name="price" type="xs:decimal" />  
                        </xs:sequence>  
                        <xs:attribute name="genre" type="xs:string" use="required" />  
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />  
                        <xs:attribute name="ISBN" type="xs:string" use="required" />  
                    </xs:complexType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="05c3c-111">Validando dados XML usando XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="05c3c-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="05c3c-112">Para iniciar a validar um infoset XML, primeiro você deve inicializar uma nova instância da classe <xref:System.Xml.Schema.XmlSchemaValidator> que usa o construtor de <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="05c3c-113">O construtor de <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> leva <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, e objetos de <xref:System.Xml.XmlNamespaceManager> como os parâmetros bem como <xref:System.Xml.Schema.XmlSchemaValidationFlags> avaliada como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="05c3c-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="05c3c-114">O objeto de <xref:System.Xml.XmlNameTable> é usado para atomizar cadeias de caracteres conhecidos de namespace como o namespace do esquema, o namespace XML, e assim por diante, e passado para o método de <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> para validar o conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="05c3c-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="05c3c-115">O objeto de <xref:System.Xml.Schema.XmlSchemaSet> contém os esquemas XML usados para validar o infoset XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="05c3c-116">O objeto de <xref:System.Xml.XmlNamespaceManager> é usado para resolver namespaces encontrados durante a validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="05c3c-117">O valor de <xref:System.Xml.Schema.XmlSchemaValidationFlags> é usado para desativar determinados recursos de validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="05c3c-118">Para obter mais informações sobre o construtor de <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="05c3c-119">Inicializando a validação</span><span class="sxs-lookup"><span data-stu-id="05c3c-119">Initializing Validation</span></span>  
 <span data-ttu-id="05c3c-120">Depois que um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> foi construído, há dois métodos sobrecarregados de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> usados para inicializar o estado do objeto de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="05c3c-121">Estes são os dois métodos de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="05c3c-122">O método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> de opção inicializa um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> ao seu estado inicial, e o método sobrecarregado de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> que leva <xref:System.Xml.Schema.XmlSchemaObject> como um parâmetro inicializa um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> ao seu estado inicial para a validação parcial.</span><span class="sxs-lookup"><span data-stu-id="05c3c-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="05c3c-123">Ambos os métodos de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> só podem ser chamados imediatamente após um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> foi construído ou após uma chamada a <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="05c3c-124">Para um exemplo de método <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> , consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-125">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="05c3c-126">Validação parcial</span><span class="sxs-lookup"><span data-stu-id="05c3c-126">Partial Validation</span></span>  
 <span data-ttu-id="05c3c-127">O método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> que leva <xref:System.Xml.Schema.XmlSchemaObject> como um parâmetro inicializa um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> ao seu estado inicial para a validação parcial.</span><span class="sxs-lookup"><span data-stu-id="05c3c-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="05c3c-128">No exemplo a seguir, <xref:System.Xml.Schema.XmlSchemaObject> é inicializado para validação usando o método parcial de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="05c3c-129">O elemento do esquema de `orderNumber` é passado selecionando o elemento de esquema por <xref:System.Xml.XmlQualifiedName> na coleção de <xref:System.Xml.Schema.XmlSchemaObjectTable> retornada pela propriedade de <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> do objeto de <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="05c3c-130">O objeto de <xref:System.Xml.Schema.XmlSchemaValidator> valida neste elemento específico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add(Nothing, "schema.xsd")  
schemaSet.Compile()  
Dim nameTable As NameTable = New NameTable()  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
  
Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)  
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))  
  
validator.ValidateElement("orderNumber", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateText("123")  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
schemaSet.Compile();  
NameTable nameTable = new NameTable();  
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);  
  
validator.ValidateElement("orderNumber", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateText("123");  
validator.ValidateEndElement(null);  
```  
  
 <span data-ttu-id="05c3c-131">O exemplo a seguir usa o esquema XML como entrada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="05c3c-132">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="05c3c-133">Adicionando esquemas adicionais</span><span class="sxs-lookup"><span data-stu-id="05c3c-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="05c3c-134">O método de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> da classe de <xref:System.Xml.Schema.XmlSchemaValidator> é usado para adicionar um esquema XML para o conjunto de esquemas usados durante a validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="05c3c-135">O método de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> pode ser usado para simular o efeito de localizar um esquema XML embutido no infoset XML que está sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-136">O namespace de destino do parâmetro de <xref:System.Xml.Schema.XmlSchema> pode não corresponder de qualquer elemento ou atributo já encontrado pelo objeto de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="05c3c-137">Se o valor de <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> não foi passado como um parâmetro para o construtor de <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> , o método de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> não fará nada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="05c3c-138">O resultado de método <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> é dependente no contexto atual do nó XML que está sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="05c3c-139">Para obter mais informações sobre contextos de validação, consulte a seção contexto validação” neste tópico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="05c3c-140">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="05c3c-141">Validando elementos, atributos, e conteúdo</span><span class="sxs-lookup"><span data-stu-id="05c3c-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="05c3c-142">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> fornece vários métodos usados para validar elementos, atributos, e o conteúdo em um infoset XML com esquemas XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="05c3c-143">A tabela a seguir descreve cada um desses métodos.</span><span class="sxs-lookup"><span data-stu-id="05c3c-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="05c3c-144">Método</span><span class="sxs-lookup"><span data-stu-id="05c3c-144">Method</span></span>|<span data-ttu-id="05c3c-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="05c3c-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="05c3c-146">Valida o nome do elemento no contexto atual.</span><span class="sxs-lookup"><span data-stu-id="05c3c-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="05c3c-147">Valida o atributo no contexto do elemento atual ou contra o objeto de <xref:System.Xml.Schema.XmlSchemaAttribute> passado como um parâmetro para o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="05c3c-148">Verifica se todos os atributos necessários no contexto do elemento entram presente e prepara o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> para validar o conteúdo filho do elemento.</span><span class="sxs-lookup"><span data-stu-id="05c3c-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="05c3c-149">Valida se o texto é permitido no contexto do elemento atual, e acumula o texto para validação se o elemento atual tem conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="05c3c-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="05c3c-150">Valida se o espaço em branco é permitido no contexto do elemento atual, e acumula o espaço em branco para validação se o elemento atual tem conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="05c3c-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="05c3c-151">Verifica se o conteúdo de texto do elemento é válida de acordo com seu tipo de dados para elementos com conteúdo simples, e verifica se o conteúdo do elemento atual seja concluída para elementos com conteúdo complexo.</span><span class="sxs-lookup"><span data-stu-id="05c3c-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="05c3c-152">Ignora a validação de conteúdo do elemento atual e prepara o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> para validar o conteúdo no contexto do elemento pai.</span><span class="sxs-lookup"><span data-stu-id="05c3c-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="05c3c-153">Termina a validação verifica e restrições de identidade para o documento inteiro XML se a opção de validação de <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> é definida.</span><span class="sxs-lookup"><span data-stu-id="05c3c-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-154">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> tiver definido uma transição de estado que aplica a sequência e a ocorrência de chamadas feitas a cada um dos métodos descritos na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="05c3c-155">A transição específica do estado da classe de <xref:System.Xml.Schema.XmlSchemaValidator> é descrita da seção “de transição de estado XmlSchemaValidator” neste tópico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="05c3c-156">Para um exemplo dos métodos usados para validar elementos, atributos, e o conteúdo em um infoset XML, consulte o exemplo na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="05c3c-157">Para obter mais informações sobre estes métodos, consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="05c3c-158">Validando conteúdo usando um XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="05c3c-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="05c3c-159"><xref:System.Xml.Schema.XmlValueGetter>`delegate` pode ser usado para passar o valor do atributo, texto, ou de nós de espaço em branco como o Common Language Runtime (CLR) tipos compatível com o tipo de idioma de XSD (XSD) de atributo, texto, ou o nó de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="05c3c-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="05c3c-160"><xref:System.Xml.Schema.XmlValueGetter>`delegate` é útil se o valor de CLR de um atributo, um texto, ou um nó de espaço em branco já estiver disponível, e evita o custo de convertê-los em `string` e dos reparsing novamente para validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="05c3c-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, e os métodos de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> são sobrecarregados e aceitar o valor do atributo, texto, ou de nós de espaço em branco como `string` ou <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span><span class="sxs-lookup"><span data-stu-id="05c3c-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="05c3c-162">Os seguintes métodos da classe <xref:System.Xml.Schema.XmlSchemaValidator> aceitam <xref:System.Xml.Schema.XmlValueGetter>`delegate` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="05c3c-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="05c3c-163">A seguir está um exemplo <xref:System.Xml.Schema.XmlValueGetter>`delegate` extraído do exemplo de classe de <xref:System.Xml.Schema.XmlSchemaValidator> na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="05c3c-164"><xref:System.Xml.Schema.XmlValueGetter>`delegate` retorna o valor de um atributo como um objeto de <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="05c3c-165">Para validar este objeto de <xref:System.DateTime> retornado por <xref:System.Xml.Schema.XmlValueGetter>, converte o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> ele para o primeiro ValueType (ValueType é CLR padrão que mapeia para o tipo XSD) para o tipo de dados de atributo e então verifica facetas o valor convertido.</span><span class="sxs-lookup"><span data-stu-id="05c3c-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 <span data-ttu-id="05c3c-166">Para um exemplo completo de <xref:System.Xml.Schema.XmlValueGetter>`delegate`, consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-167">Para obter mais informações sobre <xref:System.Xml.Schema.XmlValueGetter> de `delegate`, consulte <xref:System.Xml.Schema.XmlValueGetter>, e documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="05c3c-168">POST-Esquema-Validação-informações</span><span class="sxs-lookup"><span data-stu-id="05c3c-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="05c3c-169">A classe de <xref:System.Xml.Schema.XmlSchemaInfo> representa algumas de POST-Esquema-Validação- informações de um nó XML validado pela classe de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="05c3c-170">Os vários métodos da classe <xref:System.Xml.Schema.XmlSchemaValidator> aceitar um objeto de <xref:System.Xml.Schema.XmlSchemaInfo> como um opcional), (`null`parâmetro de `out` .</span><span class="sxs-lookup"><span data-stu-id="05c3c-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="05c3c-171">Em cima de validação com êxito, as propriedades do objeto de <xref:System.Xml.Schema.XmlSchemaInfo> são definidas com os resultados de validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="05c3c-172">Por exemplo, em cima de validação com êxito de um atributo usando o método de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo>do objeto de <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A> (se especificado), <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, e as propriedades de <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> são especificados com os resultados de validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="05c3c-173">Os seguintes métodos da classe <xref:System.Xml.Schema.XmlSchemaValidator> aceitar um objeto de <xref:System.Xml.Schema.XmlSchemaInfo> como um parâmetro de saída.</span><span class="sxs-lookup"><span data-stu-id="05c3c-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="05c3c-174">Para um exemplo completo da classe de <xref:System.Xml.Schema.XmlSchemaInfo> , consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-175">Para obter mais informações sobre a classe de <xref:System.Xml.Schema.XmlSchemaInfo> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaInfo> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="05c3c-176">Recuperando partículas previstas, atributos, e atributos padrão não especificado</span><span class="sxs-lookup"><span data-stu-id="05c3c-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="05c3c-177">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> fornece <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, e métodos de <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> para recuperar as partículas previstas, atributos, e atributos padrão não especificado no contexto atual de validação.</span><span class="sxs-lookup"><span data-stu-id="05c3c-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="05c3c-178">Recuperando partículas previstas</span><span class="sxs-lookup"><span data-stu-id="05c3c-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="05c3c-179">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz de objetos de <xref:System.Xml.Schema.XmlSchemaParticle> que contêm as partículas previstas no contexto do elemento atual.</span><span class="sxs-lookup"><span data-stu-id="05c3c-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="05c3c-180">As partículas válidas que podem ser retornadas pelo método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> são instâncias de classes de <xref:System.Xml.Schema.XmlSchemaElement> e de <xref:System.Xml.Schema.XmlSchemaAny> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="05c3c-181">Quando o compositor para o modelo de conteúdo for `xs:sequence`, somente a partícula seguir na sequência é retornada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="05c3c-182">Se o compositor para o modelo de conteúdo é `xs:all` ou `xs:choice`, todas as partículas válidos que podem seguir no contexto do elemento atual são retornadas.</span><span class="sxs-lookup"><span data-stu-id="05c3c-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-183">Se o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> é chamado imediatamente depois de chamar o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> , o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna todos os elementos globais.</span><span class="sxs-lookup"><span data-stu-id="05c3c-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="05c3c-184">Por exemplo, no esquema e o documento XML de idioma de XSD (XSD) que seguem, após validar o elemento de `book` , o elemento de `book` é o contexto do elemento atual.</span><span class="sxs-lookup"><span data-stu-id="05c3c-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="05c3c-185">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz que contém um único objeto de <xref:System.Xml.Schema.XmlSchemaElement> que representa o elemento de `title` .</span><span class="sxs-lookup"><span data-stu-id="05c3c-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="05c3c-186">Quando o contexto de validação é o elemento de `title` , o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="05c3c-187">Se o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> é chamado depois que o elemento de `title` foi validado mas antes do elemento de `description` está validado, retorna uma matriz que contém um único objeto de <xref:System.Xml.Schema.XmlSchemaElement> que representa o elemento de `description` .</span><span class="sxs-lookup"><span data-stu-id="05c3c-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="05c3c-188">Se o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> é chamado depois que o elemento de `description` já foi validado então retorna uma matriz que contém um único objeto de <xref:System.Xml.Schema.XmlSchemaAny> que representa a curinga.</span><span class="sxs-lookup"><span data-stu-id="05c3c-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
validator.Initialize()  
  
validator.ValidateElement("book", "", Nothing)  
  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("title", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
validator.ValidateEndElement(Nothing)  
  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("description", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()  
    Console.WriteLine(particle.GetType())  
Next  
  
validator.ValidateElement("namespace", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlReader reader = XmlReader.Create("input.xml");  
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize();  
  
validator.ValidateElement("book", "", null);  
  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("title", "", null);  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("description", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())  
{  
    Console.WriteLine(particle.GetType());  
}  
  
validator.ValidateElement("namespace", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
validator.ValidateEndElement(null);  
```  
  
 <span data-ttu-id="05c3c-189">O exemplo a seguir usa XML como entrada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="05c3c-190">O exemplo a seguir usa o esquema XSD como entrada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-191">Os resultados de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, e métodos de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> da classe de <xref:System.Xml.Schema.XmlSchemaValidator> são dependentes no contexto atual sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="05c3c-192">Para obter mais informações, consulte a seção contexto validação” neste tópico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="05c3c-193">Para um exemplo de método <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-194">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="05c3c-195">Recuperando atributos esperados</span><span class="sxs-lookup"><span data-stu-id="05c3c-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="05c3c-196">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz de objetos de <xref:System.Xml.Schema.XmlSchemaAttribute> que contêm os atributos esperados no contexto do elemento atual.</span><span class="sxs-lookup"><span data-stu-id="05c3c-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="05c3c-197">Por exemplo, no exemplo na introdução, o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> é usado para recuperar todos os atributos do elemento de `book` .</span><span class="sxs-lookup"><span data-stu-id="05c3c-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="05c3c-198">Se você chamar o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> imediatamente após o método de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> , todos os atributos que podem aparecer no documento XML são retornados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="05c3c-199">No entanto, se você chamar o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> depois que um ou mais chamadas para o método de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , os atributos que não foram validados ainda para o elemento atual são retornados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-200">Os resultados de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, e métodos de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> da classe de <xref:System.Xml.Schema.XmlSchemaValidator> são dependentes no contexto atual sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="05c3c-201">Para obter mais informações, consulte a seção contexto validação” neste tópico.</span><span class="sxs-lookup"><span data-stu-id="05c3c-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="05c3c-202">Para um exemplo de método <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-203">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="05c3c-204">Recuperando atributos padrão não especificado</span><span class="sxs-lookup"><span data-stu-id="05c3c-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="05c3c-205">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> preenche <xref:System.Collections.ArrayList> especificado com objetos de <xref:System.Xml.Schema.XmlSchemaAttribute> para todos os atributos com valores padrão que não foram validados anteriormente usando o método de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> no contexto do elemento.</span><span class="sxs-lookup"><span data-stu-id="05c3c-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="05c3c-206">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> deve ser chamado após o método chamado de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> em cada atributo no contexto do elemento.</span><span class="sxs-lookup"><span data-stu-id="05c3c-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="05c3c-207">O método de <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> deve ser usado para determinar quais atributos padrão devem ser inseridos no documento XML que está sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="05c3c-208">Para obter mais informações sobre o método de <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> , consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="05c3c-209">Eventos de validação do esquema de tratamento</span><span class="sxs-lookup"><span data-stu-id="05c3c-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="05c3c-210">Os avisos e os erros de validação de esquema encontrados durante a validação são tratadas pelo evento de <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> da classe de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="05c3c-211">Os avisos de validação de esquema têm um valor de <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Warning> e os erros de validação de esquema têm um valor de <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="05c3c-212">Se nenhum <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> foi atribuído, <xref:System.Xml.Schema.XmlSchemaValidationException> é acionada para todos os erros de validação de esquema com um valor de <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="05c3c-213">No entanto, <xref:System.Xml.Schema.XmlSchemaValidationException> não é lançada para avisos de validação de esquema com um valor de <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="05c3c-214">O código a seguir é um exemplo de <xref:System.Xml.Schema.ValidationEventHandler> que receberá os avisos e os erros de validação de esquema encontrados durante a validação de esquema tomada de exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
    Select Case e.Severity  
        Case XmlSeverityType.Error  
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)  
            Exit Sub  
        Case XmlSeverityType.Warning  
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)  
            Exit Sub  
    End Select  
End Sub  
```  
  
```csharp  
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)  
{  
    switch (e.Severity)  
    {  
        case XmlSeverityType.Error:  
            Console.WriteLine("\nError: {0}", e.Message);  
            break;  
        case XmlSeverityType.Warning:  
            Console.WriteLine("\nWarning: {0}", e.Message);  
            break;  
    }  
}  
```  
  
 <span data-ttu-id="05c3c-215">Para um exemplo completo de <xref:System.Xml.Schema.ValidationEventHandler>, consulte o exemplo na introdução.</span><span class="sxs-lookup"><span data-stu-id="05c3c-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="05c3c-216">Para obter mais informações, consulte a documentação de referência da classe <xref:System.Xml.Schema.XmlSchemaInfo> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="05c3c-217">Transição de estado de XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="05c3c-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="05c3c-218">A classe de <xref:System.Xml.Schema.XmlSchemaValidator> tiver definido uma transição de estado que aplica a sequência e a ocorrência de chamadas feitas a cada um dos métodos usados para validar elementos, atributos, e o conteúdo em um infoset XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="05c3c-219">A tabela a seguir descreve a transição de estado da classe de <xref:System.Xml.Schema.XmlSchemaValidator> , e a sequência e a ocorrência de chamadas de método que podem ser feitas em cada estado.</span><span class="sxs-lookup"><span data-stu-id="05c3c-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="05c3c-220">Estado</span><span class="sxs-lookup"><span data-stu-id="05c3c-220">State</span></span>|<span data-ttu-id="05c3c-221">Transição</span><span class="sxs-lookup"><span data-stu-id="05c3c-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="05c3c-222">Validar</span><span class="sxs-lookup"><span data-stu-id="05c3c-222">Validate</span></span>|<span data-ttu-id="05c3c-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="05c3c-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="05c3c-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="05c3c-224">TopLevel</span></span>|<span data-ttu-id="05c3c-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="05c3c-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="05c3c-226">Elemento</span><span class="sxs-lookup"><span data-stu-id="05c3c-226">Element</span></span>|<span data-ttu-id="05c3c-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span><span class="sxs-lookup"><span data-stu-id="05c3c-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="05c3c-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="05c3c-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="05c3c-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="05c3c-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="05c3c-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="05c3c-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="05c3c-231">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="05c3c-231">Content</span></span>|<span data-ttu-id="05c3c-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="05c3c-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-233"><xref:System.InvalidOperationException> é acionada por cada um dos métodos na tabela acima quando a chamada para o método é feito na sequência incorreta de acordo com o estado atual de um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="05c3c-234">A tabela de transição de estado anterior de símbolos de pontuação usos para descrever os métodos e outros estados que podem ser chamados para cada estado de transição de estado da classe de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="05c3c-235">Os símbolos usados são os mesmos símbolos localizados na referência de padrões XML para o Document type definition (DTD).</span><span class="sxs-lookup"><span data-stu-id="05c3c-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="05c3c-236">A tabela a seguir descreve como símbolos de pontuação localizados na tabela de transição de estado anterior afetam os métodos e outros estados que podem ser chamados para cada estado na transição de estado da classe de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="05c3c-237">Símbolo</span><span class="sxs-lookup"><span data-stu-id="05c3c-237">Symbol</span></span>|<span data-ttu-id="05c3c-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="05c3c-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="05c3c-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="05c3c-239">&#124;</span></span>|<span data-ttu-id="05c3c-240">O método ou o estado (aquele antes de barra ou esse após ele) podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="05c3c-241">?</span><span class="sxs-lookup"><span data-stu-id="05c3c-241">?</span></span>|<span data-ttu-id="05c3c-242">O método ou indica que antes do ponto de interrogação é opcional mas se é chamado pode ser chamado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="05c3c-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="05c3c-243">O método ou indica que precede \* o símbolo é opcional, e pode ser chamado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="05c3c-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="05c3c-244">Contexto de validação</span><span class="sxs-lookup"><span data-stu-id="05c3c-244">Validation Context</span></span>  
 <span data-ttu-id="05c3c-245">Os métodos da classe <xref:System.Xml.Schema.XmlSchemaValidator> usada para validar elementos, atributos, e o conteúdo em um infoset XML, alterar o contexto de validação de um objeto de <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="05c3c-246">Por exemplo, a validação ignora do método de <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> de conteúdo do elemento atual e prepara o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> para validar o conteúdo no contexto do elemento pai; é equivalente à validação de ir para todos os filhos do elemento atual e de chamar o método de <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="05c3c-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="05c3c-247">Os resultados de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, e métodos de <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> da classe de <xref:System.Xml.Schema.XmlSchemaValidator> são dependentes no contexto atual sendo validada.</span><span class="sxs-lookup"><span data-stu-id="05c3c-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="05c3c-248">A tabela a seguir descreve os resultados de chamar esses métodos após chamando um dos métodos da classe <xref:System.Xml.Schema.XmlSchemaValidator> usada para validar elementos, atributos, e o conteúdo em um infoset XML.</span><span class="sxs-lookup"><span data-stu-id="05c3c-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="05c3c-249">Método</span><span class="sxs-lookup"><span data-stu-id="05c3c-249">Method</span></span>|<span data-ttu-id="05c3c-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="05c3c-250">GetExpectedParticles</span></span>|<span data-ttu-id="05c3c-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="05c3c-251">GetExpectedAttributes</span></span>|<span data-ttu-id="05c3c-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="05c3c-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="05c3c-253">Se o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> padrão é chamado, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz que contém todos os elementos globais.</span><span class="sxs-lookup"><span data-stu-id="05c3c-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="05c3c-254">Se o método sobrecarregado que leva <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> como um parâmetro é chamado para inicializar a validação parcial de um elemento, <xref:System.Xml.Schema.XmlSchemaObject> de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna somente o elemento ao qual o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="05c3c-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="05c3c-255">Se o método de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> padrão é chamado, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-256">Se a sobrecarga de método que usa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> como um parâmetro é chamado para inicializar a validação parcial de um atributo, <xref:System.Xml.Schema.XmlSchemaObject> de <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna somente o atributo para que o objeto de <xref:System.Xml.Schema.XmlSchemaValidator> foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="05c3c-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="05c3c-257">Adiciona o esquema a <xref:System.Xml.Schema.XmlSchemaSet> do objeto de <xref:System.Xml.Schema.XmlSchemaValidator> se não tem nenhum erro de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="05c3c-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="05c3c-258">Se o elemento de contexto é válido, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado como filhos do elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="05c3c-259">Se o elemento de contexto é inválido, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="05c3c-260">Se o elemento de contexto é válido, e se nenhuma chamada a <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> tiver sido feito anteriormente, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma lista de todos os atributos definidos no elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="05c3c-261">Se alguns atributos já foram validados, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma lista dos outros atributos a ser validados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="05c3c-262">Se o elemento de contexto é inválido, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="05c3c-263">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="05c3c-264">Se o atributo de contexto é um atributo de nível superior, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-265">Se não <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado como o primeiro filho do elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="05c3c-266">Se o atributo de contexto é um atributo de nível superior, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-267">Se não <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna a lista dos outros atributos a ser validados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="05c3c-268">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="05c3c-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado como o primeiro filho do elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="05c3c-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma lista de atributos necessários e opcionais que devem ser validados ainda para o elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="05c3c-271">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="05c3c-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado como o primeiro filho do elemento de contexto.</span><span class="sxs-lookup"><span data-stu-id="05c3c-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="05c3c-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="05c3c-274">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="05c3c-275">Se o contentType do elemento de contexto é misturado, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado na próxima posição.</span><span class="sxs-lookup"><span data-stu-id="05c3c-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="05c3c-276">Se o contentType do elemento de contexto é TextOnly ou Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-277">Se o contentType do elemento de contexto é ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado na próxima posição mas um erro de validação tem ocorreu.</span><span class="sxs-lookup"><span data-stu-id="05c3c-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="05c3c-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna a lista de elemento do contexto de atributos não validados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="05c3c-279">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="05c3c-280">Se o espaço em branco de contexto é o espaço em branco de nível superior, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-281">Se não o comportamento de método <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> é o mesmo que em <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="05c3c-282">Se o espaço em branco de contexto é o espaço em branco de nível superior, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="05c3c-283">Se não o comportamento de método <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> é o mesmo que em <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="05c3c-284">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="05c3c-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retorna a sequência de elementos esperado após o elemento de contexto (irmãos possíveis).</span><span class="sxs-lookup"><span data-stu-id="05c3c-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="05c3c-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna a lista de elemento do contexto de atributos não validados.</span><span class="sxs-lookup"><span data-stu-id="05c3c-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="05c3c-287">Se o elemento de contexto não tem nenhum pai em <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retorna uma lista vazia (o elemento de contexto é o pai do elemento atual em <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> que foi chamado.)</span><span class="sxs-lookup"><span data-stu-id="05c3c-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="05c3c-288">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="05c3c-289">Mesmo que <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="05c3c-290">Mesmo que <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="05c3c-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="05c3c-291">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="05c3c-292">Retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-292">Returns an empty array.</span></span>|<span data-ttu-id="05c3c-293">Retorna uma matriz vazia.</span><span class="sxs-lookup"><span data-stu-id="05c3c-293">Returns an empty array.</span></span>|<span data-ttu-id="05c3c-294">Mesmo que anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="05c3c-295">Os valores retornados por várias propriedades da classe de <xref:System.Xml.Schema.XmlSchemaValidator> não são alterados chamando os métodos na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="05c3c-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c3c-296">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05c3c-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
