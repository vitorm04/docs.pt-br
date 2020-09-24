---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: f7e513bb5c486fa5f7c39c9b2e3cfcd26bd7c219
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157090"
---
# \<timeOuts>

<span data-ttu-id="302a1-101">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="302a1-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="302a1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="302a1-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="302a1-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="302a1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="302a1-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="302a1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="302a1-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="302a1-105">Attributes</span></span>  
  
|<span data-ttu-id="302a1-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="302a1-106">Attribute</span></span>|<span data-ttu-id="302a1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="302a1-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="302a1-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="302a1-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="302a1-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="302a1-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="302a1-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="302a1-110">Child Elements</span></span>  

 <span data-ttu-id="302a1-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="302a1-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="302a1-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="302a1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="302a1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="302a1-113">Element</span></span>|<span data-ttu-id="302a1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="302a1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="302a1-115">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="302a1-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="302a1-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="302a1-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="302a1-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="302a1-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
