---
title: Elemento <dateTimeSerialization>
description: Este artigo descreve o <dateTimeSerialization> elemento, que determina o modo de serialização de objetos DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 90ae911c8942fef7a9e8238921990b0a52a47ca0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281760"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="bce80-103">Elemento \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="bce80-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="bce80-104">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="bce80-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a><span data-ttu-id="bce80-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bce80-105">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bce80-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bce80-106">Attributes and Elements</span></span>  
 <span data-ttu-id="bce80-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bce80-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bce80-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="bce80-108">Attributes</span></span>  
  
|<span data-ttu-id="bce80-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bce80-109">Attributes</span></span>|<span data-ttu-id="bce80-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="bce80-110">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="bce80-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bce80-111">Optional.</span></span> <span data-ttu-id="bce80-112">Especifica o modo de serialização.</span><span class="sxs-lookup"><span data-stu-id="bce80-112">Specifies the serialization mode.</span></span> <span data-ttu-id="bce80-113">Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="bce80-113">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="bce80-114">O padrão é **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="bce80-114">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bce80-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bce80-115">Child Elements</span></span>  
 <span data-ttu-id="bce80-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bce80-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bce80-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bce80-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bce80-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="bce80-118">Element</span></span>|<span data-ttu-id="bce80-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="bce80-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bce80-120">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="bce80-120">system.xml.serialization</span></span>|<span data-ttu-id="bce80-121">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="bce80-121">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bce80-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="bce80-122">Remarks</span></span>  

<span data-ttu-id="bce80-123">Quando essa propriedade é definida como **local** , <xref:System.DateTime> os objetos são sempre formatados como a hora local.</span><span class="sxs-lookup"><span data-stu-id="bce80-123">When this property is set to **Local** , <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="bce80-124">Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="bce80-124">That is, local time zone information is always included with the serialized data.</span></span>
  
<span data-ttu-id="bce80-125">Quando essa propriedade é definida como de **ida e volta** , os <xref:System.DateTime> objetos são examinados para determinar se estão no local, no UTC ou em um fuso horário não especificado.</span><span class="sxs-lookup"><span data-stu-id="bce80-125">When this property is set to **Roundtrip** , <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="bce80-126">Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas.</span><span class="sxs-lookup"><span data-stu-id="bce80-126">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="bce80-127">Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.</span><span class="sxs-lookup"><span data-stu-id="bce80-127">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce80-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="bce80-128">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="bce80-129">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bce80-129">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="bce80-130">\<schemaImporterExtensions> Elementos</span><span class="sxs-lookup"><span data-stu-id="bce80-130">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="bce80-131">\<add> Elemento para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="bce80-131">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="bce80-132">\<system.xml.serialization> Elementos</span><span class="sxs-lookup"><span data-stu-id="bce80-132">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
