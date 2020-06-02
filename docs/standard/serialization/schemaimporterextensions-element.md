---
title: Elemento <schemaImporterExtensions>
description: O <schemaImporterExtensions> elemento contém tipos que são usados pelo XmlSchemaImporter para mapeamento de tipos XSD para .NET Framework tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278396"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="f311d-103">Elemento \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f311d-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="f311d-104">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f311d-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="f311d-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="f311d-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f311d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f311d-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="f311d-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f311d-107">Child Elements</span></span>  
  
|<span data-ttu-id="f311d-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="f311d-108">Element</span></span>|<span data-ttu-id="f311d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f311d-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f311d-110">\<add>Elemento para\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f311d-110">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)|<span data-ttu-id="f311d-111">Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="f311d-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="f311d-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f311d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f311d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f311d-113">Element</span></span>|<span data-ttu-id="f311d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f311d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f311d-115">\<system.xml.serialization>Elementos</span><span class="sxs-lookup"><span data-stu-id="f311d-115">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="f311d-116">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="f311d-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f311d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f311d-117">Example</span></span>  
 <span data-ttu-id="f311d-118">O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f311d-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f311d-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="f311d-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="f311d-120">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f311d-120">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f311d-121">\<dateTimeSerialization>Elementos</span><span class="sxs-lookup"><span data-stu-id="f311d-121">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="f311d-122">\<add>Elemento para\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f311d-122">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="f311d-123">\<system.xml.serialization>Elementos</span><span class="sxs-lookup"><span data-stu-id="f311d-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
