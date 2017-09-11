---
title: "Atributos que controlam a serialização SOAP codificada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: 8
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a6af8cd2560bb9c39657d8e5b088954996ba2a04
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="attributes-that-control-encoded-soap-serialization"></a><span data-ttu-id="f9bf0-102">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="f9bf0-102">Attributes That Control Encoded SOAP Serialization</span></span> 
<span data-ttu-id="f9bf0-103">O documento do World Wide Web Consortium (www.w3.org) intitulado “Simple Object Access Protocol (SOAP) 1.1” (Protocolo SOAP 1.1) contém uma seção opcional (seção 5) que descreve como os parâmetros SOAP podem ser codificados.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-103">The World Wide Web Consortium (www.w3.org) document named "Simple Object Access Protocol (SOAP) 1.1" contains an optional section (section 5) that describes how SOAP parameters can be encoded.</span></span> <span data-ttu-id="f9bf0-104">Para estar em conformidade com a seção 5 da especificação, é necessário usar um conjunto especial de atributos encontrados no namespace <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-104">To conform to section 5 of the specification, you must use a special set of attributes found in the <xref:System.Xml.Serialization> namespace.</span></span> <span data-ttu-id="f9bf0-105">Aplique esses atributos conforme for apropriado a classes e membros das classes e, em seguida, use o <xref:System.Xml.Serialization.XmlSerializer> para serializar instâncias da classe ou classes.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-105">Apply those attributes as appropriate to classes and members of classes, and then use the <xref:System.Xml.Serialization.XmlSerializer> to serialize instances of the class or classes.</span></span>  
  
 <span data-ttu-id="f9bf0-106">A tabela a seguir mostra os atributos, onde podem ser aplicados e o que eles fazem.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-106">The following table shows the attributes, where they can be applied, and what they do.</span></span> <span data-ttu-id="f9bf0-107">Para obter mais informações sobre como usar esses atributos para controlar a serialização XML, consulte [Como serializar um objeto como um fluxo XML codificado em SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) e [Como substituir a serialização XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f9bf0-107">For more information about using these attributes to control XML serialization, see [How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) and [How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).</span></span>  
  
 <span data-ttu-id="f9bf0-108">Para obter mais informações sobre atributos, consulte [Atributos](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9bf0-108">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span>  
  
|<span data-ttu-id="f9bf0-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="f9bf0-109">Attribute</span></span>|<span data-ttu-id="f9bf0-110">Aplica-se a</span><span class="sxs-lookup"><span data-stu-id="f9bf0-110">Applies to</span></span>|<span data-ttu-id="f9bf0-111">Especifica</span><span class="sxs-lookup"><span data-stu-id="f9bf0-111">Specifies</span></span>|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|<span data-ttu-id="f9bf0-112">Campo público, propriedade, parâmetro ou valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-112">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="f9bf0-113">O membro da classe será serializado como um atributo XML.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-113">The class member will be serialized as an XML attribute.</span></span>|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|<span data-ttu-id="f9bf0-114">Campo público, propriedade, parâmetro ou valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-114">Public field, property, parameter, or return value.</span></span>|<span data-ttu-id="f9bf0-115">A classe será serializada como um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-115">The class will be serialized as an XML element.</span></span>|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|<span data-ttu-id="f9bf0-116">O campo público que é um identificador de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-116">Public field that is an enumeration identifier.</span></span>|<span data-ttu-id="f9bf0-117">O nome do elemento de um membro de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-117">The element name of an enumeration member.</span></span>|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|<span data-ttu-id="f9bf0-118">Propriedades públicas e campos.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-118">Public properties and fields.</span></span>|<span data-ttu-id="f9bf0-119">A propriedade ou campo devem ser ignorados quando a classe recipiente é serializada.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-119">The property or field should be ignored when the containing class is serialized.</span></span>|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|<span data-ttu-id="f9bf0-120">Declarações públicas de classe derivada e métodos públicos para documentos da linguagem WSDL.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-120">Public-derived class declarations and public methods for Web Services Description Language (WSDL) documents.</span></span>|<span data-ttu-id="f9bf0-121">O tipo deve ser incluído ao gerar esquemas (para serem reconhecidos quando serializados).</span><span class="sxs-lookup"><span data-stu-id="f9bf0-121">The type should be included when generating schemas (to be recognized when serialized).</span></span>|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|<span data-ttu-id="f9bf0-122">Declarações públicas de classe.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-122">Public class declarations.</span></span>|<span data-ttu-id="f9bf0-123">A classe deverá ser serializada como um tipo XML.</span><span class="sxs-lookup"><span data-stu-id="f9bf0-123">The class should be serialized as an XML type.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9bf0-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9bf0-124">See Also</span></span>  
 <span data-ttu-id="f9bf0-125">[Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="f9bf0-125">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span></span>  
 <span data-ttu-id="f9bf0-126">[Como serializar um objeto como um fluxo XML codificado em SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) </span><span class="sxs-lookup"><span data-stu-id="f9bf0-126">[How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) </span></span>  
 <span data-ttu-id="f9bf0-127">[Como substituir a serialização XML de SOAP codificada](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="f9bf0-127">[How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md) </span></span>  
 <span data-ttu-id="f9bf0-128">[Atributos](../../../docs/standard/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="f9bf0-128">[Attributes](../../../docs/standard/attributes/index.md) </span></span>  
 <span data-ttu-id="f9bf0-129"><xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="f9bf0-129"><xref:System.Xml.Serialization.XmlSerializer></span></span>   
 <span data-ttu-id="f9bf0-130">[Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="f9bf0-130">[How to: Serialize an Object](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span></span>  
 [<span data-ttu-id="f9bf0-131">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="f9bf0-131">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

