---
title: Elemento &lt;schemaImporterExtensions&gt;
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
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: cf9ef09f514f38c0250c288e347d28d73caab295
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltschemaimporterextensionsgt-element"></a><span data-ttu-id="81dd7-102">Elemento &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="81dd7-102">&lt;schemaImporterExtensions&gt; Element</span></span>
<span data-ttu-id="81dd7-103">Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81dd7-103">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="81dd7-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="81dd7-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dd7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81dd7-105">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="81dd7-106">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81dd7-106">Child Elements</span></span>  
  
|<span data-ttu-id="81dd7-107">Elemento</span><span class="sxs-lookup"><span data-stu-id="81dd7-107">Element</span></span>|<span data-ttu-id="81dd7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="81dd7-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81dd7-109">Elemento \<add> para \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="81dd7-109">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)|<span data-ttu-id="81dd7-110">Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.</span><span class="sxs-lookup"><span data-stu-id="81dd7-110">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="81dd7-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81dd7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="81dd7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="81dd7-112">Element</span></span>|<span data-ttu-id="81dd7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="81dd7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81dd7-114">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="81dd7-114">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="81dd7-115">O elemento de nível superior para controlar a serialização XML.</span><span class="sxs-lookup"><span data-stu-id="81dd7-115">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="81dd7-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81dd7-116">Example</span></span>  
 <span data-ttu-id="81dd7-117">O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81dd7-117">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81dd7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81dd7-118">See Also</span></span>  
 <span data-ttu-id="81dd7-119"><xref:System.Xml.Serialization.XmlSchemaImporter></span><span class="sxs-lookup"><span data-stu-id="81dd7-119"><xref:System.Xml.Serialization.XmlSchemaImporter></span></span>   
 <span data-ttu-id="81dd7-120"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span><span class="sxs-lookup"><span data-stu-id="81dd7-120"><xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode></span></span>   
 <span data-ttu-id="81dd7-121">[Esquema de arquivo de configuração](../../../docs/framework/configure-apps/file-schema/index.md) </span><span class="sxs-lookup"><span data-stu-id="81dd7-121">[Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md) </span></span>  
 <span data-ttu-id="81dd7-122">[\<Elemento dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md) </span><span class="sxs-lookup"><span data-stu-id="81dd7-122">[\<dateTimeSerialization> Element](../../../docs/standard/serialization/datetimeserialization-element.md) </span></span>  
 <span data-ttu-id="81dd7-123">[Elemento \<add> para \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md) </span><span class="sxs-lookup"><span data-stu-id="81dd7-123">[\<add> Element for \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md) </span></span>  
 [<span data-ttu-id="81dd7-124">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="81dd7-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)

