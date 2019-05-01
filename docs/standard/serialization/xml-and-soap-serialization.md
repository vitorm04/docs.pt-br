---
title: Serialização XML e SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028233"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="64b09-102">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="64b09-102">XML and SOAP Serialization</span></span>

<span data-ttu-id="64b09-103">A serialização XML converte (serializa) as propriedades e os campos públicos de um objeto (ou os parâmetros e valores de retorno de métodos) em um fluxo XML que esteja de acordo com um documento XSD (linguagem de definição de esquema XML) específico.</span><span class="sxs-lookup"><span data-stu-id="64b09-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="64b09-104">A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.</span><span class="sxs-lookup"><span data-stu-id="64b09-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="64b09-105">Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="64b09-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="64b09-106">Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets.</span><span class="sxs-lookup"><span data-stu-id="64b09-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="64b09-107">Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.</span><span class="sxs-lookup"><span data-stu-id="64b09-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="64b09-108">A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP.</span><span class="sxs-lookup"><span data-stu-id="64b09-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="64b09-109">SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="64b09-110">Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="64b09-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="64b09-111">Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="64b09-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="64b09-112">In This Section</span></span>

[<span data-ttu-id="64b09-113">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="64b09-113">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)  
<span data-ttu-id="64b09-114">Fornece uma definição geral de serialização, particularmente da serialização XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-114">Provides a general definition of serialization, particularly XML serialization.</span></span>

[<span data-ttu-id="64b09-115">Como: Serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="64b09-115">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)  
<span data-ttu-id="64b09-116">Fornece instruções passo a passo para serializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="64b09-116">Provides step-by-step instructions for serializing an object.</span></span>

[<span data-ttu-id="64b09-117">Como: Desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="64b09-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)  
<span data-ttu-id="64b09-118">Fornece instruções passo a passo para desserializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="64b09-118">Provides step-by-step instructions for deserializing an object.</span></span>

[<span data-ttu-id="64b09-119">Exemplos de serialização XML</span><span class="sxs-lookup"><span data-stu-id="64b09-119">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)  
<span data-ttu-id="64b09-120">Fornece exemplos que demonstram os conceitos básicos da serialização XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-120">Provides examples that demonstrate the basics of XML serialization.</span></span>

[<span data-ttu-id="64b09-121">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="64b09-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)  
<span data-ttu-id="64b09-122">Descreve como usar a ferramenta de definição de esquema XML para criar classes que aderem a um esquema XSD específico ou para gerar um esquema XML de um arquivo .dll.</span><span class="sxs-lookup"><span data-stu-id="64b09-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>

[<span data-ttu-id="64b09-123">Controlando a serialização XML usando atributos</span><span class="sxs-lookup"><span data-stu-id="64b09-123">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)  
<span data-ttu-id="64b09-124">Descreve como controlar a serialização usando atributos.</span><span class="sxs-lookup"><span data-stu-id="64b09-124">Describes how to control serialization by using attributes.</span></span>

[<span data-ttu-id="64b09-125">Atributos que controlam a serialização XML</span><span class="sxs-lookup"><span data-stu-id="64b09-125">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)  
<span data-ttu-id="64b09-126">Lista os atributos que são usados para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-126">Lists the attributes that are used to control XML serialization.</span></span>

[<span data-ttu-id="64b09-127">Como: Especifique um nome de elemento alternativo para um Stream XML</span><span class="sxs-lookup"><span data-stu-id="64b09-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
<span data-ttu-id="64b09-128">Apresenta um cenário avançado de como gerar vários fluxos XML substituindo a serialização.</span><span class="sxs-lookup"><span data-stu-id="64b09-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>

[<span data-ttu-id="64b09-129">Como: Controlam a serialização de Classes derivadas</span><span class="sxs-lookup"><span data-stu-id="64b09-129">How to: Control Serialization of Derived Classes</span></span>](how-to-control-serialization-of-derived-classes.md)  
<span data-ttu-id="64b09-130">Fornece um exemplo de como controlar a serialização de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="64b09-130">Provides an example of how to control the serialization of derived classes.</span></span>

[<span data-ttu-id="64b09-131">Como: Qualificar elementos XML e nomes de atributo XML</span><span class="sxs-lookup"><span data-stu-id="64b09-131">How to: Qualify XML Element and XML Attribute Names</span></span>](how-to-qualify-xml-element-and-xml-attribute-names.md)  
<span data-ttu-id="64b09-132">Descreve como definir e controlar a maneira como namespaces XML são usados no fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>

[<span data-ttu-id="64b09-133">Serialização XML com Serviços Web XML</span><span class="sxs-lookup"><span data-stu-id="64b09-133">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)  
<span data-ttu-id="64b09-134">Explica como a serialização XML é usada em serviços Web XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-134">Explains how XML serialization is used in XML Web services.</span></span>

[<span data-ttu-id="64b09-135">Como: Serializar um objeto como um Stream do XML codificado em SOAP</span><span class="sxs-lookup"><span data-stu-id="64b09-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
<span data-ttu-id="64b09-136">Descreve como usar o <xref:System.Xml.Serialization.XmlSerializer> classe para criar fluxos XML SOAP codificados que estão em conformidade com a seção 5 do documento do World Wide Web Consortium (W3C) [simples objeto Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span><span class="sxs-lookup"><span data-stu-id="64b09-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).</span></span>

[<span data-ttu-id="64b09-137">Como: Substituir a serialização de XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="64b09-137">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)  
<span data-ttu-id="64b09-138">Descreve o processo para substituir a serialização XML de objetos, como mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="64b09-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>

[<span data-ttu-id="64b09-139">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="64b09-139">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)  
<span data-ttu-id="64b09-140">Lista os atributos que são usados para controlar a serialização codificada por SOAP.</span><span class="sxs-lookup"><span data-stu-id="64b09-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>

[<span data-ttu-id="64b09-141">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="64b09-141">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)  
<span data-ttu-id="64b09-142">O elemento de configuração de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="64b09-142">The top-level configuration element for controlling XML serialization.</span></span>

<span data-ttu-id="64b09-143">Elemento [\<dateTimeSerialization>](datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="64b09-143">[\<dateTimeSerialization> Element](datetimeserialization-element.md)</span></span>  
<span data-ttu-id="64b09-144">Controla o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="64b09-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>

<span data-ttu-id="64b09-145">Elemento [\<schemaImporterExtensions>](schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="64b09-145">[\<schemaImporterExtensions> Element](schemaimporterextensions-element.md)</span></span>  
<span data-ttu-id="64b09-146">Contém tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="64b09-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

[<span data-ttu-id="64b09-147">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="64b09-147">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)  
<span data-ttu-id="64b09-148">Adiciona tipos que são usados pela classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="64b09-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>

## <a name="related-sections"></a><span data-ttu-id="64b09-149">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="64b09-149">Related Sections</span></span>

<span data-ttu-id="64b09-150">[Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64b09-150">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>  
<span data-ttu-id="64b09-151">Fornece tópicos que descrevem e explicam como programar serviços Web XML usando ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64b09-151">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="64b09-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64b09-152">See also</span></span>

- [<span data-ttu-id="64b09-153">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="64b09-153">Binary Serialization</span></span>](binary-serialization.md)
