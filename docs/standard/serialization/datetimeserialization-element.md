---
title: Elemento <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459269"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="9bb85-102">Elemento \<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="9bb85-102">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="9bb85-103">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9bb85-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="9bb85-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9bb85-104">\<configuration></span></span>  
<span data-ttu-id="9bb85-105">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="9bb85-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb85-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bb85-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bb85-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9bb85-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9bb85-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9bb85-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bb85-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9bb85-109">Attributes</span></span>  
  
|<span data-ttu-id="9bb85-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9bb85-110">Attributes</span></span>|<span data-ttu-id="9bb85-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb85-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="9bb85-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9bb85-112">Optional.</span></span> <span data-ttu-id="9bb85-113">Especifica o modo de serialização.</span><span class="sxs-lookup"><span data-stu-id="9bb85-113">Specifies the serialization mode.</span></span> <span data-ttu-id="9bb85-114">Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.</span><span class="sxs-lookup"><span data-stu-id="9bb85-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="9bb85-115">O padrão é **RoundTrip**.</span><span class="sxs-lookup"><span data-stu-id="9bb85-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bb85-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9bb85-116">Child Elements</span></span>  
 <span data-ttu-id="9bb85-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9bb85-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bb85-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9bb85-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9bb85-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9bb85-119">Element</span></span>|<span data-ttu-id="9bb85-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb85-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bb85-121">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="9bb85-121">system.xml.serialization</span></span>|<span data-ttu-id="9bb85-122">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="9bb85-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bb85-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bb85-123">Remarks</span></span>  
 <span data-ttu-id="9bb85-124">Nas versões 1,0, 1,1, 2,0 e versões posteriores do .NET Framework, quando essa propriedade é definida como **local**, <xref:System.DateTime> os objetos são sempre formatados como a hora local.</span><span class="sxs-lookup"><span data-stu-id="9bb85-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="9bb85-125">Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="9bb85-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="9bb85-126">Defina essa propriedade como **Local** para garantir a compatibilidade com versões mais antigas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bb85-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9bb85-127">Na versão 2,0 e versões posteriores do .NET Framework que têm essa propriedade definida como de ida <xref:System.DateTime> e **volta**, os objetos são examinados para determinar se estão no fuso horário local, UTC ou não especificado.</span><span class="sxs-lookup"><span data-stu-id="9bb85-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="9bb85-128">Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas.</span><span class="sxs-lookup"><span data-stu-id="9bb85-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="9bb85-129">Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.</span><span class="sxs-lookup"><span data-stu-id="9bb85-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb85-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="9bb85-130">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="9bb85-131">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9bb85-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9bb85-132">\<Elemento de> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="9bb85-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="9bb85-133">\<Adicionar> elemento para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="9bb85-133">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="9bb85-134">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="9bb85-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
