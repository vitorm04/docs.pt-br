---
title: Elemento <webProxyScript> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 2abab3de2965c31c11d9acaf7b78f3a668563506
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697451"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="d0663-102">\<webProxyScript > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="d0663-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="d0663-103">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="d0663-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
[<span data-ttu-id="d0663-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="d0663-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d0663-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d0663-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="d0663-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d0663-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="d0663-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="d0663-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0663-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0663-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0663-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0663-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0663-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0663-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0663-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0663-111">Attributes</span></span>  
  
|<span data-ttu-id="d0663-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0663-112">Attribute</span></span>|<span data-ttu-id="d0663-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0663-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="d0663-114">Especifica o tempo máximo para baixar o script em horas, minutos e segundos.</span><span class="sxs-lookup"><span data-stu-id="d0663-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="d0663-115">O valor padrão é um minuto.</span><span class="sxs-lookup"><span data-stu-id="d0663-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0663-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0663-116">Child Elements</span></span>  
 <span data-ttu-id="d0663-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d0663-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0663-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0663-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d0663-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0663-119">Element</span></span>|<span data-ttu-id="d0663-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0663-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0663-121">settings</span><span class="sxs-lookup"><span data-stu-id="d0663-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d0663-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="d0663-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0663-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0663-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d0663-124">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="d0663-124">Configuration Files</span></span>  
 <span data-ttu-id="d0663-125">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d0663-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0663-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0663-126">See also</span></span>

- [<span data-ttu-id="d0663-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="d0663-127">Network Settings Schema</span></span>](index.md)
