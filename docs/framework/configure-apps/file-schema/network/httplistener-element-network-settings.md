---
title: Elemento <httpListener> (configurações de rede)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: ff5e4ad2788ab3df621beb52b1703647df068a7f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257987"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="9f39c-102">\<httpListener > (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="9f39c-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="9f39c-103">Personaliza os parâmetros usados pelo <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="9f39c-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="9f39c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9f39c-104">\<configuration></span></span>  
<span data-ttu-id="9f39c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9f39c-105">\<system.net></span></span>  
<span data-ttu-id="9f39c-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="9f39c-106">\<settings></span></span>  
<span data-ttu-id="9f39c-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="9f39c-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f39c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f39c-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="9f39c-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="9f39c-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f39c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f39c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f39c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f39c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f39c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f39c-112">Attributes</span></span>  
  
|<span data-ttu-id="9f39c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f39c-113">Attribute</span></span>|<span data-ttu-id="9f39c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f39c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f39c-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="9f39c-115">unescapeRequestUrl</span></span>|<span data-ttu-id="9f39c-116">Um valor booliano que indica se um <xref:System.Net.HttpListener> instância usa o URI sem escape bruto em vez do URI convertido.</span><span class="sxs-lookup"><span data-stu-id="9f39c-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f39c-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f39c-117">Child Elements</span></span>  
 <span data-ttu-id="9f39c-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f39c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f39c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f39c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9f39c-120">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="9f39c-120">**Element**</span></span>|<span data-ttu-id="9f39c-121">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9f39c-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9f39c-122">settings</span><span class="sxs-lookup"><span data-stu-id="9f39c-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="9f39c-123">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="9f39c-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f39c-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f39c-124">Remarks</span></span>  
 <span data-ttu-id="9f39c-125">O **unescapeRequestUrl** atributo indica se <xref:System.Net.HttpListener> usa o URI sem escape bruto em vez do URI convertido em que todos os valores codificados por porcentagem são convertidos e outras etapas de normalização são obtidas.</span><span class="sxs-lookup"><span data-stu-id="9f39c-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="9f39c-126">Quando um <xref:System.Net.HttpListener> instância recebe uma solicitação por meio de `http.sys` serviço, ele cria uma instância da cadeia de caracteres URI fornecida pelo `http.sys`e o expõe como o <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f39c-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9f39c-127">O `http.sys` serviço expõe duas cadeias de caracteres URI de solicitação:</span><span class="sxs-lookup"><span data-stu-id="9f39c-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="9f39c-128">URI bruto</span><span class="sxs-lookup"><span data-stu-id="9f39c-128">Raw URI</span></span>  
  
-   <span data-ttu-id="9f39c-129">URI convertido</span><span class="sxs-lookup"><span data-stu-id="9f39c-129">Converted URI</span></span>  
  
 <span data-ttu-id="9f39c-130">O URI bruto é o <xref:System.Uri?displayProperty=nameWithType> fornecido na linha de solicitação de uma solicitação HTTP:</span><span class="sxs-lookup"><span data-stu-id="9f39c-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="9f39c-131">O URI bruto fornecido pelo `http.sys` para a solicitação mencionada acima, é "/ caminho /".</span><span class="sxs-lookup"><span data-stu-id="9f39c-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="9f39c-132">Isso representa a cadeia de caracteres após o verbo HTTP, como ele foi enviado pela rede.</span><span class="sxs-lookup"><span data-stu-id="9f39c-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="9f39c-133">O `http.sys` serviço cria um URI convertido das informações fornecidas na solicitação usando o URI fornecido na linha da solicitação HTTP e o cabeçalho de Host para determinar o servidor de origem da solicitação deve ser encaminhado.</span><span class="sxs-lookup"><span data-stu-id="9f39c-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="9f39c-134">Isso é feito comparando as informações da solicitação com um conjunto de prefixos URI registrados.</span><span class="sxs-lookup"><span data-stu-id="9f39c-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="9f39c-135">A documentação do SDK do servidor HTTP se refere a esse URI convertido como a estrutura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="9f39c-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="9f39c-136">Para poder comparar a solicitação com prefixos URI registrados, alguns normalização para a solicitação precisa ser feito.</span><span class="sxs-lookup"><span data-stu-id="9f39c-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="9f39c-137">Para o exemplo acima do URI convertido seria da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f39c-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="9f39c-138">O `http.sys` serviço combina o <xref:System.Uri.Host%2A?displayProperty=nameWithType> valor da propriedade e a cadeia de caracteres na linha da solicitação para criar um URI convertido.</span><span class="sxs-lookup"><span data-stu-id="9f39c-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="9f39c-139">Além disso, `http.sys` e o <xref:System.Uri?displayProperty=nameWithType> classe também faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9f39c-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="9f39c-140">Un-escapa o percentual de todos os valores codificados.</span><span class="sxs-lookup"><span data-stu-id="9f39c-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="9f39c-141">Caracteres não ASCII de converte codificados por porcentagem em uma representação de caractere UTF-16.</span><span class="sxs-lookup"><span data-stu-id="9f39c-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="9f39c-142">Observe que há suporte para caracteres UTF-8 e ANSI DBCS, bem como caracteres Unicode (codificação Unicode usando o formato de uXXXX %).</span><span class="sxs-lookup"><span data-stu-id="9f39c-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="9f39c-143">Executa outras etapas de normalização, como a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="9f39c-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="9f39c-144">Uma vez que a solicitação não contém todas as informações sobre a codificação usada para valores codificados por percentual, não é possível determinar a codificação correta apenas analisando os valores codificados por porcentagem.</span><span class="sxs-lookup"><span data-stu-id="9f39c-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="9f39c-145">Portanto `http.sys` fornece duas chaves de registro para modificar o processo:</span><span class="sxs-lookup"><span data-stu-id="9f39c-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="9f39c-146">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="9f39c-146">Registry Key</span></span>|<span data-ttu-id="9f39c-147">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="9f39c-147">Default Value</span></span>|<span data-ttu-id="9f39c-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f39c-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="9f39c-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="9f39c-149">EnableNonUTF8</span></span>|<span data-ttu-id="9f39c-150">1</span><span class="sxs-lookup"><span data-stu-id="9f39c-150">1</span></span>|<span data-ttu-id="9f39c-151">Se for zero, `http.sys` aceita apenas as URLs codificado em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9f39c-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="9f39c-152">Se diferente de zero, `http.sys` também aceita codificado em ANSI ou DBCS codificado URLs nas solicitações.</span><span class="sxs-lookup"><span data-stu-id="9f39c-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="9f39c-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="9f39c-153">FavorUTF8</span></span>|<span data-ttu-id="9f39c-154">1</span><span class="sxs-lookup"><span data-stu-id="9f39c-154">1</span></span>|<span data-ttu-id="9f39c-155">Se diferente de zero, `http.sys` sempre tentará decodificar uma URL como UTF-8 primeiro; se essa conversão falhar e EnableNonUTF8 for diferente de zero, o HTTP. sys e tenta decodificá-lo como ANSI ou DBCS.</span><span class="sxs-lookup"><span data-stu-id="9f39c-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="9f39c-156">Se for zero (e EnableNonUTF8 for diferente de zero), `http.sys` tenta decodificá-lo como ANSI ou DBCS; se isso não for bem-sucedida, ele tenta uma conversão de UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9f39c-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="9f39c-157">Quando <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f39c-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="9f39c-158">É necessário para dar suporte a caracteres além de caracteres e números em URIs.</span><span class="sxs-lookup"><span data-stu-id="9f39c-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="9f39c-159">Um exemplo é o seguinte URI é usado para recuperar informações do cliente para cliente número "1/3812":</span><span class="sxs-lookup"><span data-stu-id="9f39c-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="9f39c-160">Observe a barra codificados por porcentagem no Uri (% 2F).</span><span class="sxs-lookup"><span data-stu-id="9f39c-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="9f39c-161">Isso é necessário, já que nesse caso, o caractere de barra "/" representa os dados e não um delimitador de caminho.</span><span class="sxs-lookup"><span data-stu-id="9f39c-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="9f39c-162">Passando a cadeia de caracteres para o construtor de Uri levará para o seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="9f39c-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="9f39c-163">Dividindo o caminho em seus segmentos resultaria nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="9f39c-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="9f39c-164">Isso não é a intenção do remetente da solicitação.</span><span class="sxs-lookup"><span data-stu-id="9f39c-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="9f39c-165">Se o **unescapeRequestUrl** atributo é definido como **falso**, em seguida, quando o <xref:System.Net.HttpListener> recebe uma solicitação, ele usa o URI bruto em vez do URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f39c-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="9f39c-166">O valor padrão para o **unescapeRequestUrl** atributo é **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="9f39c-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="9f39c-167">O <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriedade pode ser usada para obter o valor atual do **unescapeRequestUrl** atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f39c-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f39c-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f39c-168">Example</span></span>  
 <span data-ttu-id="9f39c-169">O exemplo a seguir mostra como configurar o <xref:System.Net.HttpListener> classe quando ele recebe uma solicitação para usar o URI bruto em vez do URI convertido de `http.sys` como entrada para o <xref:System.Net.HttpListenerRequest.Url%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f39c-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="9f39c-170">Informações do elemento</span><span class="sxs-lookup"><span data-stu-id="9f39c-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="9f39c-171">Namespace</span><span class="sxs-lookup"><span data-stu-id="9f39c-171">Namespace</span></span>|<span data-ttu-id="9f39c-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="9f39c-172">System.Net</span></span>|  
|<span data-ttu-id="9f39c-173">Nome do esquema</span><span class="sxs-lookup"><span data-stu-id="9f39c-173">Schema Name</span></span>||  
|<span data-ttu-id="9f39c-174">Arquivo de validação</span><span class="sxs-lookup"><span data-stu-id="9f39c-174">Validation File</span></span>||  
|<span data-ttu-id="9f39c-175">Pode ser vazio</span><span class="sxs-lookup"><span data-stu-id="9f39c-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="9f39c-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f39c-176">See also</span></span>
- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="9f39c-177">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9f39c-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
