---
title: Elemento <remove> para webRequestModules (Configurações de Rede)
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
ms.openlocfilehash: c57e2849d608b1706c41beca91ff8026ebd9ca45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705019"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="c1ffb-102">\<Remover > elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="c1ffb-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="c1ffb-103">Remove um módulo de solicitação da Web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="c1ffb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c1ffb-104">\<configuration></span></span>  
<span data-ttu-id="c1ffb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c1ffb-105">\<system.net></span></span>  
<span data-ttu-id="c1ffb-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="c1ffb-106">\<webRequestModules></span></span>  
<span data-ttu-id="c1ffb-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="c1ffb-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ffb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1ffb-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1ffb-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1ffb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c1ffb-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1ffb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1ffb-111">Attributes</span></span>  
  
|<span data-ttu-id="c1ffb-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="c1ffb-112">**Attribute**</span></span>|<span data-ttu-id="c1ffb-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c1ffb-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="c1ffb-114">O prefixo URI para solicitações manipuladas por esse módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1ffb-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1ffb-115">Child Elements</span></span>  
 <span data-ttu-id="c1ffb-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1ffb-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1ffb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c1ffb-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c1ffb-118">**Element**</span></span>|<span data-ttu-id="c1ffb-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c1ffb-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1ffb-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="c1ffb-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="c1ffb-121">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1ffb-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1ffb-122">Remarks</span></span>  
 <span data-ttu-id="c1ffb-123">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo URI especificado.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="c1ffb-124">O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "`http`", ou "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="c1ffb-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c1ffb-125">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="c1ffb-125">Configuration Files</span></span>  
 <span data-ttu-id="c1ffb-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c1ffb-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1ffb-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1ffb-127">Example</span></span>  

<span data-ttu-id="c1ffb-128">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP e, em seguida, registra um novo módulo de solicitação da Web personalizado para HTTP solicitações para `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c1ffb-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1ffb-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1ffb-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="c1ffb-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c1ffb-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
