---
title: Elemento <dateTimeSerialization>
description: Este artigo descreve o <dateTimeSerialization> elemento, que determina o modo de serialização de objetos DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375820"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="b85c5-103">Elemento \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="b85c5-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="b85c5-104">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b85c5-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="b85c5-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b85c5-105">\<configuration></span></span>  
<span data-ttu-id="b85c5-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="b85c5-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85c5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b85c5-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b85c5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b85c5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b85c5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b85c5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b85c5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b85c5-110">Attributes</span></span>  
  
|<span data-ttu-id="b85c5-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b85c5-111">Attributes</span></span>|<span data-ttu-id="b85c5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b85c5-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="b85c5-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b85c5-113">Optional.</span></span> <span data-ttu-id="b85c5-114">Especifica o modo de serialização.</span><span class="sxs-lookup"><span data-stu-id="b85c5-114">Specifies the serialization mode.</span></span> <span data-ttu-id="b85c5-115">Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="b85c5-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="b85c5-116">O padrão é **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="b85c5-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b85c5-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b85c5-117">Child Elements</span></span>  
 <span data-ttu-id="b85c5-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b85c5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b85c5-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b85c5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b85c5-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b85c5-120">Element</span></span>|<span data-ttu-id="b85c5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b85c5-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b85c5-122">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="b85c5-122">system.xml.serialization</span></span>|<span data-ttu-id="b85c5-123">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="b85c5-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b85c5-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b85c5-124">Remarks</span></span>  
 <span data-ttu-id="b85c5-125">Nas versões 1,0, 1,1, 2,0 e versões posteriores do .NET Framework, quando essa propriedade é definida como **local**, <xref:System.DateTime> os objetos são sempre formatados como a hora local.</span><span class="sxs-lookup"><span data-stu-id="b85c5-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="b85c5-126">Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="b85c5-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="b85c5-127">Defina essa propriedade como **Local** para garantir a compatibilidade com versões mais antigas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b85c5-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b85c5-128">Na versão 2,0 e versões posteriores do .NET Framework que têm essa propriedade definida como de **ida e volta**, os <xref:System.DateTime> objetos são examinados para determinar se estão no fuso horário local, UTC ou não especificado.</span><span class="sxs-lookup"><span data-stu-id="b85c5-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="b85c5-129">Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas.</span><span class="sxs-lookup"><span data-stu-id="b85c5-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="b85c5-130">Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.</span><span class="sxs-lookup"><span data-stu-id="b85c5-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85c5-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b85c5-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="b85c5-132">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="b85c5-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b85c5-133">\<Elemento de> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="b85c5-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="b85c5-134">\<Adicionar> elemento para \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="b85c5-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="b85c5-135">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="b85c5-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
