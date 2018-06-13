---
title: '&lt;remover&gt; elemento para schemeSettings (configurações de Uri)'
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8e01f82a476286e27129e4b1a47fefc1ac77c2b5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744155"
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="8dc65-102">&lt;remover&gt; elemento para schemeSettings (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="8dc65-102">&lt;remove&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="8dc65-103">Remove uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="8dc65-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="8dc65-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8dc65-104">\<configuration></span></span>  
<span data-ttu-id="8dc65-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="8dc65-105">\<uri></span></span>  
<span data-ttu-id="8dc65-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="8dc65-106">\<schemeSettings></span></span>  
<span data-ttu-id="8dc65-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="8dc65-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc65-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dc65-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dc65-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8dc65-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8dc65-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8dc65-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dc65-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="8dc65-111">Attributes</span></span>  
  
|<span data-ttu-id="8dc65-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="8dc65-112">Attribute</span></span>|<span data-ttu-id="8dc65-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dc65-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dc65-114">name</span><span class="sxs-lookup"><span data-stu-id="8dc65-114">name</span></span>|<span data-ttu-id="8dc65-115">O nome do esquema para o qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="8dc65-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="8dc65-116">A apenas os valores com suporte são nome = "http" e o nome = "https".</span><span class="sxs-lookup"><span data-stu-id="8dc65-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dc65-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8dc65-117">Child Elements</span></span>  
 <span data-ttu-id="8dc65-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8dc65-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8dc65-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8dc65-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8dc65-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dc65-120">Element</span></span>|<span data-ttu-id="8dc65-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dc65-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8dc65-122">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="8dc65-122">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="8dc65-123">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="8dc65-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dc65-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="8dc65-124">Remarks</span></span>  
 <span data-ttu-id="8dc65-125">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento de escapa Cancelar classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="8dc65-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8dc65-126">Isso foi implementado como um mecanismo de segurança contra ataques semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="8dc65-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8dc65-127">Se esse URI é passado para módulos não tratamento % caracteres codificados corretamente, isso poderia resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="8dc65-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8dc65-128">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe delimitadores de caminho escapes cancelar primeiro e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="8dc65-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8dc65-129">O resultado de passar a URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="8dc65-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8dc65-130">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="8dc65-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8dc65-131">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="8dc65-131">Configuration Files</span></span>  
 <span data-ttu-id="8dc65-132">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8dc65-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dc65-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8dc65-133">Example</span></span>  
 <span data-ttu-id="8dc65-134">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe que remove as definições de esquema para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="8dc65-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dc65-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc65-135">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="8dc65-136">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="8dc65-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
