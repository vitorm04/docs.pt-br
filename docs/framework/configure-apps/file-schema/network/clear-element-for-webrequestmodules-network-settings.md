---
title: Elemento <clear> para webRequestModules (Configurações de Rede)
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
ms.openlocfilehash: 5832d120824df75d374fc94cb0aa4e08189cb965
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088495"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="976d7-102">\<limpar > elemento para webRequestModules (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="976d7-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="976d7-103">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="976d7-103">Removes all registered Web request modules from the application.</span></span>  

<span data-ttu-id="976d7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="976d7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="976d7-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="976d7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="976d7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="976d7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="976d7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**desmarque >**</span><span class="sxs-lookup"><span data-stu-id="976d7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="976d7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="976d7-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="976d7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="976d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="976d7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="976d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="976d7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="976d7-111">Attributes</span></span>  
 <span data-ttu-id="976d7-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="976d7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="976d7-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="976d7-113">Child Elements</span></span>  
 <span data-ttu-id="976d7-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="976d7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="976d7-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="976d7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="976d7-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="976d7-116">**Element**</span></span>|<span data-ttu-id="976d7-117">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="976d7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="976d7-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="976d7-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="976d7-119">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="976d7-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="976d7-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="976d7-120">Remarks</span></span>  
 <span data-ttu-id="976d7-121">O elemento `clear` remove todos os módulos de solicitação da Web registrados que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="976d7-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="976d7-122">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="976d7-122">Configuration Files</span></span>  
 <span data-ttu-id="976d7-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="976d7-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="976d7-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="976d7-124">Example</span></span>  
 <span data-ttu-id="976d7-125">O exemplo a seguir limpa todos os módulos de solicitação da Web e registra um módulo de solicitação da Web para HTTP.</span><span class="sxs-lookup"><span data-stu-id="976d7-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="976d7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="976d7-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="976d7-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="976d7-127">Network Settings Schema</span></span>](index.md)
