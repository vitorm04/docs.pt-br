---
title: Elemento <add> para <schemaImporterExtensions>
description: O <add> elemento Adiciona tipos usados pela classe XmlSchemaImporter para mapear tipos XSD para .NET Framework tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378476"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="e58fc-103">\<Adicionar> elemento para \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="e58fc-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="e58fc-104">Adiciona tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e58fc-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="e58fc-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="e58fc-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="e58fc-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e58fc-106">\<configuration></span></span>  
<span data-ttu-id="e58fc-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="e58fc-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="e58fc-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="e58fc-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="e58fc-109">\<add></span><span class="sxs-lookup"><span data-stu-id="e58fc-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58fc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e58fc-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e58fc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e58fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e58fc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e58fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e58fc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e58fc-113">Attributes</span></span>  
  
|<span data-ttu-id="e58fc-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="e58fc-114">Attribute</span></span>|<span data-ttu-id="e58fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58fc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e58fc-116">**name**</span><span class="sxs-lookup"><span data-stu-id="e58fc-116">**name**</span></span>|<span data-ttu-id="e58fc-117">Um nome simples que é usado para localizar a instância.</span><span class="sxs-lookup"><span data-stu-id="e58fc-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="e58fc-118">**tipo**</span><span class="sxs-lookup"><span data-stu-id="e58fc-118">**type**</span></span>|<span data-ttu-id="e58fc-119">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="e58fc-119">Required.</span></span> <span data-ttu-id="e58fc-120">Especifica a classe de extensão de esquema para adicionar.</span><span class="sxs-lookup"><span data-stu-id="e58fc-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="e58fc-121">O valor de atributo **type** deve ser uma linha e incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="e58fc-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="e58fc-122">Quando o assembly é colocado no GAC (cache de assembly global), ele também deve incluir a versão, cultura e token de chave pública do assembly assinado.</span><span class="sxs-lookup"><span data-stu-id="e58fc-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e58fc-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e58fc-123">Child Elements</span></span>  
 <span data-ttu-id="e58fc-124">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e58fc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e58fc-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e58fc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e58fc-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e58fc-126">Element</span></span>|<span data-ttu-id="e58fc-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58fc-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e58fc-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="e58fc-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="e58fc-129">Contém tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="e58fc-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e58fc-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e58fc-130">Example</span></span>  
 <span data-ttu-id="e58fc-131">O exemplo de código a seguir adiciona um tipo de extensão que o XmlSchemaImporter pode usar ao mapear tipos.</span><span class="sxs-lookup"><span data-stu-id="e58fc-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e58fc-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="e58fc-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="e58fc-133">\<Elemento de> System. xml. Serialization</span><span class="sxs-lookup"><span data-stu-id="e58fc-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="e58fc-134">\<Elemento de> schemaImporterExtensions</span><span class="sxs-lookup"><span data-stu-id="e58fc-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
