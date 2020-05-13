---
title: Elemento <schemaImporterExtensions>
description: O <schemaImporterExtensions> elemento contém tipos que são usados pelo XmlSchemaImporter para mapeamento de tipos XSD para .NET Framework tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379797"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="9c2a3-103">Elemento \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="9c2a3-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="9c2a3-104">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="9c2a3-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c2a3-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2a3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c2a3-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="9c2a3-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c2a3-107">Child Elements</span></span>  
  
|<span data-ttu-id="9c2a3-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c2a3-108">Element</span></span>|<span data-ttu-id="9c2a3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c2a3-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c2a3-110">\<Adicionar> elemento para \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="9c2a3-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="9c2a3-111">Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="9c2a3-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c2a3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9c2a3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c2a3-113">Element</span></span>|<span data-ttu-id="9c2a3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c2a3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c2a3-115">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="9c2a3-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="9c2a3-116">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c2a3-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c2a3-117">Example</span></span>  
 <span data-ttu-id="9c2a3-118">O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c2a3-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c2a3-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c2a3-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="9c2a3-120">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9c2a3-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9c2a3-121">\<Elemento de> dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="9c2a3-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="9c2a3-122">\<Adicionar> elemento para \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="9c2a3-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="9c2a3-123">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="9c2a3-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
