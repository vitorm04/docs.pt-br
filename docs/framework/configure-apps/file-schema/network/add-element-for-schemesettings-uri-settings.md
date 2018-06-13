---
title: '&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd8033b07b29066633e5217645f3ee06937179da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741848"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a>&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)
Adiciona uma configuração de esquema para um nome de esquema.  
  
 \<configuration>  
\<URI >  
\<schemeSettings >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|O nome do esquema para o qual essa configuração se aplica. A apenas os valores com suporte são nome = "http" e o nome = "https".|  
  
## <a name="attribute-name-attribute"></a>{Nome do atributo} Atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|genericUriParserOptions|As opções de analisador para este esquema. O somente valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]|Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento de escapa Cancelar classe codificado delimitadores de caminho antes de executar a compactação de caminho. Isso foi implementado como um mecanismo de segurança contra ataques semelhante ao seguinte:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Se esse URI é passado para módulos não tratamento % caracteres codificados corretamente, isso poderia resultar no comando a seguir, que está sendo executado pelo servidor:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe delimitadores de caminho escapes cancelar primeiro e, em seguida, aplica-se a compactação de caminho. O resultado de passar a URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a saída não delimitadores de caminho codificados por percentual para o esquema http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
