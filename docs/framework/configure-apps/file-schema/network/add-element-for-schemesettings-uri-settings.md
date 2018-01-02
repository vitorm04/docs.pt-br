---
title: "&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d617e78231bd0b9f4e332c4b7fbe58b78598868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="c6334-102">&lt;Adicionar&gt; elemento para schemeSettings (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="c6334-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="c6334-103">Adiciona uma configuração de esquema para um nome de esquema.</span><span class="sxs-lookup"><span data-stu-id="c6334-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="c6334-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c6334-104">\<configuration></span></span>  
<span data-ttu-id="c6334-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="c6334-105">\<uri></span></span>  
<span data-ttu-id="c6334-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="c6334-106">\<schemeSettings></span></span>  
<span data-ttu-id="c6334-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c6334-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6334-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6334-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6334-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6334-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c6334-110">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6334-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6334-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6334-111">Attributes</span></span>  
  
|<span data-ttu-id="c6334-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6334-112">Attribute</span></span>|<span data-ttu-id="c6334-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6334-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6334-114">name</span><span class="sxs-lookup"><span data-stu-id="c6334-114">name</span></span>|<span data-ttu-id="c6334-115">O nome do esquema para o qual essa configuração se aplica.</span><span class="sxs-lookup"><span data-stu-id="c6334-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="c6334-116">A apenas os valores com suporte são nome = "http" e o nome = "https".</span><span class="sxs-lookup"><span data-stu-id="c6334-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="c6334-117">{Nome do atributo} Atributo</span><span class="sxs-lookup"><span data-stu-id="c6334-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="c6334-118">Valor</span><span class="sxs-lookup"><span data-stu-id="c6334-118">Value</span></span>|<span data-ttu-id="c6334-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6334-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6334-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="c6334-120">genericUriParserOptions</span></span>|<span data-ttu-id="c6334-121">As opções de analisador para este esquema.</span><span class="sxs-lookup"><span data-stu-id="c6334-121">The parser options for this scheme.</span></span> <span data-ttu-id="c6334-122">O somente valor com suporte é genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="c6334-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6334-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6334-123">Child Elements</span></span>  
 <span data-ttu-id="c6334-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c6334-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6334-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6334-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c6334-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6334-126">Element</span></span>|<span data-ttu-id="c6334-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6334-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6334-128">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="c6334-128">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="c6334-129">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="c6334-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6334-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6334-130">Remarks</span></span>  
 <span data-ttu-id="c6334-131">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento de escapa Cancelar classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="c6334-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="c6334-132">Isso foi implementado como um mecanismo de segurança contra ataques semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6334-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c6334-133">Se esse URI é passado para módulos não tratamento % caracteres codificados corretamente, isso poderia resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="c6334-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="c6334-134">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe delimitadores de caminho escapes cancelar primeiro e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="c6334-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="c6334-135">O resultado de passar a URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="c6334-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c6334-136">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="c6334-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c6334-137">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="c6334-137">Configuration Files</span></span>  
 <span data-ttu-id="c6334-138">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c6334-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6334-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6334-139">Example</span></span>  
 <span data-ttu-id="c6334-140">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe para dar suporte a saída não delimitadores de caminho codificados por percentual para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="c6334-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6334-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6334-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="c6334-142">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c6334-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
