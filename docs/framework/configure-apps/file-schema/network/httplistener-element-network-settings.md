---
title: Elemento <httpListener> (Configurações de Rede)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3f75096681ab07dd6d4788fbded5ca5c4a024aef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698189"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="8c2de-102">\<httpListener > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="8c2de-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="8c2de-103">Personaliza os parâmetros usados pela classe <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
[<span data-ttu-id="8c2de-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8c2de-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8c2de-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8c2de-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="8c2de-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8c2de-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="8c2de-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpListener >**</span><span class="sxs-lookup"><span data-stu-id="8c2de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2de-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c2de-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="8c2de-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="8c2de-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c2de-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8c2de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c2de-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8c2de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c2de-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8c2de-112">Attributes</span></span>  
  
|<span data-ttu-id="8c2de-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8c2de-113">Attribute</span></span>|<span data-ttu-id="8c2de-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c2de-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c2de-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="8c2de-115">unescapeRequestUrl</span></span>|<span data-ttu-id="8c2de-116">Um valor booliano que indica se uma instância <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido.</span><span class="sxs-lookup"><span data-stu-id="8c2de-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c2de-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8c2de-117">Child Elements</span></span>  
 <span data-ttu-id="8c2de-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8c2de-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c2de-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8c2de-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8c2de-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="8c2de-120">**Element**</span></span>|<span data-ttu-id="8c2de-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8c2de-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8c2de-122">settings</span><span class="sxs-lookup"><span data-stu-id="8c2de-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="8c2de-123">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c2de-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c2de-124">Remarks</span></span>  
 <span data-ttu-id="8c2de-125">O atributo **unescapeRequestUrl** indica se <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido em que os valores codificados por porcentagem são convertidos e outras etapas de normalização são executadas.</span><span class="sxs-lookup"><span data-stu-id="8c2de-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="8c2de-126">Quando uma instância <xref:System.Net.HttpListener> recebe uma solicitação por meio do serviço `http.sys`, ela cria uma instância da cadeia de caracteres de URI fornecida pelo `http.sys` e a expõe como a propriedade <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="8c2de-127">O serviço `http.sys` expõe duas cadeias de caracteres URI de solicitação:</span><span class="sxs-lookup"><span data-stu-id="8c2de-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="8c2de-128">URI bruto</span><span class="sxs-lookup"><span data-stu-id="8c2de-128">Raw URI</span></span>  
  
- <span data-ttu-id="8c2de-129">URI convertido</span><span class="sxs-lookup"><span data-stu-id="8c2de-129">Converted URI</span></span>  
  
 <span data-ttu-id="8c2de-130">O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação HTTP:</span><span class="sxs-lookup"><span data-stu-id="8c2de-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="8c2de-131">O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima é "/Path/".</span><span class="sxs-lookup"><span data-stu-id="8c2de-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="8c2de-132">Isso representa a cadeia de caracteres após o verbo HTTP, pois ele foi enviado pela rede.</span><span class="sxs-lookup"><span data-stu-id="8c2de-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="8c2de-133">O serviço `http.sys` cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha de solicitação HTTP e o cabeçalho do host para determinar o servidor de origem para o qual a solicitação deve ser encaminhada.</span><span class="sxs-lookup"><span data-stu-id="8c2de-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="8c2de-134">Isso é feito comparando as informações da solicitação com um conjunto de prefixos de URI registrados.</span><span class="sxs-lookup"><span data-stu-id="8c2de-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="8c2de-135">A documentação do SDK do servidor HTTP refere-se a esse URI convertido como a estrutura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="8c2de-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="8c2de-136">Para poder comparar a solicitação com prefixos de URI registrados, é necessário fazer alguma normalização na solicitação.</span><span class="sxs-lookup"><span data-stu-id="8c2de-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="8c2de-137">Para o exemplo acima, o URI convertido seria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8c2de-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="8c2de-138">O serviço `http.sys` combina o valor da propriedade <xref:System.Uri.Host%2A?displayProperty=nameWithType> e a cadeia de caracteres na linha de solicitação para criar um URI convertido.</span><span class="sxs-lookup"><span data-stu-id="8c2de-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="8c2de-139">Além disso, `http.sys` e a classe <xref:System.Uri?displayProperty=nameWithType> também faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8c2de-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="8c2de-140">Cancela o escape de todos os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="8c2de-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="8c2de-141">Converte caracteres não ASCII codificados por porcentagem em uma representação de caractere UTF-16.</span><span class="sxs-lookup"><span data-stu-id="8c2de-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="8c2de-142">Observe que os caracteres UTF-8 e ANSI/DBCS têm suporte, bem como caracteres Unicode (codificação Unicode usando o formato% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="8c2de-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="8c2de-143">Executa outras etapas de normalização, como compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="8c2de-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="8c2de-144">Como a solicitação não contém informações sobre a codificação usada para valores codificados por porcentagem, talvez não seja possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="8c2de-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="8c2de-145">Portanto, `http.sys` fornece duas chaves do registro para modificar o processo:</span><span class="sxs-lookup"><span data-stu-id="8c2de-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="8c2de-146">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="8c2de-146">Registry Key</span></span>|<span data-ttu-id="8c2de-147">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="8c2de-147">Default Value</span></span>|<span data-ttu-id="8c2de-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c2de-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="8c2de-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="8c2de-149">EnableNonUTF8</span></span>|<span data-ttu-id="8c2de-150">1</span><span class="sxs-lookup"><span data-stu-id="8c2de-150">1</span></span>|<span data-ttu-id="8c2de-151">Se zero, `http.sys` aceita somente URLs codificadas em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c2de-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="8c2de-152">Se for diferente de zero, `http.sys` também aceitará URLs codificadas por ANSI ou DBCS em solicitações.</span><span class="sxs-lookup"><span data-stu-id="8c2de-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="8c2de-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="8c2de-153">FavorUTF8</span></span>|<span data-ttu-id="8c2de-154">1</span><span class="sxs-lookup"><span data-stu-id="8c2de-154">1</span></span>|<span data-ttu-id="8c2de-155">Se for diferente de zero, `http.sys` sempre tentará decodificar uma URL como UTF-8 primeiro; Se essa conversão falhar e EnableNonUTF8 for diferente de zero, o http. sys tentará decodificá-la como ANSI ou DBCS.</span><span class="sxs-lookup"><span data-stu-id="8c2de-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="8c2de-156">Se zero (e EnableNonUTF8 for diferente de zero), `http.sys` tentará decodificá-lo como ANSI ou DBCS; Se isso não for bem-sucedido, ele tentará uma conversão UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c2de-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="8c2de-157">Quando <xref:System.Net.HttpListener> recebe uma solicitação, ela usa o URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="8c2de-158">Há uma necessidade de dar suporte a caracteres além de caracteres e números em URIs.</span><span class="sxs-lookup"><span data-stu-id="8c2de-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="8c2de-159">Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o número de cliente "1/3812":</span><span class="sxs-lookup"><span data-stu-id="8c2de-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="8c2de-160">Observe a barra codificada por porcentagem no URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="8c2de-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="8c2de-161">Isso é necessário, pois, nesse caso, o caractere de barra representa dados e não um delimitador de caminho.</span><span class="sxs-lookup"><span data-stu-id="8c2de-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="8c2de-162">Passar a cadeia de caracteres para o construtor de URI resultará no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="8c2de-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="8c2de-163">Dividir o caminho em seus segmentos resultaria nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="8c2de-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="8c2de-164">Essa não é a intenção do remetente da solicitação.</span><span class="sxs-lookup"><span data-stu-id="8c2de-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="8c2de-165">Se o atributo **unescapeRequestUrl** for definido como **false**, quando o <xref:System.Net.HttpListener> receber uma solicitação, ele usará o URI bruto em vez do URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="8c2de-166">O valor padrão para o atributo **unescapeRequestUrl** é **true**.</span><span class="sxs-lookup"><span data-stu-id="8c2de-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="8c2de-167">A propriedade <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> pode ser usada para obter o valor atual do atributo **unescapeRequestUrl** dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="8c2de-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2de-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c2de-168">Example</span></span>  
 <span data-ttu-id="8c2de-169">O exemplo a seguir mostra como configurar a classe <xref:System.Net.HttpListener> quando recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para a propriedade <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c2de-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="8c2de-170">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="8c2de-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="8c2de-171">Namespace</span><span class="sxs-lookup"><span data-stu-id="8c2de-171">Namespace</span></span>|<span data-ttu-id="8c2de-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="8c2de-172">System.Net</span></span>|  
|<span data-ttu-id="8c2de-173">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="8c2de-173">Schema Name</span></span>||  
|<span data-ttu-id="8c2de-174">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="8c2de-174">Validation File</span></span>||  
|<span data-ttu-id="8c2de-175">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="8c2de-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="8c2de-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c2de-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="8c2de-177">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8c2de-177">Network Settings Schema</span></span>](index.md)
