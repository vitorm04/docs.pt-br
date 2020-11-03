---
title: Elemento <system.xml.serialization>
description: Este artigo descreve o <system.xml. serialização> elemento, que é o elemento de nível superior para controlar a serialização de XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282390"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="4f2f0-103">Elemento \<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="4f2f0-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="4f2f0-104">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="4f2f0-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f2f0-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="4f2f0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f2f0-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f2f0-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-107">Attributes and Elements</span></span>

<span data-ttu-id="4f2f0-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f2f0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-109">Attributes</span></span>

<span data-ttu-id="4f2f0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f2f0-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f2f0-111">Child Elements</span></span>

|<span data-ttu-id="4f2f0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f2f0-112">Element</span></span>|<span data-ttu-id="4f2f0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f2f0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f2f0-114">\<dateTimeSerialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="4f2f0-115">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="4f2f0-116">\<schemaImporterExtensions> Elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="4f2f0-117">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos .net.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f2f0-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4f2f0-118">Parent Elements</span></span>

|<span data-ttu-id="4f2f0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f2f0-119">Element</span></span>|<span data-ttu-id="4f2f0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f2f0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f2f0-121">\<configuration> Elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="4f2f0-122">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="4f2f0-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f2f0-123">Example</span></span>

<span data-ttu-id="4f2f0-124">O exemplo de código a seguir ilustra como especificar o modo de serialização de um <xref:System.DateTime> objeto e a adição de tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear tipos XSD para tipos .net.</span><span class="sxs-lookup"><span data-stu-id="4f2f0-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="4f2f0-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f2f0-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="4f2f0-126">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4f2f0-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4f2f0-127">\<dateTimeSerialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="4f2f0-128">\<schemaImporterExtensions> Elementos</span><span class="sxs-lookup"><span data-stu-id="4f2f0-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="4f2f0-129">\<add> Elemento para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="4f2f0-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
