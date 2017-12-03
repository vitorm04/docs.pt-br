---
title: "A ferramenta de definição de esquema XML e a serialização XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6bd462714ada242062c9e2e23f924868f5870ef8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="fcbd5-102">A ferramenta de definição de esquema XML e a serialização XML</span><span class="sxs-lookup"><span data-stu-id="fcbd5-102">The XML Schema Definition Tool and XML Serialization</span></span>
<span data-ttu-id="fcbd5-103">A ferramenta de Definição de Esquema XML ([Ferramenta de Definição de Esquema XML [Xsd.exe]](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) é instalada junto com as ferramentas do .NET Framework como parte do Software Development Kit do Windows® (SDK do Windows).</span><span class="sxs-lookup"><span data-stu-id="fcbd5-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows® Software Development Kit (SDK).</span></span> <span data-ttu-id="fcbd5-104">A ferramenta é criada principalmente para duas finalidades:</span><span class="sxs-lookup"><span data-stu-id="fcbd5-104">The tool is designed primarily for two purposes:</span></span>  
  
-   <span data-ttu-id="fcbd5-105">Para gerar arquivos de classe C# ou Visual Basic que estejam em conformidade com um esquema específico de linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="fcbd5-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="fcbd5-106">A ferramenta usa um esquema XML como um argumento e gera um arquivo que contém um número de classes que, quando serializadas com o <xref:System.Xml.Serialization.XmlSerializer>, estão em conformidade com o esquema.</span><span class="sxs-lookup"><span data-stu-id="fcbd5-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="fcbd5-107">Para obter informações sobre como usar a ferramenta para gerar classes em conformidade com um esquema específico, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="fcbd5-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
-   <span data-ttu-id="fcbd5-108">Para gerar um documento de esquema XML de um arquivo .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="fcbd5-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="fcbd5-109">Para ver o esquema de um conjunto de arquivos que você criou ou um que tenha sido alterado com atributos, passe o DLL ou EXE como um argumento para a ferramenta para gerar o esquema XML.</span><span class="sxs-lookup"><span data-stu-id="fcbd5-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="fcbd5-110">Para obter informações sobre como usar a ferramenta para gerar um XML Schema Document com base em um conjunto de classes, consulte [Como usar a Ferramenta de Definição de Esquema XML para gerar classes e XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="fcbd5-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
 <span data-ttu-id="fcbd5-111">Para obter mais informações sobre essa ferramenta e outras, consulte [Ferramentas](../../../docs/framework/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcbd5-111">For more information about this tool and others, see [Tools](../../../docs/framework/tools/index.md).</span></span> <span data-ttu-id="fcbd5-112">Para obter informações sobre as opções da ferramenta, consulte [Ferramenta de Definição de Esquema XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fcbd5-112">For information about the tool's options, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbd5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcbd5-113">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="fcbd5-114">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="fcbd5-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="fcbd5-115">Ferramenta de Definição de Esquema XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="fcbd5-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="fcbd5-116">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="fcbd5-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="fcbd5-117">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="fcbd5-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="fcbd5-118">Como usar a ferramenta de definição de esquema XML para gerar classes e documentos de esquema XML</span><span class="sxs-lookup"><span data-stu-id="fcbd5-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)  
 [<span data-ttu-id="fcbd5-119">Suporte à associação de esquema XML no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fcbd5-119">XML Schema Binding Support in the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/8f0619dd-f1fc-4895-ae21-6d45d0382cc1)
