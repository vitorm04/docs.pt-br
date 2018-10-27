---
title: '&lt;httpListener&gt; (configurações de rede)'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3daf18fab81ea481be8e45e4d9ad682047ada6f3
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50042630"
---
# <a name="lthttplistenergt-element-network-settings"></a>&lt;httpListener&gt; (configurações de rede)
Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.  
  
 \<configuration>  
\<system.net>  
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
|unescapeRequestUrl|Um valor booliano que indica se um <xref:System.Net.HttpListener> instância usa o URI sem escape bruto em vez do URI convertido.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
 O **unescapeRequestUrl** atributo indica se <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido em que todos os valores codificados por porcentagem são convertidos e outras etapas de normalização são obtidas.  
  
 Quando um <xref:System.Net.HttpListener> instância recebe uma solicitação por meio de `http.sys` serviço, ele cria uma instância da cadeia de caracteres URI fornecida pelo `http.sys`e o expõe como o <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriedade.  
  
 O `http.sys` serviço expõe duas cadeias de caracteres URI de solicitação:  
  
-   URI bruto  
  
-   URI convertido  
  
 O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação HTTP:  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima, é "/ caminho /". Isso representa a cadeia de caracteres após o verbo HTTP, como ele foi enviado pela rede.  
  
 O `http.sys` serviço cria um URI convertido das informações fornecidas na solicitação usando o URI fornecido na linha da solicitação HTTP e o cabeçalho de Host para determinar o servidor de origem da solicitação deve ser encaminhado. Isso é feito comparando as informações da solicitação com um conjunto de prefixos URI registrados. A documentação do SDK do servidor HTTP se refere a esse URI convertido como a estrutura HTTP_COOKED_URL.  
  
 Para poder comparar a solicitação com prefixos URI registrados, alguns normalização para a solicitação precisa ser feito. Para o exemplo acima do URI convertido seria da seguinte maneira:  
  
 `http://www.contoso.com/path/`  
  
 O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> valor da propriedade e a cadeia de caracteres na linha da solicitação para criar um URI convertido. Além disso, `http.sys` e o <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:  
  
-   Un-escapa o percentual de todos os valores codificados.  
  
-   Caracteres não ASCII de converte codificados por porcentagem em uma representação de caractere UTF-16. Observe que há suporte para caracteres UTF-8 e ANSI DBCS, bem como caracteres Unicode (codificação Unicode usando o formato de uXXXX %).  
  
-   Executa outras etapas de normalização, como a compactação de caminho.  
  
 Uma vez que a solicitação não contém todas as informações sobre a codificação usada para valores codificados por percentual, não é possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.  
  
 Portanto `http.sys` fornece duas chaves de registro para modificar o processo:  
  
|Chave do Registro|Valor padrão|Descrição|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Se for zero, `http.sys` aceita apenas as URLs codificado em UTF-8.<br /><br /> Se diferente de zero, `http.sys` também aceita codificado em ANSI ou DBCS codificado URLs nas solicitações.|  
|FavorUTF8|1|Se diferente de zero, `http.sys` sempre tentará decodificar uma URL como UTF-8 primeiro; se essa conversão falhar e EnableNonUTF8 for diferente de zero, o HTTP. sys e tenta decodificá-lo como ANSI ou DBCS.<br /><br /> Se for zero (e EnableNonUTF8 for diferente de zero), `http.sys` tenta decodificá-lo como ANSI ou DBCS; se isso não for bem-sucedida, ele tenta uma conversão de UTF-8.|  
  
 Quando <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
 É necessário para dar suporte a caracteres além de caracteres e números em URIs. Um exemplo é o seguinte URI é usado para recuperar informações do cliente para cliente número "1/3812":  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Observe a barra codificados por porcentagem no Uri (% 2F). Isso é necessário, já que nesse caso, o caractere de barra "/" representa os dados e não um delimitador de caminho.  
  
 Passando a cadeia de caracteres para o construtor de Uri levará para o seguinte URI:  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Dividindo o caminho em seus segmentos resultaria nos seguintes elementos:  
  
 `Customer('1`  
  
 `3812')`  
  
 Isso não é a intenção do remetente da solicitação.  
  
 Se o **unescapeRequestUrl** atributo é definido como **falso**, em seguida, quando o <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI bruto em vez do URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
 O valor padrão para o **unescapeRequestUrl** atributo é **verdadeiro**.  
  
 O <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do **unescapeRequestUrl** atributo dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o <xref:System.Net.HttpListener> classe quando ele recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.  
  
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
