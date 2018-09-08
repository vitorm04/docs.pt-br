---
title: Elemento &lt;schemaImporterExtensions&gt;
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: b5696c593fdeaabab66ea7c286c6e1309e6e8e38
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204793"
---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="228a7-102">Elemento &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="228a7-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="228a7-103">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="228a7-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="228a7-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="228a7-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228a7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="228a7-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="228a7-106">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="228a7-106">Child Elements</span></span>  
  
|<span data-ttu-id="228a7-107">Elemento</span><span class="sxs-lookup"><span data-stu-id="228a7-107">Element</span></span>|<span data-ttu-id="228a7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="228a7-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="228a7-109">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="228a7-109">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="228a7-110">Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="228a7-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="228a7-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="228a7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="228a7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="228a7-112">Element</span></span>|<span data-ttu-id="228a7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="228a7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="228a7-114">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="228a7-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="228a7-115">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="228a7-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="228a7-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="228a7-116">Example</span></span>  
 <span data-ttu-id="228a7-117">O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="228a7-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="228a7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="228a7-118">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>  
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
- [<span data-ttu-id="228a7-119">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="228a7-119">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
- <span data-ttu-id="228a7-120">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="228a7-120">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>  
- [<span data-ttu-id="228a7-121">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="228a7-121">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)  
- [<span data-ttu-id="228a7-122">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="228a7-122">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
