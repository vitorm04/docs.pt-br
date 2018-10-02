---
title: '&lt;webProxyScript&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1450d2df424b32aacc5c113b5936001f65915a
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862731"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="b0acb-102">&lt;webProxyScript&gt; (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="b0acb-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b0acb-103">Configura as características do script usado para descobrir os proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="b0acb-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="b0acb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b0acb-104">\<configuration></span></span>  
<span data-ttu-id="b0acb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b0acb-105">\<system.net></span></span>  
<span data-ttu-id="b0acb-106">\<Configurações ></span><span class="sxs-lookup"><span data-stu-id="b0acb-106">\<settings></span></span>  
<span data-ttu-id="b0acb-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="b0acb-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0acb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0acb-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0acb-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b0acb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b0acb-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b0acb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0acb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b0acb-111">Attributes</span></span>  
  
|<span data-ttu-id="b0acb-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b0acb-112">Attribute</span></span>|<span data-ttu-id="b0acb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0acb-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="b0acb-114">Especifica o tempo máximo para baixar o script em horas, minutos e segundos.</span><span class="sxs-lookup"><span data-stu-id="b0acb-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="b0acb-115">O valor padrão é um minuto.</span><span class="sxs-lookup"><span data-stu-id="b0acb-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0acb-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b0acb-116">Child Elements</span></span>  
 <span data-ttu-id="b0acb-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b0acb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0acb-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b0acb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b0acb-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b0acb-119">Element</span></span>|<span data-ttu-id="b0acb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0acb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0acb-121">settings</span><span class="sxs-lookup"><span data-stu-id="b0acb-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="b0acb-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="b0acb-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0acb-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0acb-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b0acb-124">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="b0acb-124">Configuration Files</span></span>  
 <span data-ttu-id="b0acb-125">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b0acb-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0acb-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0acb-126">See Also</span></span>  
 [<span data-ttu-id="b0acb-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="b0acb-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
