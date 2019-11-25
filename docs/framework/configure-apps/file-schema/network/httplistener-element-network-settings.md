---
title: Elemento <httpListener> (Configurações de Rede)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088382"
---
# <a name="httplistener-element-network-settings"></a>\<o elemento > httpListener (configurações de rede)
Personaliza os parâmetros usados pela classe <xref:System.Net.HttpListener>.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**configurações**](settings-element-network-settings.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**httpListener >**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Digite  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|unescapeRequestUrl|Um valor booliano que indica se uma instância de <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Configurações](settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 O atributo **unescapeRequestUrl** indica se <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido em que quaisquer valores codificados por porcentagem são convertidos e outras etapas de normalização são feitas.  
  
 Quando uma instância de <xref:System.Net.HttpListener> recebe uma solicitação por meio do serviço de `http.sys`, ela cria uma instância da cadeia de caracteres de URI fornecida pelo `http.sys`e a expõe como a propriedade <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.  
  
 O serviço de `http.sys` expõe duas cadeias de caracteres de URI de solicitação:  
  
- URI bruto  
  
- URI convertido  
  
 O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima é "/Path/". Isso representa a cadeia de caracteres após o verbo HTTP, pois ele foi enviado pela rede.  
  
 O serviço de `http.sys` cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha de solicitação HTTP e o cabeçalho de host para determinar o servidor de origem para o qual a solicitação deve ser encaminhada. Isso é feito comparando as informações da solicitação com um conjunto de prefixos de URI registrados. A documentação do SDK do servidor HTTP refere-se a esse URI convertido como a estrutura de HTTP_COOKED_URL.  
  
 Para poder comparar a solicitação com prefixos de URI registrados, é necessário fazer alguma normalização na solicitação. Para o exemplo acima, o URI convertido seria o seguinte:  
  
 `http://www.contoso.com/path/`  
  
 O serviço `http.sys` combina o valor da propriedade <xref:System.Uri.Host%2A?displayProperty=nameWithType> e a cadeia de caracteres na linha de solicitação para criar um URI convertido. Além disso, `http.sys` e a classe <xref:System.Uri?displayProperty=nameWithType> também faz o seguinte:  
  
- Cancela o escape de todos os valores codificados por porcentagem.  
  
- Converte caracteres não ASCII codificados por porcentagem em uma representação de caractere UTF-16. Observe que os caracteres UTF-8 e ANSI/DBCS têm suporte, bem como caracteres Unicode (codificação Unicode usando o formato% uXXXX).  
  
- Executa outras etapas de normalização, como compactação de caminho.  
  
 Como a solicitação não contém informações sobre a codificação usada para valores codificados por porcentagem, talvez não seja possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.  
  
 Portanto `http.sys` fornece duas chaves do registro para modificar o processo:  
  
|Chave do Registro|Valor padrão|Descrição|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Se for zero, `http.sys` aceitará somente URLs codificadas em UTF-8.<br /><br /> Se for diferente de zero, `http.sys` também aceitará URLs codificadas por ANSI ou DBCS em solicitações.|  
|FavorUTF8|1|Se for diferente de zero, `http.sys` sempre tentará decodificar uma URL como UTF-8 primeiro; Se essa conversão falhar e EnableNonUTF8 for diferente de zero, o http. sys tentará decodificá-la como ANSI ou DBCS.<br /><br /> Se zero (e EnableNonUTF8 for diferente de zero), `http.sys` tentará decodificá-lo como ANSI ou DBCS; Se isso não for bem-sucedido, ele tentará uma conversão UTF-8.|  
  
 Quando <xref:System.Net.HttpListener> recebe uma solicitação, ela usa o URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 Há uma necessidade de dar suporte a caracteres além de caracteres e números em URIs. Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o número de cliente "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Observe a barra codificada por porcentagem no URI (% 2F). Isso é necessário, pois, nesse caso, o caractere de barra representa dados e não um delimitador de caminho.  
  
 Passar a cadeia de caracteres para o construtor de URI resultará no seguinte URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dividir o caminho em seus segmentos resultaria nos seguintes elementos:  
  
 `Customer('1`  
  
 `3812')`  
  
 Essa não é a intenção do remetente da solicitação.  
  
 Se o atributo **unescapeRequestUrl** for definido como **false**, quando o <xref:System.Net.HttpListener> receber uma solicitação, ele usará o URI bruto em vez do URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 O valor padrão para o atributo **unescapeRequestUrl** é **true**.  
  
 A propriedade <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> pode ser usada para obter o valor atual do atributo **unescapeRequestUrl** dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar a classe <xref:System.Net.HttpListener> quando ela recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
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
|espaço de nome|System.Net|  
|Nome do esquema||  
|Arquivo de validação||  
|Pode estar vazio||  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Esquema de configurações de rede](index.md)
