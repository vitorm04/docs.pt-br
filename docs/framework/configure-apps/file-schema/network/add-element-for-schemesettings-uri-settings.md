---
title: '&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: d64744cf3c88d5ec0f0edf1a31cdf184c3c8277e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524098"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="229c2-102">&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="229c2-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="229c2-103">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="229c2-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="229c2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="229c2-104">\<configuration></span></span>  
<span data-ttu-id="229c2-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="229c2-105">\<uri></span></span>  
<span data-ttu-id="229c2-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="229c2-106">\<schemeSettings></span></span>  
<span data-ttu-id="229c2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="229c2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229c2-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="229c2-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="229c2-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="229c2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="229c2-110">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="229c2-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="229c2-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="229c2-111">Attributes</span></span>  
  
|<span data-ttu-id="229c2-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="229c2-112">Attribute</span></span>|<span data-ttu-id="229c2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="229c2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="229c2-114">name</span><span class="sxs-lookup"><span data-stu-id="229c2-114">name</span></span>|<span data-ttu-id="229c2-115">O nome do esquema para o qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="229c2-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="229c2-116">O somente valores com suporte são nome = "http" e o nome = "https".</span><span class="sxs-lookup"><span data-stu-id="229c2-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="229c2-117">{Nome do atributo} Atributo</span><span class="sxs-lookup"><span data-stu-id="229c2-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="229c2-118">Valor</span><span class="sxs-lookup"><span data-stu-id="229c2-118">Value</span></span>|<span data-ttu-id="229c2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="229c2-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="229c2-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="229c2-120">genericUriParserOptions</span></span>|<span data-ttu-id="229c2-121">As opções de analisador para este esquema.</span><span class="sxs-lookup"><span data-stu-id="229c2-121">The parser options for this scheme.</span></span> <span data-ttu-id="229c2-122">O somente valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="229c2-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="229c2-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="229c2-123">Child Elements</span></span>  
 <span data-ttu-id="229c2-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="229c2-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="229c2-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="229c2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="229c2-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="229c2-126">Element</span></span>|<span data-ttu-id="229c2-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="229c2-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="229c2-128">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="229c2-128">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="229c2-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="229c2-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="229c2-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="229c2-130">Remarks</span></span>  
 <span data-ttu-id="229c2-131">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento un-escapes de classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="229c2-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="229c2-132">Isso era implementado como um mecanismo de segurança contra ataques, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="229c2-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="229c2-133">Se esse URI é passado para baixo para módulos de manipulação não % caracteres codificados corretamente, isso poderá resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="229c2-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="229c2-134">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> delimitadores de caminho primeiro cancelar escapes de classe e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="229c2-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="229c2-135">O resultado de passar a URL mal-intencionado acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="229c2-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="229c2-136">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="229c2-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="229c2-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="229c2-137">Configuration Files</span></span>  
 <span data-ttu-id="229c2-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="229c2-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="229c2-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="229c2-139">Example</span></span>  
 <span data-ttu-id="229c2-140">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe para dar suporte a escape não delimitadores de caminho codificado por percentual para o esquema de http.</span><span class="sxs-lookup"><span data-stu-id="229c2-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="229c2-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="229c2-141">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="229c2-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="229c2-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
