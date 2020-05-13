---
title: A ferramenta de definição de esquema XML e a serialização XML
description: A ferramenta de definição de esquema XML gera arquivos de classe C# ou Visual Basic para um esquema XSD e gera um esquema XML de uma biblioteca ou arquivo executável.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 258e66643dae64aec7280419911f5ac9193a2ada
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380100"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="cb354-103">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="cb354-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="cb354-104">A ferramenta de definição de esquema XML ([XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)é instalada junto com as ferramentas de .NET Framework como parte do &reg; SDK (Software Development Kit) do Windows.</span><span class="sxs-lookup"><span data-stu-id="cb354-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="cb354-105">A ferramenta é criada principalmente para duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="cb354-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="cb354-106">Para gerar arquivos de classe C# ou Visual Basic que estejam em conformidade com um esquema específico de linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="cb354-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="cb354-107">A ferramenta usa um esquema XML como um argumento e gera um arquivo que contém um número de classes que, quando serializadas com o <xref:System.Xml.Serialization.XmlSerializer>, estão em conformidade com o esquema.</span><span class="sxs-lookup"><span data-stu-id="cb354-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="cb354-108">Para obter informações sobre como usar a ferramenta para gerar classes em conformidade com um esquema específico, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="cb354-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="cb354-109">Para gerar um documento de esquema XML de um arquivo .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="cb354-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="cb354-110">Para ver o esquema de um conjunto de arquivos que você criou ou um que tenha sido alterado com atributos, passe o DLL ou EXE como um argumento para a ferramenta para gerar o esquema XML.</span><span class="sxs-lookup"><span data-stu-id="cb354-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="cb354-111">Para obter informações sobre como usar a ferramenta para gerar um XML Schema Document com base em um conjunto de classes, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="cb354-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="cb354-112">Para obter mais informações sobre como usar a ferramenta, consulte [ferramenta de definição de esquema XML (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb354-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb354-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb354-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="cb354-114">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="cb354-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="cb354-115">Ferramenta de definição de esquema XML (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="cb354-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="cb354-116">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="cb354-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="cb354-117">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="cb354-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="cb354-118">Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML</span><span class="sxs-lookup"><span data-stu-id="cb354-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="cb354-119">[Suporte à associação de esquema XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cb354-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
