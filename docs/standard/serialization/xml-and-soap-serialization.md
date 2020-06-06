---
title: Serialização XML e SOAP
description: Esta visão geral discute a serialização XML, que pode ser usada para serializar objetos em fluxos XML que estão em conformidade com a especificação SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 6b7d6f59694a28207758fa7772781eed073917e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379538"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="c5869-103">serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="c5869-103">XML and SOAP serialization</span></span>

<span data-ttu-id="c5869-104">A serialização de XML converte (serializa) os campos públicos e as propriedades de um objeto e os parâmetros e valores de retorno de métodos, em um fluxo XML que está de acordo com um documento XSD (linguagem de definição de esquema XML) específico.</span><span class="sxs-lookup"><span data-stu-id="c5869-104">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="c5869-105">A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.</span><span class="sxs-lookup"><span data-stu-id="c5869-105">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="c5869-106">Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="c5869-106">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="c5869-107">Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets.</span><span class="sxs-lookup"><span data-stu-id="c5869-107">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="c5869-108">Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.</span><span class="sxs-lookup"><span data-stu-id="c5869-108">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="c5869-109">A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP.</span><span class="sxs-lookup"><span data-stu-id="c5869-109">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="c5869-110">SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.</span><span class="sxs-lookup"><span data-stu-id="c5869-110">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="c5869-111">Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c5869-111">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="c5869-112">Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c5869-112">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5869-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5869-113">See also</span></span>

- [<span data-ttu-id="c5869-114">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="c5869-114">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="c5869-115">[Serviços Web XML criados usando ASP.NET e clientes de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c5869-115">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
