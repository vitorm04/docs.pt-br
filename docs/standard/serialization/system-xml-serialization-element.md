---
title: Elemento <system.xml.serialization>
description: Este artigo descreve o <elemento System. xml. Serialization>, que é o elemento de nível superior para controlar a serialização de XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380122"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="2a318-103">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="2a318-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="2a318-104">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="2a318-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="2a318-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a318-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="2a318-106">\<> de configuração </span><span class="sxs-lookup"><span data-stu-id="2a318-106">\<configuration></span></span>\
<span data-ttu-id="2a318-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="2a318-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="2a318-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a318-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a318-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a318-109">Attributes and Elements</span></span>

<span data-ttu-id="2a318-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2a318-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a318-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a318-111">Attributes</span></span>

<span data-ttu-id="2a318-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2a318-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a318-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a318-113">Child Elements</span></span>

|<span data-ttu-id="2a318-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a318-114">Element</span></span>|<span data-ttu-id="2a318-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a318-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a318-116">\<Elemento de> dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="2a318-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="2a318-117">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="2a318-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="2a318-118">\<Elemento de> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="2a318-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="2a318-119">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a318-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a318-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a318-120">Parent Elements</span></span>

|<span data-ttu-id="2a318-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a318-121">Element</span></span>|<span data-ttu-id="2a318-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a318-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a318-123">\<Elemento de> de configuração</span><span class="sxs-lookup"><span data-stu-id="2a318-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2a318-124">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a318-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="2a318-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a318-125">Example</span></span>

<span data-ttu-id="2a318-126">O exemplo de código a seguir ilustra como especificar o modo de serialização de um objeto <xref:System.DateTime> e a adição de tipos usada pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a318-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2a318-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a318-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="2a318-128">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2a318-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="2a318-129">\<Elemento de> dateTimeSerialization</span><span class="sxs-lookup"><span data-stu-id="2a318-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="2a318-130">\<Elemento de> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="2a318-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="2a318-131">\<Adicionar> elemento para \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="2a318-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
