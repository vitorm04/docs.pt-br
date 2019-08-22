---
title: Elemento <httpListener> (Configurações de Rede)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: cb24dc7296e2f2f6ea292566330d3d6ae4f25f85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664134"
---
# <a name="httplistener-element-network-settings"></a>\<Elemento > httpListener (configurações de rede)
Personaliza os <xref:System.Net.HttpListener> parâmetros usados pela classe.  
  
 \<configuration>  
\<system.net>  
\<> de configurações  
\<httpListener>  
  
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
|unescapeRequestUrl|Um valor booliano que indica se <xref:System.Net.HttpListener> uma instância usa o URI sem escape bruto em vez do URI convertido.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 O atributo **unescapeRequestUrl** indica se <xref:System.Net.HttpListener> o usa o URI sem escape bruto em vez do URI convertido em que os valores codificados por porcentagem são convertidos e outras etapas de normalização são feitas.  
  
 Quando uma <xref:System.Net.HttpListener> instância recebe uma solicitação por meio `http.sys` do serviço, ela cria uma instância da cadeia de caracteres de `http.sys`URI fornecida pelo e a expõe <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> como a propriedade.  
  
 O `http.sys` serviço expõe duas cadeias de caracteres de URI de solicitação:  
  
- URI bruto  
  
- URI convertido  
  
 O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação http:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima é "/Path/". Isso representa a cadeia de caracteres após o verbo HTTP, pois ele foi enviado pela rede.  
  
 O `http.sys` serviço cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha de solicitação HTTP e o cabeçalho do host para determinar o servidor de origem para o qual a solicitação deve ser encaminhada. Isso é feito comparando as informações da solicitação com um conjunto de prefixos de URI registrados. A documentação do SDK do servidor HTTP refere-se a esse URI convertido como a estrutura HTTP_COOKED_URL.  
  
 Para poder comparar a solicitação com prefixos de URI registrados, é necessário fazer alguma normalização na solicitação. Para o exemplo acima, o URI convertido seria o seguinte:  
  
 `http://www.contoso.com/path/`  
  
 O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> valor da propriedade e a cadeia de caracteres na linha de solicitação para criar um URI convertido. Além disso, `http.sys` e a <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:  
  
- Cancela o escape de todos os valores codificados por porcentagem.  
  
- Converte caracteres não ASCII codificados por porcentagem em uma representação de caractere UTF-16. Observe que os caracteres UTF-8 e ANSI/DBCS têm suporte, bem como caracteres Unicode (codificação Unicode usando o formato% uXXXX).  
  
- Executa outras etapas de normalização, como compactação de caminho.  
  
 Como a solicitação não contém informações sobre a codificação usada para valores codificados por porcentagem, talvez não seja possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.  
  
 Portanto `http.sys` , o fornece duas chaves do registro para modificar o processo:  
  
|Chave do Registro|Valor padrão|Descrição|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Se zero, `http.sys` aceitará somente URLs codificadas em UTF-8.<br /><br /> Se for diferente de zero `http.sys` , o também aceitará URLs codificadas por ANSI ou DBCS em solicitações.|  
|FavorUTF8|1|Se for diferente de zero `http.sys` , sempre tentará decodificar uma URL como UTF-8 primeiro; se essa conversão falhar e EnableNonUTF8 for diferente de zero, o http. sys tentará decodificá-la como ANSI ou DBCS.<br /><br /> Se zero (e EnableNonUTF8 for diferente de zero), `http.sys` o tentará decodificá-lo como ANSI ou DBCS; se isso não for bem-sucedido, ele tentará uma conversão UTF-8.|  
  
 Quando <xref:System.Net.HttpListener> o recebe uma solicitação, ele usa o URI convertido `http.sys` de como entrada para <xref:System.Net.HttpListenerRequest.Url%2A> a propriedade.  
  
 Há uma necessidade de dar suporte a caracteres além de caracteres e números em URIs. Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o número de cliente "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Observe a barra codificada por porcentagem no URI (% 2F). Isso é necessário, pois, nesse caso, o caractere de barra representa dados e não um delimitador de caminho.  
  
 Passar a cadeia de caracteres para o construtor de URI resultará no seguinte URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dividir o caminho em seus segmentos resultaria nos seguintes elementos:  
  
 `Customer('1`  
  
 `3812')`  
  
 Essa não é a intenção do remetente da solicitação.  
  
 Se o atributo **unescapeRequestUrl** for definido como **false**, quando o <xref:System.Net.HttpListener> receber uma solicitação, ele usará o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
 O valor padrão para o atributo **unescapeRequestUrl** é **true**.  
  
 A <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do atributo **unescapeRequestUrl** dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar a <xref:System.Net.HttpListener> classe quando ela recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
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
|Pode estar vazio||  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Esquema de configurações de rede](index.md)
