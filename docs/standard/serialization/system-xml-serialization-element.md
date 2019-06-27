---
title: Elemento <system.xml.serialization>
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410540"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="08b0a-102">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="08b0a-102">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="08b0a-103">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="08b0a-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="08b0a-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="08b0a-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="08b0a-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="08b0a-105">\<configuration></span></span>\
<span data-ttu-id="08b0a-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="08b0a-106">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="08b0a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08b0a-107">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08b0a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08b0a-108">Attributes and Elements</span></span>

<span data-ttu-id="08b0a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08b0a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="08b0a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="08b0a-110">Attributes</span></span>

<span data-ttu-id="08b0a-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="08b0a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08b0a-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08b0a-112">Child Elements</span></span>

|<span data-ttu-id="08b0a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="08b0a-113">Element</span></span>|<span data-ttu-id="08b0a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="08b0a-114">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="08b0a-115">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="08b0a-115">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>|<span data-ttu-id="08b0a-116">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="08b0a-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|<span data-ttu-id="08b0a-117">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="08b0a-117">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>|<span data-ttu-id="08b0a-118">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b0a-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08b0a-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08b0a-119">Parent Elements</span></span>

|<span data-ttu-id="08b0a-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="08b0a-120">Element</span></span>|<span data-ttu-id="08b0a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="08b0a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08b0a-122">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="08b0a-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="08b0a-123">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b0a-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="08b0a-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08b0a-124">Example</span></span>

<span data-ttu-id="08b0a-125">O exemplo de código a seguir ilustra como especificar o modo de serialização de um objeto <xref:System.DateTime> e a adição de tipos usada pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08b0a-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08b0a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08b0a-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="08b0a-127">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="08b0a-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- <span data-ttu-id="08b0a-128">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="08b0a-128">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>
- <span data-ttu-id="08b0a-129">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="08b0a-129">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>
- [<span data-ttu-id="08b0a-130">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="08b0a-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
