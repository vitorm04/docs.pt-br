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
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089058"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="6f39a-102">\<elemento de > webProxyScript (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="6f39a-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="6f39a-103">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="6f39a-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

<span data-ttu-id="6f39a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f39a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f39a-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6f39a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6f39a-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**configurações**](settings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="6f39a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="6f39a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="6f39a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6f39a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f39a-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f39a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f39a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f39a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f39a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f39a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f39a-111">Attributes</span></span>  
  
|<span data-ttu-id="6f39a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="6f39a-112">Attribute</span></span>|<span data-ttu-id="6f39a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f39a-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="6f39a-114">Especifica o tempo máximo para baixar o script em horas, minutos e segundos.</span><span class="sxs-lookup"><span data-stu-id="6f39a-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="6f39a-115">O valor padrão é um minuto.</span><span class="sxs-lookup"><span data-stu-id="6f39a-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f39a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f39a-116">Child Elements</span></span>  
 <span data-ttu-id="6f39a-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f39a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f39a-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f39a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6f39a-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f39a-119">Element</span></span>|<span data-ttu-id="6f39a-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f39a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f39a-121">Configurações</span><span class="sxs-lookup"><span data-stu-id="6f39a-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6f39a-122">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="6f39a-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f39a-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f39a-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6f39a-124">Arquivos de Configuração</span><span class="sxs-lookup"><span data-stu-id="6f39a-124">Configuration Files</span></span>  
 <span data-ttu-id="6f39a-125">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6f39a-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f39a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f39a-126">See also</span></span>

- [<span data-ttu-id="6f39a-127">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="6f39a-127">Network Settings Schema</span></span>](index.md)
