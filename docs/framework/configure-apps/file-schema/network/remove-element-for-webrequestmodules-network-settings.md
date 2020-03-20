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
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154719"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="c7153-102">\<remover> Elemento para webRequestModules (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="c7153-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="c7153-103">Remove um módulo de solicitação web personalizado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7153-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="c7153-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7153-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7153-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c7153-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c7153-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c7153-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="c7153-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remover>**</span><span class="sxs-lookup"><span data-stu-id="c7153-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c7153-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7153-108">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7153-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c7153-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c7153-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c7153-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7153-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="c7153-111">Attributes</span></span>  
  
|<span data-ttu-id="c7153-112">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="c7153-112">**Attribute**</span></span>|<span data-ttu-id="c7153-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c7153-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="c7153-114">O prefixo URI para solicitações manipuladas por este módulo de solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c7153-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7153-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c7153-115">Child Elements</span></span>  
 <span data-ttu-id="c7153-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c7153-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7153-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c7153-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c7153-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c7153-118">**Element**</span></span>|<span data-ttu-id="c7153-119">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c7153-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c7153-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="c7153-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="c7153-121">Especifica módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="c7153-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7153-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7153-122">Remarks</span></span>  
 <span data-ttu-id="c7153-123">O `remove` elemento remove o módulo de solicitação da Web registrado para o prefixo URI especificado.</span><span class="sxs-lookup"><span data-stu-id="c7153-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="c7153-124">O valor `prefix` para o atributo deve ser os caracteres`http`principais`http://www.contoso.com`de um URI válido - por exemplo, " ", ou " "" " "</span><span class="sxs-lookup"><span data-stu-id="c7153-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c7153-125">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c7153-125">Configuration Files</span></span>  
 <span data-ttu-id="c7153-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c7153-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7153-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7153-127">Example</span></span>  

<span data-ttu-id="c7153-128">O exemplo a seguir remove o módulo de solicitação da Web existente para HTTP `www.contoso.com`e, em seguida, registra um novo módulo de solicitação web personalizado para solicitações HTTP para .</span><span class="sxs-lookup"><span data-stu-id="c7153-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7153-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="c7153-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="c7153-130">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="c7153-130">Network Settings Schema</span></span>](index.md)
