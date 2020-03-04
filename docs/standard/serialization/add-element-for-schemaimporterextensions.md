---
title: Elemento <add> para <schemaImporterExtensions>
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159930"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="b77c8-102">\<Adicionar > elemento para \<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="b77c8-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="b77c8-103">Adiciona tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b77c8-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="b77c8-104">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="b77c8-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="b77c8-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b77c8-105">\<configuration></span></span>  
<span data-ttu-id="b77c8-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="b77c8-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="b77c8-107">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="b77c8-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="b77c8-108">\<add></span><span class="sxs-lookup"><span data-stu-id="b77c8-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b77c8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b77c8-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b77c8-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b77c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b77c8-111">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="b77c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b77c8-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b77c8-112">Attributes</span></span>  
  
|<span data-ttu-id="b77c8-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b77c8-113">Attribute</span></span>|<span data-ttu-id="b77c8-114">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="b77c8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b77c8-115">**name**</span><span class="sxs-lookup"><span data-stu-id="b77c8-115">**name**</span></span>|<span data-ttu-id="b77c8-116">Um nome simples que é usado para localizar a instância.</span><span class="sxs-lookup"><span data-stu-id="b77c8-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="b77c8-117">**tipo**</span><span class="sxs-lookup"><span data-stu-id="b77c8-117">**type**</span></span>|<span data-ttu-id="b77c8-118">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="b77c8-118">Required.</span></span> <span data-ttu-id="b77c8-119">Especifica a classe de extensão de esquema para adicionar.</span><span class="sxs-lookup"><span data-stu-id="b77c8-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="b77c8-120">O valor de atributo **type** deve ser uma linha e incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="b77c8-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="b77c8-121">Quando o assembly é colocado no GAC (cache de assembly global), ele também deve incluir a versão, cultura e token de chave pública do assembly assinado.</span><span class="sxs-lookup"><span data-stu-id="b77c8-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b77c8-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b77c8-122">Child Elements</span></span>  
 <span data-ttu-id="b77c8-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b77c8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b77c8-124">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="b77c8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b77c8-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b77c8-125">Element</span></span>|<span data-ttu-id="b77c8-126">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="b77c8-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b77c8-127">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="b77c8-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="b77c8-128">Contém tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="b77c8-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b77c8-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b77c8-129">Example</span></span>  
 <span data-ttu-id="b77c8-130">O exemplo de código a seguir adiciona um tipo de extensão que o XmlSchemaImporter pode usar ao mapear tipos.</span><span class="sxs-lookup"><span data-stu-id="b77c8-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b77c8-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="b77c8-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="b77c8-132">\<Elemento system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="b77c8-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- <span data-ttu-id="b77c8-133">Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span><span class="sxs-lookup"><span data-stu-id="b77c8-133">[\<schemaImporterExtensions> Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)</span></span>
