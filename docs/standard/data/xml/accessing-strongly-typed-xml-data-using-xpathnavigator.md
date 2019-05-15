---
title: Acessando dados fortemente tipados XML usando XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bc33d27d48267f5b74f1baf67a49bdf0b55c839
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647981"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="5624c-102">Acessando dados fortemente tipados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5624c-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="5624c-103">Como uma instância do modelo de dados XPath 2,0, a classe de <xref:System.Xml.XPath.XPathNavigator> pode conter dados fortemente tipados que mapeiam a Common Language Runtime (CLR) tipos.</span><span class="sxs-lookup"><span data-stu-id="5624c-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="5624c-104">De acordo com o modelo de dados XPath 2,0, somente os elementos e atributos podem conter dados fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="5624c-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="5624c-105">A classe de <xref:System.Xml.XPath.XPathNavigator> fornece mecanismos para acessar dados em um objeto de <xref:System.Xml.XPath.XPathDocument> ou de <xref:System.Xml.XmlDocument> como dados fortemente tipados bem como mecanismos para converter de um tipo de dados para outro.</span><span class="sxs-lookup"><span data-stu-id="5624c-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="5624c-106">Informações de tipo expostos por XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5624c-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="5624c-107">XML 1,0 dados é tecnicamente sem tipo, a menos que processado com um DTD, o esquema de linguagem de definição de esquema XML (XSD), ou outro mecanismo.</span><span class="sxs-lookup"><span data-stu-id="5624c-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="5624c-108">Há um número de categorias das informações que podem ser associadas com um elemento XML ou um atributo.</span><span class="sxs-lookup"><span data-stu-id="5624c-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="5624c-109">Tipos CLR simples: Nenhuma linguagem de Esquema XML dá suporte a tipos CLR (Common Language Runtime) diretamente.</span><span class="sxs-lookup"><span data-stu-id="5624c-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="5624c-110">Porque é útil poder exibir conteúdo simples de elementos e atributos porque os a maioria exibe o tipo de CLR, todo o conteúdo simples pode ser digitado como <xref:System.String> na ausência de informações de esquema com qualquer adicionadas informações de esquema que limita potencialmente esse conteúdo a um tipo apropriado.</span><span class="sxs-lookup"><span data-stu-id="5624c-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="5624c-111">Você pode localizar o melhor tipo correspondente de CLR de conteúdo simples de elementos e atributos usando a propriedade de <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> .</span><span class="sxs-lookup"><span data-stu-id="5624c-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="5624c-112">Para saber mais sobre o mapeamento de tipos internos de esquema para tipos de CLR, confira [Suporte a tipo nas classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5624c-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="5624c-113">Listas de tipos (CLR) simples: Um elemento ou um atributo com conteúdo simples pode conter uma lista de valores separados por espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="5624c-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="5624c-114">Os valores são especificados por um esquema XML para ser de um tipo “lista.”</span><span class="sxs-lookup"><span data-stu-id="5624c-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="5624c-115">Na ausência de um esquema XML, tal conteúdo simples seria tratado como um único nó de texto.</span><span class="sxs-lookup"><span data-stu-id="5624c-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="5624c-116">Quando um esquema XML está disponível, esse conteúdo simples pode ser exposta como uma série de valores atômicos cada um que tenha um tipo simples que mapeia a uma coleção de objetos CLR.</span><span class="sxs-lookup"><span data-stu-id="5624c-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="5624c-117">Para saber mais sobre o mapeamento de tipos internos de esquema para tipos de CLR, confira [Suporte a tipo nas classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5624c-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="5624c-118">Valor tipado: Um atributo ou um elemento validado por esquema com um tipo simples tem um valor tipado.</span><span class="sxs-lookup"><span data-stu-id="5624c-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="5624c-119">Esse valor é um tipo primitivo como um numérico, uma cadeia de caracteres, ou um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="5624c-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="5624c-120">Todos os tipos simples internos em XSD podem ser mapeados para os tipos de CLR de que fornece acesso ao valor de um nó como um tipo mais apropriado em vez de apenas como <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5624c-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="5624c-121">Um elemento com atributos ou filhos do elemento é considerado ser um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="5624c-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="5624c-122">O valor tipado de um tipo complexo com conteúdo simples (somente os nós de texto como filhos) é o mesmo que o do tipo simples de seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5624c-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="5624c-123">O valor tipado de um tipo complexo com conteúdo complexo (um ou mais elementos filho) é o valor da cadeia de caracteres de concatenação de todos os nós filhos de texto retornados como <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5624c-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="5624c-124">Para saber mais sobre o mapeamento de tipos internos de esquema para tipos de CLR, confira [Suporte a tipo nas classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5624c-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="5624c-125">Nome de tipo específico da linguagem de esquema: Na maioria dos casos, os tipos CLR, definidos como um efeito colateral da aplicação de um esquema externo, são usados para fornecer acesso ao valor de um nó.</span><span class="sxs-lookup"><span data-stu-id="5624c-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="5624c-126">No entanto, pode haver situações onde você pode querer examinar o tipo associado com um esquema específico aplicado a um documento XML.</span><span class="sxs-lookup"><span data-stu-id="5624c-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="5624c-127">Por exemplo, você pode desejar pesquisar por um documento XML, extraindo todos os elementos que são determinados ter o conteúdo do tipo “PurchaseOrder” de acordo com o esquema anexado.</span><span class="sxs-lookup"><span data-stu-id="5624c-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="5624c-128">Essas informações de tipo pode ser definida somente como resultado de validação de esquema e essa informação é acessada com <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> e as propriedades de <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de <xref:System.Xml.XPath.XPathNavigator> classe.</span><span class="sxs-lookup"><span data-stu-id="5624c-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="5624c-129">Para obter mais informações, consulte a seção de Infoset (PSVI) de validação do esquema de postagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="5624c-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="5624c-130">Reflexão de tipo específico da linguagem de esquema: Em outros casos, talvez você deseje obter mais detalhes do tipo específico do esquema aplicado a um documento XML.</span><span class="sxs-lookup"><span data-stu-id="5624c-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="5624c-131">Por exemplo, ao ler um arquivo XML, você pode querer extrair o atributo de `maxOccurs` para cada nó válido no documento XML para executar um cálculo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5624c-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="5624c-132">Porque essa informação é definida apenas com a validação do esquema, é acessada através da propriedade de <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="5624c-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="5624c-133">Para obter mais informações, consulte a seção de Infoset (PSVI) de validação do esquema de postagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="5624c-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="5624c-134">XPathNavigator digitou acessadores</span><span class="sxs-lookup"><span data-stu-id="5624c-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="5624c-135">A tabela a seguir mostra as várias propriedades e métodos de <xref:System.Xml.XPath.XPathNavigator> classe que pode ser usado para acessar informações de tipo sobre um nó.</span><span class="sxs-lookup"><span data-stu-id="5624c-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="5624c-136">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5624c-136">Property</span></span>|<span data-ttu-id="5624c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="5624c-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="5624c-138">Isso contém informações de tipo o esquema XML para o nó se é válido.</span><span class="sxs-lookup"><span data-stu-id="5624c-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="5624c-139">Isso contém a validação Infoset do esquema de postagem de nó que é adicionado após a validação.</span><span class="sxs-lookup"><span data-stu-id="5624c-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="5624c-140">Isso inclui informações de tipo do esquema XML, bem como informações de validade.</span><span class="sxs-lookup"><span data-stu-id="5624c-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="5624c-141">O tipo de CLR de valor tipado de nó.</span><span class="sxs-lookup"><span data-stu-id="5624c-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="5624c-142">O conteúdo do nó como um ou mais valores de CLR cujo tipo é mais próximo correspondente ao tipo de esquema XML de nó.</span><span class="sxs-lookup"><span data-stu-id="5624c-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="5624c-143">O valor de <xref:System.String> de conversão atual do nó com um valor de <xref:System.Boolean> , de acordo com o XPath 2,0 regras para converter `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="5624c-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="5624c-144">O valor de <xref:System.String> de conversão atual do nó com um valor de <xref:System.DateTime> , de acordo com o XPath 2,0 regras para converter `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="5624c-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="5624c-145">O valor de <xref:System.String> de conversão atual do nó com um valor de <xref:System.Double> , de acordo com o XPath 2,0 regras para converter `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="5624c-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="5624c-146">O valor de <xref:System.String> de conversão atual do nó com um valor de <xref:System.Int32> , de acordo com o XPath 2,0 regras para converter `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="5624c-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="5624c-147">O valor de <xref:System.String> de conversão atual do nó com um valor de <xref:System.Int64> , de acordo com o XPath 2,0 regras para converter `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="5624c-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="5624c-148">O conteúdo do nó convertem ao tipo de destino de acordo com o XPath 2,0 regras converter.</span><span class="sxs-lookup"><span data-stu-id="5624c-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="5624c-149">Para saber mais sobre o mapeamento de tipos internos de esquema para tipos de CLR, confira [Suporte a tipo nas classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5624c-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="5624c-150">A validação Infoset (PSVI) do esquema de postagem</span><span class="sxs-lookup"><span data-stu-id="5624c-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="5624c-151">Um processador XML de esquema XML Infoset aceita como entrada e o converte em uma validação Infoset (PSVI) do esquema de postagem.</span><span class="sxs-lookup"><span data-stu-id="5624c-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="5624c-152">Um PSVI é o infoset original XML de entrada com novos elementos de informações adicionados e as novas propriedades adicionadas a elementos existentes de informações.</span><span class="sxs-lookup"><span data-stu-id="5624c-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="5624c-153">Há três classes de informações de adicionadas a Infoset XML em PSVI que são expostos por <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="5624c-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="5624c-154">Resultados da validação: Informações referentes a se um elemento ou um atributo foi ou não bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="5624c-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="5624c-155">Isso expõe a propriedade de <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> de propriedade de <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="5624c-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="5624c-156">Informações padrão: Indicações referentes a se o valor do elemento ou do atributo foi obtido ou não por meio dos valores padrão especificados no esquema.</span><span class="sxs-lookup"><span data-stu-id="5624c-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="5624c-157">Isso expõe a propriedade de <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> de propriedade de <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="5624c-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="5624c-158">Anotações de tipo: Referências a componentes do esquema que podem ser definições de tipo ou declarações de elemento e atributo.</span><span class="sxs-lookup"><span data-stu-id="5624c-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="5624c-159">A propriedade de <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> de <xref:System.Xml.XPath.XPathNavigator> contém informações de tipo específico de nó se é válido.</span><span class="sxs-lookup"><span data-stu-id="5624c-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="5624c-160">Se a validade de um nó é desconhecida, como quando ele foi validado em editou posteriormente.</span><span class="sxs-lookup"><span data-stu-id="5624c-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="5624c-161">a propriedade de <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> é definida na `null` mas informações de tipo está disponível ainda das várias propriedades de propriedade de <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> da classe de <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="5624c-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="5624c-162">O exemplo a seguir ilustra usando as informações na validação Infoset do esquema de postagem expostos por <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="5624c-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="5624c-163">O exemplo usa o arquivo `books.xml` como entrada.</span><span class="sxs-lookup"><span data-stu-id="5624c-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="5624c-164">O exemplo também usa o esquema de `books.xsd` como entrada.</span><span class="sxs-lookup"><span data-stu-id="5624c-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"   
attributeFormDefault="unqualified" elementFormDefault="qualified"   
targetNamespace="http://www.contoso.com/books"   
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="5624c-165">Obtenha valores tipados usando propriedades de ValueAs</span><span class="sxs-lookup"><span data-stu-id="5624c-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="5624c-166">O valor tipado de um nó pode ser recuperado acessando a propriedade de <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="5624c-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="5624c-167">Em alguns casos você pode querer converter o valor tipado de um nó para um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="5624c-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="5624c-168">Um exemplo comum é obter um valor numérico de um nó XML.</span><span class="sxs-lookup"><span data-stu-id="5624c-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="5624c-169">Por exemplo, considere o seguinte documento XML unvalidated e sem tipo.</span><span class="sxs-lookup"><span data-stu-id="5624c-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="5624c-170">Se <xref:System.Xml.XPath.XPathNavigator> é posicionado no elemento de `price` a propriedade de <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> seria `null`, a propriedade de <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> seria <xref:System.String>, e a propriedade <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> seria a cadeia de caracteres `10.00`.</span><span class="sxs-lookup"><span data-stu-id="5624c-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="5624c-171">No entanto, ainda é possível extrair o valor como um valor numérico usando <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, ou métodos e propriedades de <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> .</span><span class="sxs-lookup"><span data-stu-id="5624c-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="5624c-172">O exemplo a seguir ilustra executar uma conversão usando o método <xref:System.Xml.XPath.XPathItem.ValueAs%2A> .</span><span class="sxs-lookup"><span data-stu-id="5624c-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="5624c-173">Para saber mais sobre o mapeamento de tipos internos de esquema para tipos de CLR, confira [Suporte a tipo nas classes System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5624c-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5624c-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5624c-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- <span data-ttu-id="5624c-175">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md) (Suporte a tipo nas classes System.XML)</span><span class="sxs-lookup"><span data-stu-id="5624c-175">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>
- [<span data-ttu-id="5624c-176">Processar dados XML usando o modelo de dados XPath</span><span class="sxs-lookup"><span data-stu-id="5624c-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="5624c-177">Navegação do nó usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5624c-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="5624c-178">Navegação do nó de atributo e de namespace usando o XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5624c-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="5624c-179">Extrair dados XML usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5624c-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
