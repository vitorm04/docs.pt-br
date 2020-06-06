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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089058"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="fe825-102">Elemento \<webProxyScript> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="fe825-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="fe825-103">Configura as características do script usado para descobrir proxies da Web.</span><span class="sxs-lookup"><span data-stu-id="fe825-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="fe825-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe825-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe825-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe825-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fe825-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fe825-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe825-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe825-107">Attributes</span></span>  
  
|<span data-ttu-id="fe825-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="fe825-108">Attribute</span></span>|<span data-ttu-id="fe825-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe825-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="fe825-110">Especifica o tempo máximo para baixar o script em horas, minutos e segundos.</span><span class="sxs-lookup"><span data-stu-id="fe825-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="fe825-111">O valor padrão é um minuto.</span><span class="sxs-lookup"><span data-stu-id="fe825-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe825-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe825-112">Child Elements</span></span>  
 <span data-ttu-id="fe825-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fe825-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe825-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe825-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fe825-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe825-115">Element</span></span>|<span data-ttu-id="fe825-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe825-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe825-117">configurações</span><span class="sxs-lookup"><span data-stu-id="fe825-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="fe825-118">Configura as opções de rede básicaspara o namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="fe825-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe825-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe825-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fe825-120">Arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="fe825-120">Configuration Files</span></span>  
 <span data-ttu-id="fe825-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="fe825-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe825-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe825-122">See also</span></span>

- [<span data-ttu-id="fe825-123">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="fe825-123">Network Settings Schema</span></span>](index.md)
