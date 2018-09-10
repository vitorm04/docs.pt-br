---
title: Compilando esquemas XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197336"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="72782-102">Compilando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="72782-102">Building XML Schemas</span></span>
<span data-ttu-id="72782-103">As classes no namespace <xref:System.Xml.Schema?displayProperty=nameWithType> mapeiam para as estruturas definidas na recomendação do W3C (World Wide Web Consortium) sobre esquemas XML e podem ser usadas para compilar esquemas XML na memória.</span><span class="sxs-lookup"><span data-stu-id="72782-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="72782-104">Compilando um esquema XML</span><span class="sxs-lookup"><span data-stu-id="72782-104">Building an XML Schema</span></span>  
 <span data-ttu-id="72782-105">Nos exemplos de código a seguir, a API do SOM é usada para compilar um esquema XML cliente na memória.</span><span class="sxs-lookup"><span data-stu-id="72782-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="72782-106">Criando o elemento e os atributos</span><span class="sxs-lookup"><span data-stu-id="72782-106">Creating Element and Attributes</span></span>  
 <span data-ttu-id="72782-107">Os exemplos de código compilam o esquema cliente de baixo para cima, criando primeiro elementos e atributos filho, bem como seus tipos correspondentes, e depois os elementos de nível superior.</span><span class="sxs-lookup"><span data-stu-id="72782-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="72782-108">No exemplo de código a seguir, os elementos `FirstName` e `LastName`, bem como o atributo `CustomerId` do esquema cliente são criados usando as classes <xref:System.Xml.Schema.XmlSchemaElement> e <xref:System.Xml.Schema.XmlSchemaAttribute> do SOM.</span><span class="sxs-lookup"><span data-stu-id="72782-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="72782-109">Com exceção das propriedades <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> das classes <xref:System.Xml.Schema.XmlSchemaElement> e <xref:System.Xml.Schema.XmlSchemaAttribute>, que correspondem ao atributo "name" dos elementos `<xs:element />` e `<xs:attribute />` em um esquema XML, todos os outros atributos permitidos pelo esquema (`defaultValue`, `fixedValue`, `form` e assim por diante) têm propriedades correspondentes nas classes <xref:System.Xml.Schema.XmlSchemaElement> e <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="72782-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="72782-110">Criando tipos de esquema</span><span class="sxs-lookup"><span data-stu-id="72782-110">Creating Schema Types</span></span>  
 <span data-ttu-id="72782-111">O conteúdo de elementos e de atributos é definido pelos respectivos tipos.</span><span class="sxs-lookup"><span data-stu-id="72782-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="72782-112">Para criar elementos e atributos cujos tipos são um dos tipos internos do esquema, a propriedade <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> das classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> são definidas com o nome qualificado correspondente do tipo interno usando a classe <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="72782-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="72782-113">Para criar um tipo definido pelo usuário de elementos e atributos, um novo tipo simples ou complexo é criado usando a classe <xref:System.Xml.Schema.XmlSchemaSimpleType> ou <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="72782-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72782-114">Para criar tipos simples ou complexos sem nome que sejam filhos anônimos de um elemento ou atributo (somente os tipos simples são aplicáveis a atributos), defina a propriedade <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> das classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute> como o tipo simples ou complexo sem nome, em vez da propriedade <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> das classes <xref:System.Xml.Schema.XmlSchemaElement> ou <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="72782-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="72782-115">Os esquemas XML permitem que tipos simples, anônimos e nomeados, sejam derivados pela restrição de outros tipos simples (internos ou definidos pelo usuário) ou construídos como uma lista ou união de outros tipos simples.</span><span class="sxs-lookup"><span data-stu-id="72782-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="72782-116">A classe <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> é usada para criar um tipo simples restringindo o tipo interno `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="72782-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="72782-117">Você também pode usar as classes <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> ou <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> para criar tipos de lista ou de união.</span><span class="sxs-lookup"><span data-stu-id="72782-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="72782-118">A propriedade <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> indica se é uma união, uma lista ou uma restrição de tipos simples.</span><span class="sxs-lookup"><span data-stu-id="72782-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="72782-119">No exemplo de código a seguir, o tipo do elemento `FirstName` é o tipo interno `xs:string`, o tipo do elemento `LastName` é um tipo simples nomeado que é uma restrição do tipo interno `xs:string`, com um valor de faceta `MaxLength` igual a 20, e o tipo do atributo `CustomerId` é o tipo interno `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="72782-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="72782-120">O elemento `Customer` é um tipo complexo anônimo cuja partícula é a sequência dos elementos `FirstName` e `LastName` e cujos atributos contêm o atributo `CustomerId`.</span><span class="sxs-lookup"><span data-stu-id="72782-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72782-121">Você também pode usar as classes <xref:System.Xml.Schema.XmlSchemaChoice> ou <xref:System.Xml.Schema.XmlSchemaAll> como partícula do tipo complexo para replicar as semânticas `<xs:choice />` ou `<xs:all />`.</span><span class="sxs-lookup"><span data-stu-id="72782-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="72782-122">Criando e compilando esquemas</span><span class="sxs-lookup"><span data-stu-id="72782-122">Creating and Compiling Schemas</span></span>  
 <span data-ttu-id="72782-123">Neste ponto, os elementos e atributos filho, seus tipos correspondentes e o elemento de nível superior `Customer` foram criados na memória usando a API do SOM.</span><span class="sxs-lookup"><span data-stu-id="72782-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="72782-124">No exemplo de código a seguir, o elemento de esquema é criado usando a classe <xref:System.Xml.Schema.XmlSchema>, os elementos e os tipos de nível superior são adicionados a ele usando a propriedade <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> e o esquema completo é compilado usando a classe <xref:System.Xml.Schema.XmlSchemaSet> e criado no console.</span><span class="sxs-lookup"><span data-stu-id="72782-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="72782-125">O método <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> valida o esquema cliente em relação às regras de um esquema XML e disponibiliza as propriedades de pós-compilação de esquema.</span><span class="sxs-lookup"><span data-stu-id="72782-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72782-126">Todas as propriedades de pós-compilação de esquema na API do SOM diferem do conjunto de informações de pós-validação de esquema.</span><span class="sxs-lookup"><span data-stu-id="72782-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="72782-127">O objeto <xref:System.Xml.Schema.ValidationEventHandler> adicionado à classe <xref:System.Xml.Schema.XmlSchemaSet> é um delegado que chama o método de retorno de chamada `ValidationCallback` para tratar avisos e erros de validação de esquema.</span><span class="sxs-lookup"><span data-stu-id="72782-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="72782-128">Veja a seguir o exemplo de código completo e o esquema cliente criado no console.</span><span class="sxs-lookup"><span data-stu-id="72782-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72782-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72782-129">See also</span></span>

- [<span data-ttu-id="72782-130">Visão geral de modelo de objeto de esquema XML</span><span class="sxs-lookup"><span data-stu-id="72782-130">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [<span data-ttu-id="72782-131">Lendo e gravando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="72782-131">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [<span data-ttu-id="72782-132">Percorrer esquemas XML</span><span class="sxs-lookup"><span data-stu-id="72782-132">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [<span data-ttu-id="72782-133">Edição de esquemas XML</span><span class="sxs-lookup"><span data-stu-id="72782-133">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [<span data-ttu-id="72782-134">Incluindo ou importando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="72782-134">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [<span data-ttu-id="72782-135">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="72782-135">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [<span data-ttu-id="72782-136">Infoset de compilação pós-esquema</span><span class="sxs-lookup"><span data-stu-id="72782-136">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
