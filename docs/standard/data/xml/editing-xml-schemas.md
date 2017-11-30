---
title: "Esquemas XML de edição"
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
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="bafb9-102">Esquemas XML de edição</span><span class="sxs-lookup"><span data-stu-id="bafb9-102">Editing XML Schemas</span></span>
<span data-ttu-id="bafb9-103">Editar um esquema XML é um dos recursos mais importantes do modelo de objeto (SOM) de esquema.</span><span class="sxs-lookup"><span data-stu-id="bafb9-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="bafb9-104">Todas as propriedades de pre-esquema- compilação de SOM podem ser usadas para alterar os valores existentes em um esquema XML.</span><span class="sxs-lookup"><span data-stu-id="bafb9-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="bafb9-105">O esquema XML pode então ser recompilado para refletir as alterações.</span><span class="sxs-lookup"><span data-stu-id="bafb9-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="bafb9-106">A primeira etapa em editar um esquema carregado no SOM é passar pelo esquema.</span><span class="sxs-lookup"><span data-stu-id="bafb9-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="bafb9-107">Você deve estar familiarizado com o atravessamento de um esquema usando o SOM API antes de tentar editar um esquema.</span><span class="sxs-lookup"><span data-stu-id="bafb9-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="bafb9-108">Você também deve estar familiarizado com as propriedades pré-compilação e de POST-esquema- compilação de POST-Esquema- compilação - Infoset (PSCI).</span><span class="sxs-lookup"><span data-stu-id="bafb9-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="bafb9-109">Editando um esquema XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="bafb9-110">Nesta seção, são fornecidos dois exemplos de código, que editar o esquema do cliente criado no [compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="bafb9-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="bafb9-111">O primeiro exemplo de código a seguir adiciona um novo elemento de `PhoneNumber` para o elemento de `Customer` e o segundo exemplo de código a seguir adiciona um novo atributo de `Title` para o elemento de `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="bafb9-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="bafb9-112">O primeiro exemplo também usa a coleção de <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de POST-esquema- compilação como os meios para percorrer o esquema de cliente quando o segundo exemplo de código usar a coleção de <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pre-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="bafb9-113">Exemplo do elemento de PhoneNumber</span><span class="sxs-lookup"><span data-stu-id="bafb9-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="bafb9-114">Isso primeiro exemplo de código a seguir adiciona um novo elemento de `PhoneNumber` para o elemento de `Customer` do cliente.</span><span class="sxs-lookup"><span data-stu-id="bafb9-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="bafb9-115">O exemplo de código editar o esquema de cliente nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="bafb9-115">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="bafb9-116">Adiciona o esquema de cliente a um novo objeto de <xref:System.Xml.Schema.XmlSchemaSet> e compilá-lo em seguida.</span><span class="sxs-lookup"><span data-stu-id="bafb9-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="bafb9-117">Todos os avisos de validação de esquema e leitura ou compilação encontrada erros o esquema são tratados pelo delegado de <xref:System.Xml.Schema.ValidationEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="bafb9-118">Recupera o objeto compilada de <xref:System.Xml.Schema.XmlSchema> de <xref:System.Xml.Schema.XmlSchemaSet> iterando sobre a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="bafb9-119">Porque o esquema é compilado, as propriedades de (PSCI) de POST-Esquema- compilação - Infoset são acessíveis.</span><span class="sxs-lookup"><span data-stu-id="bafb9-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="bafb9-120">Cria o elemento de `PhoneNumber` usando a classe de <xref:System.Xml.Schema.XmlSchemaElement> , a restrição de tipo simples de `xs:string` usando <xref:System.Xml.Schema.XmlSchemaSimpleType> e <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classe, adiciona um aspecto padrão da propriedade de <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> de restrição, e adicione a restrição à propriedade de <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> do tipo simples e de tipo simples a <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> do elemento de `PhoneNumber` .</span><span class="sxs-lookup"><span data-stu-id="bafb9-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4.  <span data-ttu-id="bafb9-121">Efetua iterações sobre cada <xref:System.Xml.Schema.XmlSchemaElement> na coleção de <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> de coleção de <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de POST-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5.  <span data-ttu-id="bafb9-122">Se <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> do elemento é `"Customer"`, obtém o tipo complexo do elemento de `Customer` usando a classe de <xref:System.Xml.Schema.XmlSchemaComplexType> e a partícula a sequência de tipo complexo usando a classe de <xref:System.Xml.Schema.XmlSchemaSequence> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6.  <span data-ttu-id="bafb9-123">Adicionar o novo elemento de `PhoneNumber` a sequência que contém `FirstName` e elementos existentes de `LastName` usando a coleção de <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> de pre-esquema- compilação de sequência.</span><span class="sxs-lookup"><span data-stu-id="bafb9-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7.  <span data-ttu-id="bafb9-124">Finalmente, reprocessa e cria o objeto modificado de <xref:System.Xml.Schema.XmlSchema> usando os métodos de <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> e de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> da classe de <xref:System.Xml.Schema.XmlSchemaSet> e grava no console.</span><span class="sxs-lookup"><span data-stu-id="bafb9-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="bafb9-125">A seguir está o exemplo de código completo.</span><span class="sxs-lookup"><span data-stu-id="bafb9-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="bafb9-126">A seguir está o esquema do cliente modificadas criado no [compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="bafb9-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
### <a name="title-attribute-example"></a><span data-ttu-id="bafb9-127">Exemplo de atributo de título</span><span class="sxs-lookup"><span data-stu-id="bafb9-127">Title Attribute Example</span></span>  
 <span data-ttu-id="bafb9-128">O segundo exemplo de código, adicione um novo atributo de `Title` para o elemento de `FirstName` do cliente.</span><span class="sxs-lookup"><span data-stu-id="bafb9-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="bafb9-129">No primeiro exemplo de código, o tipo de elemento de `FirstName` é `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="bafb9-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="bafb9-130">Para o elemento de `FirstName` tem um atributo juntamente com o conteúdo de cadeia de caracteres, seu tipo deve ser alterado para um tipo complexo com um modelo de conteúdo de conteúdo simples de extensão.</span><span class="sxs-lookup"><span data-stu-id="bafb9-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="bafb9-131">O exemplo de código editar o esquema de cliente nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="bafb9-131">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="bafb9-132">Adiciona o esquema de cliente a um novo objeto de <xref:System.Xml.Schema.XmlSchemaSet> e compilá-lo em seguida.</span><span class="sxs-lookup"><span data-stu-id="bafb9-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="bafb9-133">Todos os avisos de validação de esquema e leitura ou compilação encontrada erros o esquema são tratados pelo delegado de <xref:System.Xml.Schema.ValidationEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="bafb9-134">Recupera o objeto compilada de <xref:System.Xml.Schema.XmlSchema> de <xref:System.Xml.Schema.XmlSchemaSet> iterando sobre a propriedade de <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="bafb9-135">Porque o esquema é compilado, as propriedades de (PSCI) de POST-Esquema- compilação - Infoset são acessíveis.</span><span class="sxs-lookup"><span data-stu-id="bafb9-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="bafb9-136">Cria um novo tipo complexo para o elemento de `FirstName` usando a classe de <xref:System.Xml.Schema.XmlSchemaComplexType> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4.  <span data-ttu-id="bafb9-137">Cria uma nova extensão de conteúdo simples, com um tipo base de `xs:string`, usando as classes de <xref:System.Xml.Schema.XmlSchemaSimpleContent> e de <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5.  <span data-ttu-id="bafb9-138">Cria o novo atributo de `Title` usando a classe de <xref:System.Xml.Schema.XmlSchemaAttribute> , com <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> de `xs:string` e adicione o atributo a extensão de conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="bafb9-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6.  <span data-ttu-id="bafb9-139">Defina o modelo de conteúdo de conteúdo simples para a extensão de conteúdo simples e o modelo de conteúdo do tipo complexo para o conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="bafb9-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7.  <span data-ttu-id="bafb9-140">Adicionar o novo tipo complexo à coleção de <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pre-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8.  <span data-ttu-id="bafb9-141">Efetua iterações sobre cada <xref:System.Xml.Schema.XmlSchemaObject> na coleção de <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pre-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bafb9-142">Como o elemento de `FirstName` não é um elemento global no esquema, não está disponível em coleções de <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> ou de <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="bafb9-143">O exemplo de código posicionar o elemento de `FirstName` posicionando o primeiro elemento de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="bafb9-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="bafb9-144">O primeiro exemplo de código atravessou o esquema usando a coleção de <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> de POST-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="bafb9-145">Nesse exemplo, a coleção de <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> de pre-esquema- compilação é usada para percorrer o esquema.</span><span class="sxs-lookup"><span data-stu-id="bafb9-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="bafb9-146">Quando ambas as coleções fornecem acesso aos elementos globais no esquema, iterar através da coleção de <xref:System.Xml.Schema.XmlSchema.Items%2A> é mais demorado porque você deve iterar todos os elementos globais no esquema e não tem nenhuma propriedades de PSCI.</span><span class="sxs-lookup"><span data-stu-id="bafb9-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="bafb9-147">Coleções de PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, e assim por diante) fornecem acesso direto a seus elementos, atributos globais, tipos e suas propriedades de PSCI.</span><span class="sxs-lookup"><span data-stu-id="bafb9-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1.  <span data-ttu-id="bafb9-148">Se <xref:System.Xml.Schema.XmlSchemaObject> é um elemento, cujo <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> é `"Customer"`, obtém o tipo complexo do elemento de `Customer` usando a classe de <xref:System.Xml.Schema.XmlSchemaComplexType> e a partícula a sequência de tipo complexo usando a classe de <xref:System.Xml.Schema.XmlSchemaSequence> .</span><span class="sxs-lookup"><span data-stu-id="bafb9-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2.  <span data-ttu-id="bafb9-149">Efetua iterações sobre cada <xref:System.Xml.Schema.XmlSchemaParticle> na coleção de <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> de pre-esquema- compilação.</span><span class="sxs-lookup"><span data-stu-id="bafb9-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="bafb9-150">Se <xref:System.Xml.Schema.XmlSchemaParticle> é um elemento, que é <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> é `"FirstName"`, define <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> do elemento de `FirstName` para o novo tipo complexo de `FirstName` .</span><span class="sxs-lookup"><span data-stu-id="bafb9-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4.  <span data-ttu-id="bafb9-151">Finalmente, reprocessa e cria o objeto modificado de <xref:System.Xml.Schema.XmlSchema> usando os métodos de <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> e de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> da classe de <xref:System.Xml.Schema.XmlSchemaSet> e grava no console.</span><span class="sxs-lookup"><span data-stu-id="bafb9-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="bafb9-152">A seguir está o exemplo de código completo.</span><span class="sxs-lookup"><span data-stu-id="bafb9-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="bafb9-153">A seguir está o esquema do cliente modificadas criado no [compilando esquemas XML](../../../../docs/standard/data/xml/building-xml-schemas.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="bafb9-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bafb9-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bafb9-154">See Also</span></span>  
 [<span data-ttu-id="bafb9-155">Visão geral de modelo de objeto de esquema XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="bafb9-156">Lendo e gravando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="bafb9-157">Compilando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="bafb9-158">Percorrer esquemas XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="bafb9-159">Incluindo ou importando esquemas XML</span><span class="sxs-lookup"><span data-stu-id="bafb9-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="bafb9-160">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="bafb9-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="bafb9-161">Pós-esquema de compilação Infoset</span><span class="sxs-lookup"><span data-stu-id="bafb9-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
