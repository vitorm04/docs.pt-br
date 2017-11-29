---
title: Elemento &lt;add&gt; de &lt;xmlSchemaImporterExtensions&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 766d04dd792534f0da33116ed959d81ff376e026
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="2d9c3-102">Elemento &lt;add&gt; de &lt;xmlSchemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="2d9c3-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="2d9c3-103">Adiciona tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="2d9c3-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d9c3-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="2d9c3-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2d9c3-105">\<configuration></span></span>  
<span data-ttu-id="2d9c3-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="2d9c3-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="2d9c3-107">\<XmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="2d9c3-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="2d9c3-108">\<add></span><span class="sxs-lookup"><span data-stu-id="2d9c3-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9c3-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d9c3-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d9c3-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2d9c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2d9c3-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d9c3-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2d9c3-112">Attributes</span></span>  
  
|<span data-ttu-id="2d9c3-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2d9c3-113">Attribute</span></span>|<span data-ttu-id="2d9c3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d9c3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d9c3-115">**name**</span><span class="sxs-lookup"><span data-stu-id="2d9c3-115">**name**</span></span>|<span data-ttu-id="2d9c3-116">Um nome simples que é usado para localizar a instância.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="2d9c3-117">**type**</span><span class="sxs-lookup"><span data-stu-id="2d9c3-117">**type**</span></span>|<span data-ttu-id="2d9c3-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-118">Required.</span></span> <span data-ttu-id="2d9c3-119">Especifica a classe de extensão de esquema para adicionar.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="2d9c3-120">O valor de atributo **type** deve ser uma linha e incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="2d9c3-121">Quando o assembly é colocado no GAC (cache de assembly global), ele também deve incluir a versão, cultura e token de chave pública do assembly assinado.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d9c3-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2d9c3-122">Child Elements</span></span>  
 <span data-ttu-id="2d9c3-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d9c3-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2d9c3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2d9c3-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="2d9c3-125">Element</span></span>|<span data-ttu-id="2d9c3-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d9c3-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d9c3-127">\<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="2d9c3-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="2d9c3-128">Contém tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2d9c3-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d9c3-129">Example</span></span>  
 <span data-ttu-id="2d9c3-130">O exemplo de código a seguir adiciona um tipo de extensão que o XmlSchemaImporter pode usar ao mapear tipos.</span><span class="sxs-lookup"><span data-stu-id="2d9c3-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d9c3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d9c3-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="2d9c3-132">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="2d9c3-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="2d9c3-133">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d9c3-133">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>
