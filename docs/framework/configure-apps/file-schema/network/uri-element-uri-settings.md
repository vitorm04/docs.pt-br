---
title: '&lt;URI&gt; elemento (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 05b2fb4255643f657f37012ec51a1b29ed68095d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742803"
---
# <a name="lturigt-element-uri-settings"></a>&lt;URI&gt; elemento (configurações de Uri)
Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).  
  
## <a name="schema-hierarchy"></a>Hierarquia de esquema  
 [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<URI >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[IDN](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Especifica se a análise de identificador de recurso internacional (IRI) é aplicada a <xref:System.Uri> e se as regras de análise de IRI deve ser aplicada.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Configuração](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Contém configurações para todos os namespaces.|  
  
## <a name="remarks"></a>Comentários  
 O `uri` elemento contém configurações para membros a <xref:System.Uri> classe usada por classes no <xref:System.Net> namespace. As configurações de configuram o suporte para IRI e IDN.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a análise de IRI e nomes IDN. O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para a saída não delimitadores de caminho codificados por percentual para o esquema http.  
  
### <a name="code"></a>Código  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
