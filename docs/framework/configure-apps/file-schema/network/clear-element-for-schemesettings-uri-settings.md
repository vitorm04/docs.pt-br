---
title: '&lt;Limpar&gt; elemento para schemeSettings (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f0daa689ba09fa39ffe0f38d769112f0f095592a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028034"
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="03d7f-102">&lt;Limpar&gt; elemento para schemeSettings (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="03d7f-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="03d7f-103">Limpa todas as configurações existentes do esquema.</span><span class="sxs-lookup"><span data-stu-id="03d7f-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="03d7f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="03d7f-104">\<configuration></span></span>  
<span data-ttu-id="03d7f-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="03d7f-105">\<uri></span></span>  
<span data-ttu-id="03d7f-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="03d7f-106">\<schemeSettings></span></span>  
<span data-ttu-id="03d7f-107">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="03d7f-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d7f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03d7f-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03d7f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="03d7f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03d7f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="03d7f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03d7f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="03d7f-111">Attributes</span></span>  
 <span data-ttu-id="03d7f-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="03d7f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03d7f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="03d7f-113">Child Elements</span></span>  
 <span data-ttu-id="03d7f-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="03d7f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03d7f-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="03d7f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="03d7f-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="03d7f-116">Element</span></span>|<span data-ttu-id="03d7f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="03d7f-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03d7f-118">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="03d7f-118">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="03d7f-119">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="03d7f-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03d7f-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="03d7f-120">Remarks</span></span>  
 <span data-ttu-id="03d7f-121">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento un-escapes de classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="03d7f-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="03d7f-122">Isso era implementado como um mecanismo de segurança contra ataques, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="03d7f-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="03d7f-123">Se esse URI é passado para baixo para módulos de manipulação não % caracteres codificados corretamente, isso poderá resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="03d7f-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="03d7f-124">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> delimitadores de caminho primeiro cancelar escapes de classe e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="03d7f-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="03d7f-125">O resultado de passar a URL mal-intencionado acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="03d7f-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="03d7f-126">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="03d7f-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03d7f-127">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="03d7f-127">Configuration Files</span></span>  
 <span data-ttu-id="03d7f-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="03d7f-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03d7f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03d7f-129">Example</span></span>  
 <span data-ttu-id="03d7f-130">O exemplo a seguir mostra uma configuração usada pelo <xref:System.Uri> classe que limpa todas as configurações de esquema e, em seguida, adiciona suporte para não escapar delimitadores de caminho codificado por percentual para o esquema de http.</span><span class="sxs-lookup"><span data-stu-id="03d7f-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03d7f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03d7f-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="03d7f-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="03d7f-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
