---
title: Elemento <dateTimeSerialization>
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: af0d8eeb36e023b4d38f9ad5831de3d392a487fd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288256"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization > elemento
Determina o modo de serialização de objetos <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributos|Descrição|  
|----------------|-----------------|  
|`mode`|Opcional. Especifica o modo de serialização. Define como um dos valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>. O padrão é **RoundTrip**.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|system.xml.serialization|O elemento de nível superior para controlar a serialização XML.|  
  
## <a name="remarks"></a>Comentários  
 Em versões 1.0, 1.1, 2.0 e posteriores do .NET Framework, quando essa propriedade for definida como **Local**, os objetos <xref:System.DateTime> serão sempre formatados com a hora local. Ou seja, as informações de fuso horário local são sempre incluídas com os dados serializados. Defina essa propriedade como **Local** para garantir a compatibilidade com versões mais antigas do .NET Framework.  
  
 Na versão 2.0 e posterior do .NET Framework que têm essa propriedade definida como **Roundtrip**, os objetos <xref:System.DateTime> são sempre examinados para determinar se estão em um fuso horário local, UTC ou não especificado. Os objetos <xref:System.DateTime> são então serializados de modo que essas informações sejam preservadas. Esse é o comportamento padrão recomendado para todos os novos aplicativos que não se comunicam com versões antigas do framework.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)
- Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<Adicionar > elemento para \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<Elemento system.xml.serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
