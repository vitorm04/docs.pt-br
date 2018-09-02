---
title: Elemento &lt;system.xml.serialization&gt;
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: bf84c412c2d5e3c75cfdc752eeb70239f23d9245
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421836"
---
# <a name="ltsystemxmlserializationgt-element"></a>Elemento &lt;system.xml.serialization&gt;
O elemento de nível superior para controlar a serialização XML. Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)|Determina o modo de serialização de objetos <xref:System.DateTime>.|  
|Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Contém tipos que são usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra como especificar o modo de serialização de um objeto <xref:System.DateTime> e a adição de tipos usada pelo <xref:System.Xml.Serialization.XmlSchemaImporter> ao mapear os tipos XSD para os tipos do .NET Framework.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)  
 Elemento [\<dateTimeSerialization>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<Adicionar > elemento para \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
