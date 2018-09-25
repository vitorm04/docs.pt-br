---
title: '&lt;schemeSettings&gt; (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 76ca5acc22eca07d372a2964cf3a6df4ea3b58d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077480"
---
# <a name="ltschemesettingsgt-element-uri-settings"></a>&lt;schemeSettings&gt; (configurações de Uri)
Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.  
  
 \<configuration>  
\<URI >  
\<schemeSettings >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|Adiciona uma configuração de esquema para um nome de esquema.|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|Limpa todas as configurações existentes do esquema.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|Remove uma definição de esquema para um nome de esquema.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework controla endereços da web expressados usando identificadores de recurso uniformes (URIs).|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento un-escapes de classe codificado delimitadores de caminho antes de executar a compactação de caminho. Isso era implementado como um mecanismo de segurança contra ataques, como o seguinte:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Se esse URI é passado para baixo para módulos de manipulação não % caracteres codificados corretamente, isso poderá resultar no comando a seguir, que está sendo executado pelo servidor:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> delimitadores de caminho primeiro cancelar escapes de classe e, em seguida, aplica-se a compactação de caminho. O resultado de passar a URL mal-intencionado acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte a escape não delimitadores de caminho codificado por percentual para o esquema de http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>Informações do elemento  
  
|||
|-|-|  
|Namespace|Sistema|  
|Nome do esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
