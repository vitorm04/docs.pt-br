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
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="44aeb-102">\<Elemento > httpListener (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="44aeb-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="44aeb-103">Personaliza os <xref:System.Net.HttpListener> parâmetros usados pela classe.</span><span class="sxs-lookup"><span data-stu-id="44aeb-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="44aeb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="44aeb-104">\<configuration></span></span>  
<span data-ttu-id="44aeb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="44aeb-105">\<system.net></span></span>  
<span data-ttu-id="44aeb-106">\<> de configurações</span><span class="sxs-lookup"><span data-stu-id="44aeb-106">\<settings></span></span>  
<span data-ttu-id="44aeb-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="44aeb-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44aeb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44aeb-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="44aeb-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="44aeb-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44aeb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44aeb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44aeb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44aeb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44aeb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="44aeb-112">Attributes</span></span>  
  
|<span data-ttu-id="44aeb-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="44aeb-113">Attribute</span></span>|<span data-ttu-id="44aeb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="44aeb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44aeb-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="44aeb-115">unescapeRequestUrl</span></span>|<span data-ttu-id="44aeb-116">Um valor booliano que indica se <xref:System.Net.HttpListener> uma instância usa o URI sem escape bruto em vez do URI convertido.</span><span class="sxs-lookup"><span data-stu-id="44aeb-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44aeb-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44aeb-117">Child Elements</span></span>  
 <span data-ttu-id="44aeb-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44aeb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44aeb-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44aeb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="44aeb-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="44aeb-120">**Element**</span></span>|<span data-ttu-id="44aeb-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="44aeb-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44aeb-122">settings</span><span class="sxs-lookup"><span data-stu-id="44aeb-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="44aeb-123">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="44aeb-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44aeb-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="44aeb-124">Remarks</span></span>  
 <span data-ttu-id="44aeb-125">O atributo **unescapeRequestUrl** indica se <xref:System.Net.HttpListener> o usa o URI sem escape bruto em vez do URI convertido em que os valores codificados por porcentagem são convertidos e outras etapas de normalização são feitas.</span><span class="sxs-lookup"><span data-stu-id="44aeb-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="44aeb-126">Quando uma <xref:System.Net.HttpListener> instância recebe uma solicitação por meio `http.sys` do serviço, ela cria uma instância da cadeia de caracteres de `http.sys`URI fornecida pelo e a expõe <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> como a propriedade.</span><span class="sxs-lookup"><span data-stu-id="44aeb-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="44aeb-127">O `http.sys` serviço expõe duas cadeias de caracteres de URI de solicitação:</span><span class="sxs-lookup"><span data-stu-id="44aeb-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="44aeb-128">URI bruto</span><span class="sxs-lookup"><span data-stu-id="44aeb-128">Raw URI</span></span>  
  
- <span data-ttu-id="44aeb-129">URI convertido</span><span class="sxs-lookup"><span data-stu-id="44aeb-129">Converted URI</span></span>  
  
 <span data-ttu-id="44aeb-130">O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação http:</span><span class="sxs-lookup"><span data-stu-id="44aeb-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="44aeb-131">O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima é "/Path/".</span><span class="sxs-lookup"><span data-stu-id="44aeb-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="44aeb-132">Isso representa a cadeia de caracteres após o verbo HTTP, pois ele foi enviado pela rede.</span><span class="sxs-lookup"><span data-stu-id="44aeb-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="44aeb-133">O `http.sys` serviço cria um URI convertido a partir das informações fornecidas na solicitação usando o URI fornecido na linha de solicitação HTTP e o cabeçalho do host para determinar o servidor de origem para o qual a solicitação deve ser encaminhada.</span><span class="sxs-lookup"><span data-stu-id="44aeb-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="44aeb-134">Isso é feito comparando as informações da solicitação com um conjunto de prefixos de URI registrados.</span><span class="sxs-lookup"><span data-stu-id="44aeb-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="44aeb-135">A documentação do SDK do servidor HTTP refere-se a esse URI convertido como a estrutura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="44aeb-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="44aeb-136">Para poder comparar a solicitação com prefixos de URI registrados, é necessário fazer alguma normalização na solicitação.</span><span class="sxs-lookup"><span data-stu-id="44aeb-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="44aeb-137">Para o exemplo acima, o URI convertido seria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="44aeb-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="44aeb-138">O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> valor da propriedade e a cadeia de caracteres na linha de solicitação para criar um URI convertido.</span><span class="sxs-lookup"><span data-stu-id="44aeb-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="44aeb-139">Além disso, `http.sys` e a <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="44aeb-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="44aeb-140">Cancela o escape de todos os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="44aeb-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="44aeb-141">Converte caracteres não ASCII codificados por porcentagem em uma representação de caractere UTF-16.</span><span class="sxs-lookup"><span data-stu-id="44aeb-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="44aeb-142">Observe que os caracteres UTF-8 e ANSI/DBCS têm suporte, bem como caracteres Unicode (codificação Unicode usando o formato% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="44aeb-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="44aeb-143">Executa outras etapas de normalização, como compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="44aeb-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="44aeb-144">Como a solicitação não contém informações sobre a codificação usada para valores codificados por porcentagem, talvez não seja possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="44aeb-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="44aeb-145">Portanto `http.sys` , o fornece duas chaves do registro para modificar o processo:</span><span class="sxs-lookup"><span data-stu-id="44aeb-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="44aeb-146">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="44aeb-146">Registry Key</span></span>|<span data-ttu-id="44aeb-147">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="44aeb-147">Default Value</span></span>|<span data-ttu-id="44aeb-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="44aeb-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="44aeb-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="44aeb-149">EnableNonUTF8</span></span>|<span data-ttu-id="44aeb-150">1</span><span class="sxs-lookup"><span data-stu-id="44aeb-150">1</span></span>|<span data-ttu-id="44aeb-151">Se zero, `http.sys` aceitará somente URLs codificadas em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44aeb-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="44aeb-152">Se for diferente de zero `http.sys` , o também aceitará URLs codificadas por ANSI ou DBCS em solicitações.</span><span class="sxs-lookup"><span data-stu-id="44aeb-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="44aeb-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="44aeb-153">FavorUTF8</span></span>|<span data-ttu-id="44aeb-154">1</span><span class="sxs-lookup"><span data-stu-id="44aeb-154">1</span></span>|<span data-ttu-id="44aeb-155">Se for diferente de zero `http.sys` , sempre tentará decodificar uma URL como UTF-8 primeiro; se essa conversão falhar e EnableNonUTF8 for diferente de zero, o http. sys tentará decodificá-la como ANSI ou DBCS.</span><span class="sxs-lookup"><span data-stu-id="44aeb-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="44aeb-156">Se zero (e EnableNonUTF8 for diferente de zero), `http.sys` o tentará decodificá-lo como ANSI ou DBCS; se isso não for bem-sucedido, ele tentará uma conversão UTF-8.</span><span class="sxs-lookup"><span data-stu-id="44aeb-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="44aeb-157">Quando <xref:System.Net.HttpListener> o recebe uma solicitação, ele usa o URI convertido `http.sys` de como entrada para <xref:System.Net.HttpListenerRequest.Url%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="44aeb-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="44aeb-158">Há uma necessidade de dar suporte a caracteres além de caracteres e números em URIs.</span><span class="sxs-lookup"><span data-stu-id="44aeb-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="44aeb-159">Um exemplo é o URI a seguir, que é usado para recuperar informações do cliente para o número de cliente "1/3812":</span><span class="sxs-lookup"><span data-stu-id="44aeb-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="44aeb-160">Observe a barra codificada por porcentagem no URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="44aeb-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="44aeb-161">Isso é necessário, pois, nesse caso, o caractere de barra representa dados e não um delimitador de caminho.</span><span class="sxs-lookup"><span data-stu-id="44aeb-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="44aeb-162">Passar a cadeia de caracteres para o construtor de URI resultará no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="44aeb-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="44aeb-163">Dividir o caminho em seus segmentos resultaria nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="44aeb-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="44aeb-164">Essa não é a intenção do remetente da solicitação.</span><span class="sxs-lookup"><span data-stu-id="44aeb-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="44aeb-165">Se o atributo **unescapeRequestUrl** for definido como **false**, quando o <xref:System.Net.HttpListener> receber uma solicitação, ele usará o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="44aeb-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="44aeb-166">O valor padrão para o atributo **unescapeRequestUrl** é **true**.</span><span class="sxs-lookup"><span data-stu-id="44aeb-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="44aeb-167">A <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do atributo **unescapeRequestUrl** dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="44aeb-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44aeb-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44aeb-168">Example</span></span>  
 <span data-ttu-id="44aeb-169">O exemplo a seguir mostra como configurar a <xref:System.Net.HttpListener> classe quando ela recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para a <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="44aeb-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="44aeb-170">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="44aeb-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="44aeb-171">Namespace</span><span class="sxs-lookup"><span data-stu-id="44aeb-171">Namespace</span></span>|<span data-ttu-id="44aeb-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="44aeb-172">System.Net</span></span>|  
|<span data-ttu-id="44aeb-173">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="44aeb-173">Schema Name</span></span>||  
|<span data-ttu-id="44aeb-174">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="44aeb-174">Validation File</span></span>||  
|<span data-ttu-id="44aeb-175">Pode estar vazio</span><span class="sxs-lookup"><span data-stu-id="44aeb-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="44aeb-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44aeb-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="44aeb-177">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="44aeb-177">Network Settings Schema</span></span>](index.md)
