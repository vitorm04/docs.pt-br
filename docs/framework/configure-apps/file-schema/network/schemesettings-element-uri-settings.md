---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 498aef77a1dfd8cffcac73b704b8d1bb6df5d165
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697766"
---
# <a name="schemesettings-element-uri-settings"></a>\<elemento de > schemeSettings (configurações de URI)
Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.  
  
[ **\<configuration>** ](../configuration-element.md)  
URI de\<de &nbsp;de &nbsp;[ **>** ](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<schemeSettings >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[add](add-element-for-schemesettings-uri-settings.md)|Adiciona uma configuração de esquema para um nome de esquema.|  
|[clear](clear-element-for-schemesettings-uri-settings.md)|Limpa todas as configurações de esquema existentes.|  
|[remove](remove-element-for-schemesettings-uri-settings.md)|Remove uma configuração de esquema para um nome de esquema.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, a classe <xref:System.Uri?displayProperty=nameWithType> não escapa os delimitadores de caminho codificados por porcentagem antes de executar a compactação de caminho. Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Se esse URI for passado para os módulos que não manipulam a porcentagem de caracteres codificados corretamente, isso pode fazer com que o seguinte comando seja executado pelo servidor:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe primeiro cancela o escape dos delimitadores de caminho e, em seguida, aplica a compactação de caminho. O resultado da passagem da URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> Construtor de classe resulta no seguinte URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Esse comportamento padrão pode ser modificado para não cancelar o escape de delimitadores de caminho codificados por porcentagem usando a opção de configuração schemeSettings para um esquema específico.  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte a não escapar delimitadores de caminho codificados por porcentagem para o esquema http.  
  
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
|{1&gt;Namespace&lt;1}|{1&gt;Sistema&lt;1}|  
|Schema Name||  
|Arquivo de validação||  
|Pode estar vazio||  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
