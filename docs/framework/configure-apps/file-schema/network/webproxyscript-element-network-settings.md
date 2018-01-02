---
title: "&lt;webProxyScript&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="b6227-102">&lt;webProxyScript&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="b6227-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b6227-103">Define as características do script usado para descobrir os proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="b6227-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="b6227-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b6227-104">\<configuration></span></span>  
<span data-ttu-id="b6227-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="b6227-105">\<system.net></span></span>  
<span data-ttu-id="b6227-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="b6227-106">\<settings></span></span>  
<span data-ttu-id="b6227-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="b6227-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6227-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6227-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6227-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b6227-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6227-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b6227-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6227-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b6227-111">Attributes</span></span>  
  
|<span data-ttu-id="b6227-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b6227-112">Attribute</span></span>|<span data-ttu-id="b6227-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6227-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="b6227-114">Especifica o tempo máximo para baixar o script em horas, minutos e segundos.</span><span class="sxs-lookup"><span data-stu-id="b6227-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="b6227-115">O valor padrão é um minuto.</span><span class="sxs-lookup"><span data-stu-id="b6227-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6227-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b6227-116">Child Elements</span></span>  
 <span data-ttu-id="b6227-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b6227-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6227-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b6227-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b6227-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b6227-119">Element</span></span>|<span data-ttu-id="b6227-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6227-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6227-121">Configurações</span><span class="sxs-lookup"><span data-stu-id="b6227-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="b6227-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b6227-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6227-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6227-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b6227-124">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b6227-124">Configuration Files</span></span>  
 <span data-ttu-id="b6227-125">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b6227-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6227-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6227-126">See Also</span></span>  
 [<span data-ttu-id="b6227-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b6227-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
