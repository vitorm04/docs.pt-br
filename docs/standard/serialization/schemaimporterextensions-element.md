---
title: Elemento <schemaImporterExtensions>
description: O <schemaImporterExtensions> elemento contém tipos que são usados pelo XmlSchemaImporter para mapeamento de tipos XSD para tipos .net.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 35626618a8dd7c63a7008d10bc3568484836a488
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282271"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="ee76f-103">Elemento \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ee76f-103">\<schemaImporterExtensions> element</span></span>

<span data-ttu-id="ee76f-104">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos .net.</span><span class="sxs-lookup"><span data-stu-id="ee76f-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span> <span data-ttu-id="ee76f-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee76f-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee76f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee76f-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="ee76f-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ee76f-107">Child Elements</span></span>  
  
|<span data-ttu-id="ee76f-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee76f-108">Element</span></span>|<span data-ttu-id="ee76f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee76f-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee76f-110">\<add> Elemento para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ee76f-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="ee76f-111">Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="ee76f-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="ee76f-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ee76f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ee76f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee76f-113">Element</span></span>|<span data-ttu-id="ee76f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee76f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee76f-115">\<system.xml.serialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="ee76f-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="ee76f-116">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="ee76f-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee76f-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee76f-117">Example</span></span>  
 <span data-ttu-id="ee76f-118">O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear tipos XSD para tipos .net.</span><span class="sxs-lookup"><span data-stu-id="ee76f-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee76f-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="ee76f-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="ee76f-120">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ee76f-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ee76f-121">\<dateTimeSerialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="ee76f-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="ee76f-122">\<add> Elemento para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="ee76f-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="ee76f-123">\<system.xml.serialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="ee76f-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
