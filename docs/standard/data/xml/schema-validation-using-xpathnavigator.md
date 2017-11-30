---
title: "Validação de esquema usando XPathNavigator"
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
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91ad5c2e6f8af7f2c3709b9dff65bd728de08e5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="0ed7d-102">Validação de esquema usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0ed7d-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="0ed7d-103">Se você usar a classe <xref:System.Xml.XmlDocument>, poderá validar o conteúdo XML contido em um objeto <xref:System.Xml.XmlDocument> de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="0ed7d-104">A primeira maneira é validar o conteúdo XML usando um objeto <xref:System.Xml.XmlReader> de validação, e a segunda maneira é usar o método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0ed7d-105">Você também pode executar a validação somente leitura do conteúdo XML usando a classe <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="0ed7d-106">Validando dados XML</span><span class="sxs-lookup"><span data-stu-id="0ed7d-106">Validating XML Data</span></span>  
 <span data-ttu-id="0ed7d-107">A classe <xref:System.Xml.XmlDocument> não valida um documento XML usando validação de esquema DTD nem XSD (linguagem de definição de esquema XML) por padrão.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="0ed7d-108">Ela só verifica se o documento XML está bem-formado.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="0ed7d-109">A primeira maneira de validar um documento XML é validar o documento enquanto ele é carregado para um objeto <xref:System.Xml.XmlDocument> usando um objeto <xref:System.Xml.XmlReader> de validação.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0ed7d-110">A segunda maneira é validar um documento XML anteriormente não tipado usando o método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0ed7d-111">Nos dois casos, as alterações no documento XML validado podem ser revalidadas usando o método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="0ed7d-112">Validando um documento enquanto ele é carregado</span><span class="sxs-lookup"><span data-stu-id="0ed7d-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="0ed7d-113">Um objeto <xref:System.Xml.XmlReader> de validação é criado passando um objeto <xref:System.Xml.XmlReaderSettings> para o método <xref:System.Xml.XmlReader.Create%2A> da classe <xref:System.Xml.XmlReader> que usa um objeto <xref:System.Xml.XmlReaderSettings> como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="0ed7d-114">O objeto <xref:System.Xml.XmlReaderSettings> passado como parâmetro tem uma propriedade <xref:System.Xml.XmlReaderSettings.ValidationType%2A> definida como `Schema` e um esquema XML para o documento XML contido no objeto <xref:System.Xml.XmlDocument> adicionado à sua propriedade <xref:System.Xml.XmlReaderSettings.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="0ed7d-115">O objeto <xref:System.Xml.XmlReader> de validação é usado para criar o objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="0ed7d-116">O exemplo a seguir valida o arquivo `contosoBooks.xml` enquanto ele é carregado para o objeto <xref:System.Xml.XmlDocument> criando o objeto <xref:System.Xml.XmlDocument> que usa um objeto <xref:System.Xml.XmlReader> de validação.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0ed7d-117">Como o documento XML é válido de acordo com o esquema, nenhum erro ou aviso de validação de esquema é gerado.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0ed7d-118">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0ed7d-119">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="0ed7d-120">No exemplo acima, uma <xref:System.Xml.Schema.XmlSchemaValidationException> será gerado quando <xref:System.Xml.XmlDocument.Load%2A> for chamado se nenhum tipo de atributo ou de elemento corresponder ao tipo correspondente especificado no esquema de validação.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="0ed7d-121">Se um <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> não for definido no objeto <xref:System.Xml.XmlReader> de validação, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> será chamado sempre que um tipo inválido for localizado.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="0ed7d-122">Uma <xref:System.Xml.Schema.XmlSchemaException> será gerada quando um atributo ou um elemento com <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> definido como `invalid` for acessado pela classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="0ed7d-123">A propriedade <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> pode ser usada para determinar se um atributo ou um elemento individual é válido para acessar atributos ou elementos com a classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ed7d-124">Quando um documento XML é carregado para um objeto <xref:System.Xml.XmlDocument> com um esquema associado que define os valores padrão, o objeto <xref:System.Xml.XmlDocument> trata esses padrões como se eles tivessem aparecido no documento XML.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="0ed7d-125">Isso significa que a propriedade <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> sempre retorna `false` para um elemento do esquema que é usado como padrão, mesmo se o documento XML tiver sido criado como um elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="0ed7d-126">Validando um documento com o método Validate</span><span class="sxs-lookup"><span data-stu-id="0ed7d-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="0ed7d-127">O método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument> valida o documento XML contido em um objeto <xref:System.Xml.XmlDocument> em relação aos esquemas especificados na propriedade <xref:System.Xml.XmlDocument> do objeto <xref:System.Xml.XmlDocument.Schemas%2A> e executa o aumento do conjunto de informações.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="0ed7d-128">O resultado é um documento XML anteriormente não tipado no objeto <xref:System.Xml.XmlDocument> substituído por um documento tipado.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="0ed7d-129">O objeto <xref:System.Xml.XmlDocument> relata erros e avisos de validação do esquema de relatórios que usa o delegado <xref:System.Xml.Schema.ValidationEventHandler> passado como parâmetro para o método <xref:System.Xml.XmlDocument.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="0ed7d-130">O exemplo a seguir valida o arquivo `contosoBooks.xml` contido no objeto <xref:System.Xml.XmlDocument> em relação ao esquema `contosoBooks.xsd` contido na propriedade <xref:System.Xml.XmlDocument> do objeto <xref:System.Xml.XmlDocument.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0ed7d-131">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0ed7d-132">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="0ed7d-133">Validando modificações</span><span class="sxs-lookup"><span data-stu-id="0ed7d-133">Validating Modifications</span></span>  
 <span data-ttu-id="0ed7d-134">Depois que as alterações são feitas em um documento XML, você pode validar as modificações em relação ao esquema do documento XML usando o método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="0ed7d-135">O exemplo a seguir valida o arquivo `contosoBooks.xml` enquanto ele é carregado para o objeto <xref:System.Xml.XmlDocument> criando o objeto <xref:System.Xml.XmlDocument> que usa um objeto <xref:System.Xml.XmlReader> de validação.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0ed7d-136">O documento XML é validado com êxito enquanto é carregado sem gerar erros nem avisos de validação de esquema.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="0ed7d-137">Em seguida, o exemplo faz duas modificações no documento XML que são inválidas de acordo com o esquema `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="0ed7d-138">A primeira modificação insere um elemento filho inválido que resulta em um erro de validação de esquema, e a segunda modificação define o valor de um nó tipado como um valor inválido de acordo com o tipo de nó que resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0ed7d-139">O exemplo usa o arquivo `contosoBooks.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0ed7d-140">O exemplo também usa `contosoBooks.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="0ed7d-141">No exemplo anterior, duas modificações são feitas no documento XML contido no objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0ed7d-142">Enquanto o documento XML era carregado, todos os erros de validação de esquema encontrados teriam sido tratados pelo método de manipulador de eventos de validação e gravados no console.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="0ed7d-143">Neste exemplo, os erros de validação foram introduzidos após o documento XML ser carregado e foram encontrados usando o método <xref:System.Xml.XmlDocument.Validate%2A> da classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="0ed7d-144">As modificações feitas usando o método <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> da classe <xref:System.Xml.XPath.XPathNavigator> resultaram em uma <xref:System.InvalidCastException> porque o novo valor era inválido de acordo com o tipo do nó de esquema.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="0ed7d-145">Para obter mais informações sobre como modificar valores usando o <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> método, consulte o [modificar dados XML usando XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="0ed7d-146">Validação somente leitura</span><span class="sxs-lookup"><span data-stu-id="0ed7d-146">Read-Only Validation</span></span>  
 <span data-ttu-id="0ed7d-147">A classe <xref:System.Xml.XPath.XPathDocument> é uma representação somente leitura na memória de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="0ed7d-148">As classes <xref:System.Xml.XPath.XPathDocument> e <xref:System.Xml.XmlDocument> criam objetos <xref:System.Xml.XPath.XPathNavigator> para navegar em documentos XML e editá-los.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="0ed7d-149">Como a classe <xref:System.Xml.XPath.XPathDocument> é uma classe somente leitura, o objeto <xref:System.Xml.XPath.XPathNavigator> retornado de objetos <xref:System.Xml.XPath.XPathDocument> não pode editar o documento XML contido no objeto <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="0ed7d-150">No caso de validação, você pode criar um objeto <xref:System.Xml.XPath.XPathDocument> da mesma forma como cria um objeto <xref:System.Xml.XmlDocument> usando um objeto <xref:System.Xml.XmlReader> de validação, como descrito anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="0ed7d-151">O objeto <xref:System.Xml.XPath.XPathDocument> valida o documento XML enquanto ele é carregado, mas, como não é possível editar os dados XML no objeto <xref:System.Xml.XPath.XPathDocument>, você não pode revalidar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="0ed7d-152">Para obter mais informações sobre como somente leitura e editável <xref:System.Xml.XPath.XPathNavigator> objetos, consulte o [leitura de dados XML usando XPathDocument e XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="0ed7d-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed7d-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ed7d-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="0ed7d-154">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="0ed7d-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="0ed7d-155">Lendo dados XML usando XPathDocument e XmlDocument</span><span class="sxs-lookup"><span data-stu-id="0ed7d-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="0ed7d-156">Selecionando, avaliando e correspondente de dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0ed7d-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="0ed7d-157">Acessando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0ed7d-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="0ed7d-158">Editando dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0ed7d-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
