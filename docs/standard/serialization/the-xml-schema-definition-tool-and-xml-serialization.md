---
title: A ferramenta de definição de esquema XML e a serialização XML
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588383"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="74368-102">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="74368-102">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="74368-103">A ferramenta XML Schema Definition[(XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)é instalada juntamente&reg; com as ferramentas .NET Framework como parte do Windows Software Development Kit (SDK).</span><span class="sxs-lookup"><span data-stu-id="74368-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="74368-104">A ferramenta é criada principalmente para duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="74368-104">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="74368-105">Para gerar arquivos de classe C# ou Visual Basic que estejam em conformidade com um esquema específico de linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="74368-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="74368-106">A ferramenta usa um esquema XML como um argumento e gera um arquivo que contém um número de classes que, quando serializadas com o <xref:System.Xml.Serialization.XmlSerializer>, estão em conformidade com o esquema.</span><span class="sxs-lookup"><span data-stu-id="74368-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="74368-107">Para obter informações sobre como usar a ferramenta para gerar classes em conformidade com um esquema específico, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="74368-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="74368-108">Para gerar um documento de esquema XML de um arquivo .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="74368-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="74368-109">Para ver o esquema de um conjunto de arquivos que você criou ou um que tenha sido alterado com atributos, passe o DLL ou EXE como um argumento para a ferramenta para gerar o esquema XML.</span><span class="sxs-lookup"><span data-stu-id="74368-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="74368-110">Para obter informações sobre como usar a ferramenta para gerar um XML Schema Document com base em um conjunto de classes, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="74368-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="74368-111">Para obter mais informações sobre o uso da ferramenta, consulte [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="74368-111">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74368-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="74368-112">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="74368-113">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="74368-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="74368-114">Ferramenta de Definição de Esquema XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="74368-114">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="74368-115">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="74368-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="74368-116">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="74368-116">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="74368-117">Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML</span><span class="sxs-lookup"><span data-stu-id="74368-117">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="74368-118">[Suporte de vinculação do esquema XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74368-118">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>
