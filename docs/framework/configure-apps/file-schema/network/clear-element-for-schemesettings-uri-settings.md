---
title: "&lt;Limpar&gt; elemento para schemeSettings (configurações de Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2a4841635b5d6bcaa49d024dd92241573473036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="9f6f9-102">&lt;Limpar&gt; elemento para schemeSettings (configurações de Uri)</span><span class="sxs-lookup"><span data-stu-id="9f6f9-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="9f6f9-103">Limpa todas as configurações existentes do esquema.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="9f6f9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9f6f9-104">\<configuration></span></span>  
<span data-ttu-id="9f6f9-105">\<URI ></span><span class="sxs-lookup"><span data-stu-id="9f6f9-105">\<uri></span></span>  
<span data-ttu-id="9f6f9-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="9f6f9-106">\<schemeSettings></span></span>  
<span data-ttu-id="9f6f9-107">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="9f6f9-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6f9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f6f9-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f6f9-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f6f9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9f6f9-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f6f9-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f6f9-111">Attributes</span></span>  
 <span data-ttu-id="9f6f9-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f6f9-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f6f9-113">Child Elements</span></span>  
 <span data-ttu-id="9f6f9-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f6f9-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f6f9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9f6f9-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f6f9-116">Element</span></span>|<span data-ttu-id="9f6f9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f6f9-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f6f9-118">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]</span><span class="sxs-lookup"><span data-stu-id="9f6f9-118">[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)</span></span>|<span data-ttu-id="9f6f9-119">Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f6f9-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f6f9-120">Remarks</span></span>  
 <span data-ttu-id="9f6f9-121">Por padrão, o <xref:System.Uri?displayProperty=nameWithType> por cento de escapa Cancelar classe codificado delimitadores de caminho antes de executar a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="9f6f9-122">Isso foi implementado como um mecanismo de segurança contra ataques semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="9f6f9-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9f6f9-123">Se esse URI é passado para módulos não tratamento % caracteres codificados corretamente, isso poderia resultar no comando a seguir, que está sendo executado pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="9f6f9-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="9f6f9-124">Por esse motivo, <xref:System.Uri?displayProperty=nameWithType> classe delimitadores de caminho escapes cancelar primeiro e, em seguida, aplica-se a compactação de caminho.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="9f6f9-125">O resultado de passar a URL mal-intencionada acima para <xref:System.Uri?displayProperty=nameWithType> classe resultados construtor no seguinte URI:</span><span class="sxs-lookup"><span data-stu-id="9f6f9-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9f6f9-126">Esse comportamento padrão pode ser modificado para não cancelar escape porcentagem codificado delimitadores de caminho usando a opção de configuração schemeSettings para um esquema específico.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9f6f9-127">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="9f6f9-127">Configuration Files</span></span>  
 <span data-ttu-id="9f6f9-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9f6f9-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f6f9-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f6f9-129">Example</span></span>  
 <span data-ttu-id="9f6f9-130">O exemplo a seguir mostra uma configuração usada pela <xref:System.Uri> classe limpa todas as configurações de esquema e, em seguida, adiciona suporte para a saída não delimitadores de caminho codificados por percentual para o esquema http.</span><span class="sxs-lookup"><span data-stu-id="9f6f9-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f6f9-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f6f9-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="9f6f9-132">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9f6f9-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
