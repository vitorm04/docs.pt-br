---
title: Atributos que controlam a serialização SOAP codificada
description: Este artigo lista um conjunto especial de atributos encontrados no namespace System. xml. Serialization necessário para estar em conformidade com a especificação SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 9e99856c3ac70b122c0def23e36bbc3059c5891c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378468"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="ba975-103">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="ba975-103">Attributes That Control Encoded SOAP Serialization</span></span>

<span data-ttu-id="ba975-104">O documento World Wide Web Consortium (W3C) denominado [protocolo soap 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contém uma seção opcional (seção 5) que descreve como os parâmetros SOAP podem ser codificados.</span><span class="sxs-lookup"><span data-stu-id="ba975-104">The World Wide Web Consortium (W3C) document named [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="ba975-105">Para estar em conformidade com a seção 5 da especificação, é necessário usar um conjunto especial de atributos encontrados no namespace <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="ba975-105">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="ba975-106">Aplique esses atributos conforme for apropriado a classes e membros das classes e, em seguida, use o <xref:System.Xml.Serialization.XmlSerializer> para serializar instâncias da classe ou classes.</span><span class="sxs-lookup"><span data-stu-id="ba975-106">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>

<span data-ttu-id="ba975-107">A tabela a seguir mostra os atributos, onde podem ser aplicados e o que eles fazem.</span><span class="sxs-lookup"><span data-stu-id="ba975-107">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="ba975-108">Para obter mais informações sobre como usar esses atributos para controlar a serialização XML, consulte [Como serializar um objeto como um fluxo XML codificado em SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) e [Como substituir a serialização XML de SOAP codificada](how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ba975-108">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](how-to-override-encoded-soap-xml-serialization.md).</span></span>

<span data-ttu-id="ba975-109">Para obter mais informações sobre atributos, consulte [Atributos](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba975-109">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>

|<span data-ttu-id="ba975-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba975-110">Attribute</span></span>|<span data-ttu-id="ba975-111">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="ba975-111">Applies to</span></span>|<span data-ttu-id="ba975-112">Especifica</span><span class="sxs-lookup"><span data-stu-id="ba975-112">Specifies</span></span>|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="ba975-113">Campo público, propriedade, parâmetro ou valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ba975-113">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="ba975-114">O membro da classe será serializado como um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="ba975-114">The class member will be serialized as an XML attribute.</span></span>|
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="ba975-115">Campo público, propriedade, parâmetro ou valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ba975-115">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="ba975-116">A classe será serializada como um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ba975-116">The class will be serialized as an XML element.</span></span>|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="ba975-117">O campo público que é um identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ba975-117">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="ba975-118">O nome do elemento de um membro de enumeração.</span><span class="sxs-lookup"><span data-stu-id="ba975-118">The element name of an enumeration member.</span></span>|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="ba975-119">Propriedades públicas e campos.</span><span class="sxs-lookup"><span data-stu-id="ba975-119">Public properties and fields.</span></span>|<span data-ttu-id="ba975-120">A propriedade ou campo devem ser ignorados quando a classe recipiente é serializada.</span><span class="sxs-lookup"><span data-stu-id="ba975-120">The property or field should be ignored when the containing class is serialized.</span></span>|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="ba975-121">Declarações públicas de classe derivada e métodos públicos para documentos da linguagem WSDL.</span><span class="sxs-lookup"><span data-stu-id="ba975-121">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="ba975-122">O tipo deve ser incluído ao gerar esquemas (para serem reconhecidos quando serializados).</span><span class="sxs-lookup"><span data-stu-id="ba975-122">The type should be included when generating schemas (to be recognized when serialized).</span></span>|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="ba975-123">Declarações públicas de classe.</span><span class="sxs-lookup"><span data-stu-id="ba975-123">Public class declarations.</span></span>|<span data-ttu-id="ba975-124">A classe deverá ser serializada como um tipo XML.</span><span class="sxs-lookup"><span data-stu-id="ba975-124">The class should be serialized as an XML type.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ba975-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="ba975-125">See also</span></span>

- [<span data-ttu-id="ba975-126">Serialização de XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="ba975-126">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="ba975-127">Como serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="ba975-127">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [<span data-ttu-id="ba975-128">Como substituir a serialização XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="ba975-128">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)
- [<span data-ttu-id="ba975-129">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba975-129">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="ba975-130">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="ba975-130">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="ba975-131">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="ba975-131">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
