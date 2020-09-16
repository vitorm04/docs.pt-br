---
title: Validação de XSD (esquema XML) com XmlSchemaSet
description: Saiba como validar documentos XML em um esquema XSD (linguagem de definição de esquema XML) usando uma classe XmlSchemaSet no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 5963ba1b382740b1774c944b74c6a54b13db4f76
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554509"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="889c5-103">Validação de esquema XML (XSD) com o XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="889c5-103">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="889c5-104">Documentos XML podem ser validados em um esquema da linguagem XSD em um <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="889c5-104">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="889c5-105">Validar documentos XML</span><span class="sxs-lookup"><span data-stu-id="889c5-105">Validate XML documents</span></span>  
 <span data-ttu-id="889c5-106">Documentos XML são validados pelo método <xref:System.Xml.XmlReader.Create%2A> da classe <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="889c5-106">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="889c5-107">Para validar um documento XML, construa um objeto <xref:System.Xml.XmlReaderSettings> que contém uma linguagem XSD com a qual validar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="889c5-107">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="889c5-108">O namespace <xref:System.Xml.Schema> contém métodos de extensão que facilitam a validação de uma árvore XML em um arquivo XSD ao usar [LINQ to XML (C#)](../../linq/linq-xml-overview.md) e [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="889c5-108">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="889c5-109">Para obter mais informações sobre como validar documentos XML com LINQ to XML, consulte [como validar usando xsd (LINQ to XML) (C#)](../../linq/validate-xsd.md) e [como: validar usando xsd (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="889c5-109">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../linq/validate-xsd.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).</span></span>
  
 <span data-ttu-id="889c5-110">Um esquema individual ou um conjunto de esquemas (como <xref:System.Xml.Schema.XmlSchemaSet>) podem ser adicionados a um <xref:System.Xml.Schema.XmlSchemaSet> passando qualquer um como um parâmetro para o método <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="889c5-110">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="889c5-111">Ao validar um documento, o namespace de destino do documento deve corresponder ao namespace de destino do esquema no conjunto de esquema.</span><span class="sxs-lookup"><span data-stu-id="889c5-111">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="889c5-112">Veja a seguir um documento XML de exemplo.</span><span class="sxs-lookup"><span data-stu-id="889c5-112">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="889c5-113">Veja a seguir o esquema que valida o documento XML de exemplo.</span><span class="sxs-lookup"><span data-stu-id="889c5-113">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="889c5-114">No exemplo de código a seguir, o esquema acima é adicionado à propriedade <xref:System.Xml.XmlReaderSettings.Schemas%2A> do objeto <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="889c5-114">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="889c5-115">O objeto <xref:System.Xml.XmlReaderSettings> é passado como um parâmetro para o método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>, que valida o documento XML acima.</span><span class="sxs-lookup"><span data-stu-id="889c5-115">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="889c5-116">A propriedade <xref:System.Xml.XmlReaderSettings.ValidationType%2A> do objeto <xref:System.Xml.XmlReaderSettings> é definida como `Schema` para aplicar a validação o documento XML pelo método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="889c5-116">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="889c5-117">Um <xref:System.Xml.Schema.ValidationEventHandler> é adicionado ao objeto <xref:System.Xml.XmlReaderSettings> para manipular qualquer evento <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> gerado por erros encontrados durante o processo de validação do documento XML e do esquema.</span><span class="sxs-lookup"><span data-stu-id="889c5-117">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="889c5-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="889c5-118">See also</span></span>

- [<span data-ttu-id="889c5-119">XmlSchemaSet para compilação de esquema</span><span class="sxs-lookup"><span data-stu-id="889c5-119">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="889c5-120">Trabalhando com esquemas XML</span><span class="sxs-lookup"><span data-stu-id="889c5-120">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
