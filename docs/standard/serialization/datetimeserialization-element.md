---
title: Elemento <dateTimeSerialization>
description: Este artigo descreve o <dateTimeSerialization> elemento, que determina o modo de serialização de objetos DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289636"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="575ef-103">Elemento \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="575ef-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="575ef-104">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="575ef-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="575ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="575ef-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="575ef-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="575ef-106">Attributes and Elements</span></span>  
 <span data-ttu-id="575ef-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="575ef-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="575ef-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="575ef-108">Attributes</span></span>  
  
|<span data-ttu-id="575ef-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="575ef-109">Attributes</span></span>|<span data-ttu-id="575ef-110">Description</span><span class="sxs-lookup"><span data-stu-id="575ef-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="575ef-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="575ef-111">Optional.</span></span> <span data-ttu-id="575ef-112">Especifica o modo de serialização.</span><span class="sxs-lookup"><span data-stu-id="575ef-112">Specifies the serialization mode.</span></span> <span data-ttu-id="575ef-113">Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="575ef-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="575ef-114">O padrão é **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="575ef-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="575ef-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="575ef-115">Child Elements</span></span>  
 <span data-ttu-id="575ef-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="575ef-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="575ef-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="575ef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="575ef-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="575ef-118">Element</span></span>|<span data-ttu-id="575ef-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="575ef-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="575ef-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="575ef-120">system.xml.serialization</span></span>|<span data-ttu-id="575ef-121">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="575ef-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="575ef-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="575ef-122">Remarks</span></span>  
 <span data-ttu-id="575ef-123">Nas versões 1,0, 1,1, 2,0 e versões posteriores do .NET Framework, quando essa propriedade é definida como **local**, <xref:System.DateTime> os objetos são sempre formatados como a hora local.</span><span class="sxs-lookup"><span data-stu-id="575ef-123">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="575ef-124">Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="575ef-124">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="575ef-125">Defina essa propriedade como **Local** para garantir a compatibilidade com versões mais antigas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="575ef-125">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="575ef-126">Na versão 2,0 e versões posteriores do .NET Framework que têm essa propriedade definida como de **ida e volta**, os <xref:System.DateTime> objetos são examinados para determinar se estão no fuso horário local, UTC ou não especificado.</span><span class="sxs-lookup"><span data-stu-id="575ef-126">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="575ef-127">Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas.</span><span class="sxs-lookup"><span data-stu-id="575ef-127">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="575ef-128">Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.</span><span class="sxs-lookup"><span data-stu-id="575ef-128">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575ef-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="575ef-129">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="575ef-130">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="575ef-130">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="575ef-131">\<schemaImporterExtensions>Elementos</span><span class="sxs-lookup"><span data-stu-id="575ef-131">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="575ef-132">\<add>Elemento para\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="575ef-132">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="575ef-133">\<system.xml.serialization>Elementos</span><span class="sxs-lookup"><span data-stu-id="575ef-133">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
