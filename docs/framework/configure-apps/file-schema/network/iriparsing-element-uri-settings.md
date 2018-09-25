---
title: '&lt;iriParsing&gt; (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 446447f0d279755dbc06e0e3a25d50ad86ad555b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075209"
---
# <a name="ltiriparsinggt-element-uri-settings"></a>&lt;iriParsing&gt; (configurações de Uri)
Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.  
  
## <a name="schema-hierarchy"></a>Hierarquia de esquema  
 [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<URI > (configurações de Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|`enabled`|Especifica se a análise de IRI está habilitada. O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).|  
  
## <a name="remarks"></a>Comentários  
 Existente <xref:System.Uri> classe foi estendido no .NET Framework 3.5. 3.0 SP1 e 2.0 SP1 para fornecer suporte a identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizado (IDN). Os usuários atuais não verão qualquer mudança do comportamento do .NET Framework 2.0, a menos que eles especificamente habilitarem IRI e IDN dão suporte. Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.  
  
 Para habilitar o suporte IRI, duas alterações a seguir são necessárias:  
  
1.  Adicione a seguinte linha ao arquivo Machine. config no diretório do .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  Especifique se as regras de análise de IRI deve ser aplicada. Isso pode ser feito no arquivo machine.config ou em app.config.  
  
 Habilitar a análise de IRI (iriParsing habilitado = `true`) executará a normalização e regras de caractere de verificação de acordo com a mais recentes de IRI na RFC 3987. O valor padrão é `false` e normalização e verificação de acordo com RFC 2396 e RFC 3986 de caracteres (para literais IPv6).  
  
### <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte à análise de IRI e nomes IDN.  
  
### <a name="code"></a>Código  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
