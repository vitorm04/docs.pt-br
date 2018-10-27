---
title: '&lt;remover&gt; elemento para webRequestModules (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: 2f787206c503c047a34383e12c5676296e39c1fe
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190743"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="b5142-102">&lt;remover&gt; elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="b5142-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="b5142-103">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5142-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="b5142-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b5142-104">\<configuration></span></span>  
<span data-ttu-id="b5142-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b5142-105">\<system.net></span></span>  
<span data-ttu-id="b5142-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="b5142-106">\<webRequestModules></span></span>  
<span data-ttu-id="b5142-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="b5142-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5142-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5142-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5142-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b5142-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b5142-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b5142-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5142-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5142-111">Attributes</span></span>  
  
|<span data-ttu-id="b5142-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="b5142-112">**Attribute**</span></span>|<span data-ttu-id="b5142-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b5142-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="b5142-114">O prefixo URI para solicitações manipuladas por esse módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="b5142-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5142-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b5142-115">Child Elements</span></span>  
 <span data-ttu-id="b5142-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b5142-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5142-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b5142-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b5142-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="b5142-118">**Element**</span></span>|<span data-ttu-id="b5142-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="b5142-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b5142-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="b5142-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="b5142-121">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="b5142-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5142-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5142-122">Remarks</span></span>  
 <span data-ttu-id="b5142-123">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo URI especificado.</span><span class="sxs-lookup"><span data-stu-id="b5142-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="b5142-124">O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "`http`", ou "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="b5142-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b5142-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b5142-125">Configuration Files</span></span>  
 <span data-ttu-id="b5142-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b5142-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5142-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5142-127">Example</span></span>  

<span data-ttu-id="b5142-128">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e, em seguida, registra um novo módulo de solicitação da Web personalizado para HTTP solicitações para `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="b5142-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5142-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5142-129">See Also</span></span>  
- <xref:System.Net.WebRequest>  
- [<span data-ttu-id="b5142-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b5142-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
