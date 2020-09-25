---
title: Elemento <httpListener> (Configurações de Rede)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 78526559164939667eab8848bc5fd2af6749d474
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195435"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="347ce-102">Elemento \<httpListener> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="347ce-102">\<httpListener> Element (Network Settings)</span></span>

<span data-ttu-id="347ce-103">Personaliza os parâmetros usados pela <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="347ce-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="347ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="347ce-104">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="347ce-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="347ce-105">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="347ce-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="347ce-106">Attributes and Elements</span></span>  

 <span data-ttu-id="347ce-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="347ce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="347ce-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="347ce-108">Attributes</span></span>  
  
|<span data-ttu-id="347ce-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="347ce-109">Attribute</span></span>|<span data-ttu-id="347ce-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="347ce-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="347ce-111">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="347ce-111">unescapeRequestUrl</span></span>|<span data-ttu-id="347ce-112">Um valor booliano que indica se uma <xref:System.Net.HttpListener> instância usa o URI sem escape bruto em vez do URI convertido.</span><span class="sxs-lookup"><span data-stu-id="347ce-112">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="347ce-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="347ce-113">Child Elements</span></span>  

 <span data-ttu-id="347ce-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="347ce-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="347ce-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="347ce-115">Parent Elements</span></span>  
  
|<span data-ttu-id="347ce-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="347ce-116">**Element**</span></span>|<span data-ttu-id="347ce-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="347ce-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="347ce-118">configurações</span><span class="sxs-lookup"><span data-stu-id="347ce-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="347ce-119">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="347ce-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="347ce-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="347ce-120">Remarks</span></span>  

 <span data-ttu-id="347ce-121">O atributo **unescapeRequestUrl** indica se <xref:System.Net.HttpListener> o usa o URI sem escape bruto em vez do URI convertido em que os valores codificados por porcentagem são convertidos e outras etapas de normalização são feitas.</span><span class="sxs-lookup"><span data-stu-id="347ce-121">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="347ce-122">Quando uma <xref:System.Net.HttpListener> instância recebe uma solicitação por meio do `http.sys` serviço, ela cria uma instância da cadeia de caracteres de URI fornecida pelo `http.sys` e a expõe como a <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="347ce-122">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="347ce-123">O `http.sys` serviço expõe duas cadeias de caracteres de URI de solicitação:</span><span class="sxs-lookup"><span data-stu-id="347ce-123">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="347ce-124">URI bruto</span><span class="sxs-lookup"><span data-stu-id="347ce-124">Raw URI</span></span>  
  
- <span data-ttu-id="347ce-125">URI convertido</span><span class="sxs-lookup"><span data-stu-id="347ce-125">Converted URI</span></span>  
  
 <span data-ttu-id="347ce-126">O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação http:</span><span class="sxs-lookup"><span data-stu-id="347ce-126">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="347ce-127">O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima é "/Path/".</span><span class="sxs-lookup"><span data-stu-id="347ce-127">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="347ce-128">Isso representa a cadeia de caracteres após o verbo HTTP, pois ele foi enviado pela rede.</span><span class="sxs-lookup"><span data-stu-id="347ce-128">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="347ce-129">O `http.sys` serviço cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha de solicitação HTTP e o cabeçalho do host para determinar o servidor de origem para o qual a solicitação deve ser encaminhada.</span><span class="sxs-lookup"><span data-stu-id="347ce-129">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="347ce-130">Isso é feito comparando as informações da solicitação com um conjunto de prefixos de URI registrados.</span><span class="sxs-lookup"><span data-stu-id="347ce-130">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="347ce-131">A documentação do SDK do servidor HTTP refere-se a esse URI convertido como a estrutura de HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="347ce-131">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="347ce-132">Para poder comparar a solicitação com prefixos de URI registrados, é necessário fazer alguma normalização na solicitação.</span><span class="sxs-lookup"><span data-stu-id="347ce-132">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="347ce-133">Para o exemplo acima, o URI convertido seria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="347ce-133">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="347ce-134">O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> valor da propriedade e a cadeia de caracteres na linha de solicitação para criar um URI convertido.</span><span class="sxs-lookup"><span data-stu-id="347ce-134">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="347ce-135">Além disso, `http.sys` e a <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="347ce-135">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="347ce-136">Cancela o escape de todos os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="347ce-136">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="347ce-137">Converte caracteres não ASCII codificados por porcentagem em uma representação de caractere UTF-16.</span><span class="sxs-lookup"><span data-stu-id="347ce-137">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="347ce-138">Observe que os caracteres UTF-8 e ANSI/DBCS têm suporte, bem como caracteres Unicode (codificação Unicode usando o formato% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="347ce-138">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="347ce-139">Executa outras etapas de normalização, como compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="347ce-139">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="347ce-140">Como a solicitação não contém informações sobre a codificação usada para valores codificados por porcentagem, talvez não seja possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="347ce-140">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="347ce-141">Portanto, o `http.sys` fornece duas chaves do registro para modificar o processo:</span><span class="sxs-lookup"><span data-stu-id="347ce-141">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="347ce-142">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="347ce-142">Registry Key</span></span>|<span data-ttu-id="347ce-143">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="347ce-143">Default Value</span></span>|<span data-ttu-id="347ce-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="347ce-144">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="347ce-145">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="347ce-145">EnableNonUTF8</span></span>|<span data-ttu-id="347ce-146">1</span><span class="sxs-lookup"><span data-stu-id="347ce-146">1</span></span>|<span data-ttu-id="347ce-147">Se zero, `http.sys` aceitará somente URLs codificadas em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="347ce-147">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="347ce-148">Se for diferente de zero, o `http.sys` também aceitará URLs codificadas por ANSI ou DBCS em solicitações.</span><span class="sxs-lookup"><span data-stu-id="347ce-148">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="347ce-149">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="347ce-149">FavorUTF8</span></span>|<span data-ttu-id="347ce-150">1</span><span class="sxs-lookup"><span data-stu-id="347ce-150">1</span></span>|<span data-ttu-id="347ce-151">Se for diferente de zero, `http.sys` o sempre tentará decodificar uma URL como UTF-8 primeiro; se essa conversão falhar e EnableNonUTF8 for diferente de zero, Http.sys tentará decodificá-la como ANSI ou DBCS.</span><span class="sxs-lookup"><span data-stu-id="347ce-151">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="347ce-152">Se zero (e EnableNonUTF8 for diferente de zero), `http.sys` o tentará decodificá-lo como ANSI ou DBCS; se isso não for bem-sucedido, ele tentará uma conversão UTF-8.</span><span class="sxs-lookup"><span data-stu-id="347ce-152">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="347ce-153">Quando o <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="347ce-153">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="347ce-154">Há uma necessidade de dar suporte a caracteres além de caracteres e números em URIs.</span><span class="sxs-lookup"><span data-stu-id="347ce-154">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="347ce-155">Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o número de cliente "1/3812":</span><span class="sxs-lookup"><span data-stu-id="347ce-155">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="347ce-156">Observe a barra codificada por porcentagem no URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="347ce-156">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="347ce-157">Isso é necessário, pois, nesse caso, o caractere de barra representa dados e não um delimitador de caminho.</span><span class="sxs-lookup"><span data-stu-id="347ce-157">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="347ce-158">Passar a cadeia de caracteres para o construtor de URI resultará no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="347ce-158">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="347ce-159">Dividir o caminho em seus segmentos resultaria nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="347ce-159">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="347ce-160">Essa não é a intenção do remetente da solicitação.</span><span class="sxs-lookup"><span data-stu-id="347ce-160">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="347ce-161">Se o atributo **unescapeRequestUrl** for definido como **false**, quando o <xref:System.Net.HttpListener> receber uma solicitação, ele usará o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="347ce-161">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="347ce-162">O valor padrão para o atributo **unescapeRequestUrl** é **true**.</span><span class="sxs-lookup"><span data-stu-id="347ce-162">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="347ce-163">A <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do atributo **unescapeRequestUrl** dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="347ce-163">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="347ce-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="347ce-164">Example</span></span>  

 <span data-ttu-id="347ce-165">O exemplo a seguir mostra como configurar a <xref:System.Net.HttpListener> classe quando ela recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="347ce-165">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="347ce-166">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="347ce-166">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="347ce-167">Namespace</span><span class="sxs-lookup"><span data-stu-id="347ce-167">Namespace</span></span>|<span data-ttu-id="347ce-168">System.Net</span><span class="sxs-lookup"><span data-stu-id="347ce-168">System.Net</span></span>|  
|<span data-ttu-id="347ce-169">Nome do Esquema</span><span class="sxs-lookup"><span data-stu-id="347ce-169">Schema Name</span></span>||  
|<span data-ttu-id="347ce-170">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="347ce-170">Validation File</span></span>||  
|<span data-ttu-id="347ce-171">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="347ce-171">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="347ce-172">Veja também</span><span class="sxs-lookup"><span data-stu-id="347ce-172">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="347ce-173">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="347ce-173">Network Settings Schema</span></span>](index.md)
