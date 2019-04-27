---
title: Elemento <iriParsing> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 7033f4dcda7d2fe73310ae0d36d9b05c090d13d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674513"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing > (configurações de Uri)
Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.  
  
## <a name="schema-hierarchy"></a>Hierarquia de esquema  
 [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<URI > (configurações de Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
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
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).|  
  
## <a name="remarks"></a>Comentários  
 Existente <xref:System.Uri> classe foi estendido no .NET Framework 3.5. 3.0 SP1 e 2.0 SP1 para fornecer suporte a identificadores de recursos internacionais (IRI) e nomes de domínio internacionalizado (IDN). Os usuários atuais não verão qualquer mudança do comportamento do .NET Framework 2.0, a menos que eles especificamente habilitarem IRI e IDN dão suporte. Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.  
  
 Para habilitar o suporte IRI, duas alterações a seguir são necessárias:  
  
1. Adicione a seguinte linha ao arquivo Machine. config no diretório do .NET Framework 2.0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Especifique se as regras de análise de IRI deve ser aplicada. Isso pode ser feito no arquivo machine.config ou em app.config.  
  
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

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
