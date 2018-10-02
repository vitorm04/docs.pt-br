---
title: '&lt;Limpar&gt; elemento para webRequestModules (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2b313aa2481b1257715ac4dbc6d452e2120f4726
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032082"
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="2e864-102">&lt;Limpar&gt; elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="2e864-102">&lt;clear&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="2e864-103">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e864-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="2e864-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2e864-104">\<configuration></span></span>  
<span data-ttu-id="2e864-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2e864-105">\<system.net></span></span>  
<span data-ttu-id="2e864-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="2e864-106">\<webRequestModules></span></span>  
<span data-ttu-id="2e864-107">\<Limpar ></span><span class="sxs-lookup"><span data-stu-id="2e864-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e864-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e864-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e864-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2e864-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e864-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2e864-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e864-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2e864-111">Attributes</span></span>  
 <span data-ttu-id="2e864-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2e864-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e864-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2e864-113">Child Elements</span></span>  
 <span data-ttu-id="2e864-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2e864-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e864-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2e864-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2e864-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="2e864-116">**Element**</span></span>|<span data-ttu-id="2e864-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2e864-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2e864-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="2e864-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="2e864-119">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="2e864-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e864-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e864-120">Remarks</span></span>  
 <span data-ttu-id="2e864-121">O `clear` elemento remove todos os módulos de solicitação da Web que foram definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="2e864-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2e864-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="2e864-122">Configuration Files</span></span>  
 <span data-ttu-id="2e864-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2e864-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e864-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e864-124">Example</span></span>  
 <span data-ttu-id="2e864-125">O exemplo a seguir limpa todos os módulos de solicitação da Web e, em seguida, registra um módulo de solicitação da Web para HTTP.</span><span class="sxs-lookup"><span data-stu-id="2e864-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e864-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e864-126">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="2e864-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="2e864-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
