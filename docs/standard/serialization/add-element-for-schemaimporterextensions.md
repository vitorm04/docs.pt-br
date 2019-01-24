---
title: '&lt;Adicione&gt; elemento para &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 212ce43dc50735da71091111a0fd03eca0583315
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577676"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a>&lt;Adicione&gt; elemento para &lt;schemaImporterExtensions&gt;
Adiciona tipos usados pelo <xref:System.Xml.Serialization.XmlSchemaImporter> para mapeamento de tipos XSD para tipos do .NET Framework. Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**name**|Um nome simples que é usado para localizar a instância.|  
|**type**|Necessário. Especifica a classe de extensão de esquema para adicionar. O valor de atributo **type** deve ser uma linha e incluir o nome do tipo totalmente qualificado. Quando o assembly é colocado no GAC (cache de assembly global), ele também deve incluir a versão, cultura e token de chave pública do assembly assinado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|Contém tipos que são usados pela <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir adiciona um tipo de extensão que o XmlSchemaImporter pode usar ao mapear tipos.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<Elemento system.xml.serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- Elemento [\<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
