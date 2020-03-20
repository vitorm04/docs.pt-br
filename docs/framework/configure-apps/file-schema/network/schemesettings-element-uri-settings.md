---
title: Elemento <schemeSettings> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154641"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings> Element (Uri Settings) [Elemento schemeSettings> (configurações de URI)]
Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<esquemaConfigurações>**  
  
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
|[adicionar](add-element-for-schemesettings-uri-settings.md)|Adiciona uma configuração de esquema para um nome de esquema.|  
|[Claro](clear-element-for-schemesettings-uri-settings.md)|Limpa todas as configurações de esquema existentes.|  
|[remover](remove-element-for-schemesettings-uri-settings.md)|Remove uma configuração de esquema para um nome de esquema.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Uri](uri-element-uri-settings.md)|Contém configurações que especificam como o .NET Framework lida com endereços da Web expressos usando URIs (Uniform Resource Identifiers).|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, <xref:System.Uri?displayProperty=nameWithType> a classe desescapa por cento delimitadores de caminho codificados antes de executar a compactação do caminho. Isso foi implementado como um mecanismo de segurança contra ataques como o seguinte:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Se esse URI for repassado para módulos que não lidam com caracteres codificados por porcentagem corretamente, isso pode resultar na execução do seguinte comando pelo servidor:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Por essa <xref:System.Uri?displayProperty=nameWithType> razão, a classe primeiro desescapa delimitadores do caminho e, em seguida, aplica compactação de caminho. O resultado da passagem da <xref:System.Uri?displayProperty=nameWithType> URL maliciosa acima para o construtor de classe resulta no seguinte URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Esse comportamento padrão pode ser modificado para não delimitar delimitadores de caminho codificados por porcentagem de desfugação usando a opção de configuração schemeSettings para um esquema específico.  
  
## <a name="configuration-files"></a>Arquivos de configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra <xref:System.Uri> uma configuração usada pela classe para suportar não escapar de limitadores de caminho codificados por cento para o esquema http.  
  
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
|Nome do Esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Confira também

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
