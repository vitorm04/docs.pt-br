---
title: Elemento <clear> para webRequestModules (configurações de rede)
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
ms.openlocfilehash: 0096c7b3426645b90e2e1609fb2427334345fd87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284148"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="ae5db-102">\<Limpar > elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="ae5db-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="ae5db-103">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae5db-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="ae5db-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ae5db-104">\<configuration></span></span>  
<span data-ttu-id="ae5db-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ae5db-105">\<system.net></span></span>  
<span data-ttu-id="ae5db-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="ae5db-106">\<webRequestModules></span></span>  
<span data-ttu-id="ae5db-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="ae5db-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5db-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae5db-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae5db-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ae5db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae5db-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ae5db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae5db-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ae5db-111">Attributes</span></span>  
 <span data-ttu-id="ae5db-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae5db-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ae5db-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ae5db-113">Child Elements</span></span>  
 <span data-ttu-id="ae5db-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ae5db-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae5db-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ae5db-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ae5db-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="ae5db-116">**Element**</span></span>|<span data-ttu-id="ae5db-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="ae5db-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ae5db-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="ae5db-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="ae5db-119">Especifica os módulos para usá-lo para solicitar informações de hosts da rede.</span><span class="sxs-lookup"><span data-stu-id="ae5db-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae5db-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae5db-120">Remarks</span></span>  
 <span data-ttu-id="ae5db-121">O `clear` elemento remove todos os módulos de solicitação da Web que foram definidos anteriormente no arquivo de configuração ou em um nível mais alto na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="ae5db-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ae5db-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="ae5db-122">Configuration Files</span></span>  
 <span data-ttu-id="ae5db-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ae5db-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae5db-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae5db-124">Example</span></span>  
 <span data-ttu-id="ae5db-125">O exemplo a seguir limpa todos os módulos de solicitação da Web e, em seguida, registra um módulo de solicitação da Web para HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae5db-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae5db-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae5db-126">See also</span></span>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="ae5db-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="ae5db-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
