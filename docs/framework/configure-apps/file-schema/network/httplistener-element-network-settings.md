---
title: "&lt;httpListener&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14a758f1d69da4db8ed58809de20d3522ea7e4e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; elemento (configurações de rede)
Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.  
  
 \<configuration>  
\<System.NET >  
\<Configurações >  
\<httpListener >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Tipo  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|unescapeRequestUrl|Um valor booliano que indica se um <xref:System.Net.HttpListener> instância usa o URI de escape bruto em vez do URI convertido.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Configurações](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 O **unescapeRequestUrl** atributo indica se <xref:System.Net.HttpListener> usa o URI de escape bruto em vez do URI convertido em que quaisquer valores codificados por percentual são convertidos e outras etapas de normalização são obtidas.  
  
 Quando um <xref:System.Net.HttpListener> instância recebe uma solicitação por meio de `http.sys` serviço, ele cria uma instância da cadeia de caracteres URI fornecida pelo `http.sys`e o expõe como o <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriedade.  
  
 O `http.sys` serviço expõe duas cadeias de caracteres URI de solicitação:  
  
-   URI bruto  
  
-   URI convertido  
  
 O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima, é "/ caminho /". Isso representa a cadeia de caracteres após o verbo HTTP, como ele foi enviado pela rede.  
  
 O `http.sys` serviço cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha da solicitação HTTP e o cabeçalho de Host para determinar a solicitação do servidor de origem deve ser encaminhado. Isso é feito comparando as informações da solicitação com um conjunto de prefixos registrados do URI. A documentação do SDK do servidor HTTP se refere a esse URI convertido como a estrutura HTTP_COOKED_URL.  
  
 Para poder comparar a solicitação com prefixos registrados do URI, alguns normalização para a solicitação precisa ser feito. Para o exemplo acima convertido URI seria a seguinte:  
  
 `http://www.contoso.com/path/`  
  
 O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> o valor da propriedade e a cadeia de caracteres na linha da solicitação para criar um URI convertido. Além disso, `http.sys` e <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:  
  
-   Cancelar-ignora a porcentagem de todos os valores codificados.  
  
-   Converte codificados por percentual contém caracteres não ASCII em uma representação de caractere UTF-16. Observe que há suporte para caracteres UTF-8 e ANSI DBCS, bem como caracteres Unicode (codificação Unicode usando o formato de uXXXX %).  
  
-   Executa outras etapas de normalização, como compactação de caminho.  
  
 Desde que a solicitação não contém todas as informações sobre a codificação usada para valores codificados por percentual, pode não ser possível determinar a codificação correta analisando apenas os valores codificados por porcentagem.  
  
 Portanto, `http.sys` fornece duas chaves do registro para modificar o processo:  
  
|Chave do Registro|Valor padrão|Descrição|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Se for zero, `http.sys` aceita apenas as URLs codificados em UTF-8.<br /><br /> Se diferente de zero, `http.sys` também aceita URLs codificado em ANSI ou DBCS codificado em solicitações.|  
|FavorUTF8|1|Se diferente de zero, `http.sys` sempre tenta decodificar uma URL como UTF-8 primeiro; se a conversão falhará e EnableNonUTF8 é diferente de zero, o HTTP. sys, em seguida, tenta decodificá-la como ANSI ou DBCS.<br /><br /> Se for zero (e EnableNonUTF8 é diferente de zero), `http.sys` tenta decodificá-la como ANSI ou DBCS; se esse não for bem-sucedida, ele tenta uma conversão de UTF-8.|  
  
 Quando <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI convertido do `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
 É necessário para dar suporte a caracteres além de caracteres e números nos URIs. Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o cliente número "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Observe a barra codificados por percentual no Uri (% 2F). Isso é necessário, pois, nesse caso o caractere de barra representa dados e não um delimitador de caminho.  
  
 Passando a cadeia de caracteres de construtor Uri levará para o seguinte URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dividir o caminho em seus segmentos resultaria nos seguintes elementos:  
  
 `Customer('1`  
  
 `3812')`  
  
 Isso não é a intenção do remetente da solicitação.  
  
 Se o **unescapeRequestUrl** atributo é definido como **false**, quando o <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI bruto em vez do URI convertido do `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
 O valor padrão para o **unescapeRequestUrl** atributo é **true**.  
  
 O <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do **unescapeRequestUrl** atributo dos arquivos de configuração aplicável.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o <xref:System.Net.HttpListener> classe quando ele recebe uma solicitação para usar o URI bruto em vez do URI convertido do `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>Informações do elemento  
  
|||
|-|-|  
|Namespace|System.Net|  
|Nome do esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
