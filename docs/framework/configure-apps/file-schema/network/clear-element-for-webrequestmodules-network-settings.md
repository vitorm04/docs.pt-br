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
ms.openlocfilehash: 892058dd8af8a38bd7bde868b34a2c6899d9a989
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184034"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="9ee37-102">Elemento \<clear> para webRequestModules (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="9ee37-102">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="9ee37-103">Remove todos os módulos de solicitação da Web registrados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ee37-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="9ee37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ee37-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ee37-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9ee37-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9ee37-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9ee37-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ee37-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ee37-107">Attributes</span></span>  

 <span data-ttu-id="9ee37-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9ee37-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ee37-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ee37-109">Child Elements</span></span>  

 <span data-ttu-id="9ee37-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9ee37-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ee37-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9ee37-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9ee37-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="9ee37-112">**Element**</span></span>|<span data-ttu-id="9ee37-113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9ee37-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9ee37-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9ee37-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="9ee37-115">Especifica os módulos a serem usados para solicitar informações de hosts de rede.</span><span class="sxs-lookup"><span data-stu-id="9ee37-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee37-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ee37-116">Remarks</span></span>  

 <span data-ttu-id="9ee37-117">O `clear` elemento remove todos os módulos de solicitação da Web registrados que foram definidos anteriormente no arquivo de configuração ou em um nível superior na hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="9ee37-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9ee37-118">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="9ee37-118">Configuration Files</span></span>  

 <span data-ttu-id="9ee37-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9ee37-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ee37-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ee37-120">Example</span></span>  

 <span data-ttu-id="9ee37-121">O exemplo a seguir limpa todos os módulos de solicitação da Web e registra um módulo de solicitação da Web para HTTP.</span><span class="sxs-lookup"><span data-stu-id="9ee37-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ee37-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="9ee37-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="9ee37-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9ee37-123">Network Settings Schema</span></span>](index.md)
