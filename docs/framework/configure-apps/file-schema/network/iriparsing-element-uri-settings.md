---
title: Elemento <iriParsing> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698100"
---
# <a name="iriparsing-element-uri-settings"></a>\<elemento de > iriParsing (configurações de URI)
Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.  
  
[ **\<configuration>** ](../configuration-element.md)  
URI de\<de &nbsp;de &nbsp;[ **>** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<iriParsing >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|`enabled`|Especifica se a análise de IRI está habilitada. O valor padrão é `false`.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).|  
  
## <a name="remarks"></a>Comentários  
 A classe de <xref:System.Uri> existente foi estendida em .NET Framework 3,5. 3,0 SP1 e 2,0 SP1 para fornecer suporte para IRI (identificadores de recursos internacionais) e IDNs (nomes de domínio internacionalizados). Os usuários atuais não verão nenhuma alteração do comportamento .NET Framework 2,0, a menos que eles especificamente habilitem o suporte a IRI e IDN. Isso garante a compatibilidade do aplicativo com versões anteriores do .NET Framework.  
  
 Para habilitar o suporte para IRI, as duas alterações a seguir são necessárias:  
  
1. Adicione a seguinte linha ao arquivo Machine. config no diretório .NET Framework 2,0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Especifique se as regras de análise de IRI devem ser aplicadas. Isso pode ser feito no arquivo machine.config ou em app.config.  
  
 Habilitar a análise de IRI (iriParsing Enabled = `true`) fará a normalização e a verificação de caracteres de acordo com as regras de IRI mais recentes no RFC 3987. O valor padrão é `false` e fará a normalização e a verificação de caracteres de acordo com RFC 2396 e RFC 3986 (para literais IPv6).  
  
### <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte a análise IRI e nomes IDN.  
  
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
- [Esquema de configurações de rede](index.md)
