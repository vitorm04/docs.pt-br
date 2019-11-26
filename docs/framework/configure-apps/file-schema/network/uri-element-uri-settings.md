---
title: Elemento <uri> (Configurações de URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697435"
---
# <a name="uri-element-uri-settings"></a>Elemento de > URI de \<(configurações de URI)
Contém configurações que especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes).  
  
[ **\<configuration>** ](../configuration-element.md)  
URI de **\<** de &nbsp;de &nbsp;>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  
 None.  
  
### <a name="child-elements"></a>Elementos filho  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[idn](idn-element-uri-settings.md)|Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.|  
|[iriParsing](iriparsing-element-uri-settings.md)|Especifica se a análise do IRI (identificador de recurso internacional) é aplicada ao <xref:System.Uri> e se as regras de análise do IRI devem ser aplicadas.|  
|[schemeSettings](schemesettings-element-uri-settings.md)|Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[configuração](../configuration-element.md)|Contém configurações para todos os namespaces.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `uri` contém configurações para membros da classe <xref:System.Uri> usada por classes no namespace <xref:System.Net>. As configurações configuram o suporte para IRI e IDN.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma configuração usada pela classe <xref:System.Uri> para dar suporte a análise IRI e nomes IDN. O exemplo também limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escape de delimitadores de caminho codificados por porcentagem para o esquema http.  
  
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

- [Esquema de configurações de rede](index.md)
