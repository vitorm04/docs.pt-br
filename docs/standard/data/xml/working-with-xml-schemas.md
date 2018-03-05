---
title: Trabalhando com esquemas XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cba66a0d8291592b082898d20ca780c8067401e
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="f9e68-102">Trabalhando com esquemas XML</span><span class="sxs-lookup"><span data-stu-id="f9e68-102">Working with XML Schemas</span></span>
<span data-ttu-id="f9e68-103">Para definir a estrutura de um documento XML, bem como os relacionamentos de seus elementos, tipos de dados e restrições de conteúdo, você usa uma DTD (definição de tipo de documento) ou um esquema XSD (linguagem de definição de esquema XML).</span><span class="sxs-lookup"><span data-stu-id="f9e68-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="f9e68-104">Embora um documento XML seja considerado bem-formado se atender a todos os requisitos sintáticos definidos pela Recomendação da linguagem XML 1.0 do W3C (World Wide Web Consortium), ele não é considerado válido a menos que seja bem-formado e esteja de acordo com as restrições definidas pela DTD ou o esquema.</span><span class="sxs-lookup"><span data-stu-id="f9e68-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="f9e68-105">Portanto, embora todos os documentos XML válidos sejam bem-formados, nem todos os documentos XML bem-formados são válidos.</span><span class="sxs-lookup"><span data-stu-id="f9e68-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="f9e68-106">Para saber mais sobre o XML, confira a [Recomendação W3C XML 1.0](https://www.w3.org/TR/REC-xml/).</span><span class="sxs-lookup"><span data-stu-id="f9e68-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="f9e68-107">Para saber mais sobre o esquema XML, confira as recomendações [Parte 1 do Esquema W3C XML: recomendação de estruturas](https://www.w3.org/TR/xmlschema-1/) e a [Parte 2 do Esquema W3C XML: recomendação de tipos de dados](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="f9e68-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9e68-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f9e68-108">In This Section</span></span>  
 <span data-ttu-id="f9e68-109">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]</span><span class="sxs-lookup"><span data-stu-id="f9e68-109">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>  
 <span data-ttu-id="f9e68-110">Discute o SOM (Schema Object Model) no namespace <xref:System.Xml.Schema?displayProperty=nameWithType> que fornece um conjunto de classes que permitem que você leia um esquema XSD (linguagem de definição de esquema XML) em um arquivo ou crie programaticamente um esquema na memória.</span><span class="sxs-lookup"><span data-stu-id="f9e68-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="f9e68-111">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="f9e68-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="f9e68-112">Discute a classe <xref:System.Xml.Schema.XmlSchemaSet> que é um cache onde os esquemas XSD podem ser armazenados e validados.</span><span class="sxs-lookup"><span data-stu-id="f9e68-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="f9e68-113">Validação baseada em push do XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="f9e68-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="f9e68-114">Discute a classe <xref:System.Xml.Schema.XmlSchemaValidator>, que fornece um mecanismo eficiente e de alto desempenho para validar dados XML em esquemas XSD de uma maneira baseada em push.</span><span class="sxs-lookup"><span data-stu-id="f9e68-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="f9e68-115">Inferindo um esquema XML</span><span class="sxs-lookup"><span data-stu-id="f9e68-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="f9e68-116">Discute como usar a classe <xref:System.Xml.Schema.XmlSchemaInference> para inferir um esquema XSD na estrutura de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="f9e68-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9e68-117">Referência</span><span class="sxs-lookup"><span data-stu-id="f9e68-117">Reference</span></span>  
 <span data-ttu-id="f9e68-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="f9e68-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9e68-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f9e68-119">Related Sections</span></span>  
 [<span data-ttu-id="f9e68-120">Validando um documento XML no DOM</span><span class="sxs-lookup"><span data-stu-id="f9e68-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="f9e68-121">Discute como validar o XML no DOM (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="f9e68-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="f9e68-122">Você pode validar o XML como é carregado no DOM ou validar um documento XML invalidado anteriormente no DOM.</span><span class="sxs-lookup"><span data-stu-id="f9e68-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="f9e68-123">Validação de esquema usando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f9e68-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="f9e68-124">Discute como validar XML que está sendo navegado e editado usando a classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f9e68-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
