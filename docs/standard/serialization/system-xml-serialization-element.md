---
title: Elemento &lt;system.xml.serialization&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: 5
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 68d2b7385ce492c52de41abe50e00b1438fe52b6
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="3bbb6-102">Elemento &lt;system.xml.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="3bbb6-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="3bbb6-103">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="3bbb6-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3bbb6-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="3bbb6-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3bbb6-105">\<configuration></span></span>  
<span data-ttu-id="3bbb6-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="3bbb6-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbb6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bbb6-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bbb6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3bbb6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3bbb6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bbb6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3bbb6-110">Attributes</span></span>  
 <span data-ttu-id="3bbb6-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3bbb6-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3bbb6-112">Child Elements</span></span>  
  
|<span data-ttu-id="3bbb6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bbb6-113">Element</span></span>|<span data-ttu-id="3bbb6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bbb6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bbb6-115">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bbb6-115">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>|<span data-ttu-id="3bbb6-116">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|<span data-ttu-id="3bbb6-117">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bbb6-117">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>|<span data-ttu-id="3bbb6-118">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3bbb6-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3bbb6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3bbb6-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3bbb6-120">Element</span></span>|<span data-ttu-id="3bbb6-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bbb6-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bbb6-122">Elemento [\<configuration>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bbb6-122">[\<configuration> Element](../../../docs/framework/configure-apps/file-schema/configuration-element.md)</span></span>|<span data-ttu-id="3bbb6-123">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3bbb6-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bbb6-124">Example</span></span>  
 <span data-ttu-id="3bbb6-125">O exemplo de código a seguir ilustra como especificar o modo de serialização de um objeto <xref:System.DateTime> e a adição de tipos usada pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bbb6-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bbb6-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bbb6-126">See Also</span></span>  
 <span data-ttu-id="3bbb6-127"><xref:System.Xml.Serialization.XmlSchemaImporter></span><span class="sxs-lookup"><span data-stu-id="3bbb6-127"><xref:System.Xml.Serialization.XmlSchemaImporter></span></span>   
 <span data-ttu-id="3bbb6-128"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span><span class="sxs-lookup"><span data-stu-id="3bbb6-128"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span></span>   
 <span data-ttu-id="3bbb6-129">[Esquema de arquivo de configuração](../../../docs/framework/configure-apps/file-schema/index.md) </span><span class="sxs-lookup"><span data-stu-id="3bbb6-129">[Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md) </span></span>  
 <span data-ttu-id="3bbb6-130">[\<Elemento dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md) </span><span class="sxs-lookup"><span data-stu-id="3bbb6-130">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md) </span></span>  
 <span data-ttu-id="3bbb6-131">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md) </span><span class="sxs-lookup"><span data-stu-id="3bbb6-131">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md) </span></span>  
 [<span data-ttu-id="3bbb6-132">Elemento \<add> para \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="3bbb6-132">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)

