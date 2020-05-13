---
title: Elemento <schemaImporterExtensions>
description: O <schemaImporterExtensions> elemento contém tipos que são usados pelo XmlSchemaImporter para mapeamento de tipos XSD para .NET Framework tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379797"
---
# <a name="schemaimporterextensions-element"></a>Elemento \<schemaImporterExtensions>
Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework. Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Adicionar> elemento para \< schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|Adiciona tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter> para criar mapeamentos.|  
  
## <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Elemento de> System. xml. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)|O elemento de nível superior para controlar a serialização XML.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra como adicionar tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Esquema do arquivo de configuração](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<Elemento de> dateTimeSerialization](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<Adicionar> elemento para \< schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<Elemento de> System. xml. Serialization](../../../docs/standard/serialization/system-xml-serialization-element.md)
