---
title: Elemento &lt;system.xml.serialization&gt;
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 8b85eef0f2c3bbb2d0d4a5548f5cbb4a66b0431d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609558"
---
# <a name="ltsystemxmlserializationgt-element"></a><span data-ttu-id="6ae8b-102">Elemento &lt;system.xml.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="6ae8b-102">&lt;system.xml.serialization&gt; Element</span></span>
<span data-ttu-id="6ae8b-103">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-103">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="6ae8b-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ae8b-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="6ae8b-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6ae8b-105">\<configuration></span></span>  
<span data-ttu-id="6ae8b-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="6ae8b-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae8b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ae8b-107">Syntax</span></span>  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ae8b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6ae8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6ae8b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ae8b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6ae8b-110">Attributes</span></span>  
 <span data-ttu-id="6ae8b-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ae8b-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6ae8b-112">Child Elements</span></span>  
  
|<span data-ttu-id="6ae8b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ae8b-113">Element</span></span>|<span data-ttu-id="6ae8b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ae8b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ae8b-115">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ae8b-115">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>|<span data-ttu-id="6ae8b-116">Determina o modo de serialização de objetos <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-116">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|  
|<span data-ttu-id="6ae8b-117">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ae8b-117">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>|<span data-ttu-id="6ae8b-118">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-118">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ae8b-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6ae8b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6ae8b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="6ae8b-120">Element</span></span>|<span data-ttu-id="6ae8b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ae8b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ae8b-122">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="6ae8b-122">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="6ae8b-123">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-123">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6ae8b-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ae8b-124">Example</span></span>  
 <span data-ttu-id="6ae8b-125">O exemplo de código a seguir ilustra como especificar o modo de serialização de um objeto <xref:System.DateTime> e a adição de tipos usada pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ae8b-125">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ae8b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ae8b-126">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="6ae8b-127">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6ae8b-127">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- <span data-ttu-id="6ae8b-128">Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ae8b-128">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md)</span></span>
- <span data-ttu-id="6ae8b-129">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ae8b-129">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>
- [<span data-ttu-id="6ae8b-130">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="6ae8b-130">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
