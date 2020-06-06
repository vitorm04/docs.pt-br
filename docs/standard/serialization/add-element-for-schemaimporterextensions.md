---
title: Elemento <add> para <schemaImporterExtensions>
description: O <add> elemento Adiciona tipos usados pela classe XmlSchemaImporter para mapear tipos XSD para .NET Framework tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 6fd8113ad39a22c927035fca574151ae8f002685
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288323"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="f87f8-103">Elemento \<add> para \<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="f87f8-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="f87f8-104">Adiciona tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f87f8-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="f87f8-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="f87f8-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="f87f8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f87f8-106">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f87f8-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f87f8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f87f8-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f87f8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f87f8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f87f8-109">Attributes</span></span>  
  
|<span data-ttu-id="f87f8-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="f87f8-110">Attribute</span></span>|<span data-ttu-id="f87f8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f87f8-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f87f8-112">**name**</span><span class="sxs-lookup"><span data-stu-id="f87f8-112">**name**</span></span>|<span data-ttu-id="f87f8-113">Um nome simples que é usado para localizar a instância.</span><span class="sxs-lookup"><span data-stu-id="f87f8-113">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="f87f8-114">**tipo**</span><span class="sxs-lookup"><span data-stu-id="f87f8-114">**type**</span></span>|<span data-ttu-id="f87f8-115">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="f87f8-115">Required.</span></span> <span data-ttu-id="f87f8-116">Especifica a classe de extensão de esquema para adicionar.</span><span class="sxs-lookup"><span data-stu-id="f87f8-116">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="f87f8-117">O valor de atributo **type** deve ser uma linha e incluir o nome do tipo totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="f87f8-117">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="f87f8-118">Quando o assembly é colocado no GAC (cache de assembly global), ele também deve incluir a versão, cultura e token de chave pública do assembly assinado.</span><span class="sxs-lookup"><span data-stu-id="f87f8-118">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f87f8-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f87f8-119">Child Elements</span></span>  
 <span data-ttu-id="f87f8-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f87f8-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f87f8-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f87f8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f87f8-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f87f8-122">Element</span></span>|<span data-ttu-id="f87f8-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f87f8-123">Description</span></span>|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<span data-ttu-id="f87f8-124">Contém tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="f87f8-124">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f87f8-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f87f8-125">Example</span></span>  
 <span data-ttu-id="f87f8-126">O exemplo de código a seguir adiciona um tipo de extensão que o XmlSchemaImporter pode usar ao mapear tipos.</span><span class="sxs-lookup"><span data-stu-id="f87f8-126">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f87f8-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="f87f8-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="f87f8-128">\<system.xml.serialization>Elementos</span><span class="sxs-lookup"><span data-stu-id="f87f8-128">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="f87f8-129">\<schemaImporterExtensions>Elementos</span><span class="sxs-lookup"><span data-stu-id="f87f8-129">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
