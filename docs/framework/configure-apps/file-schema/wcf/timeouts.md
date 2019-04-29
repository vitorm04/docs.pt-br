---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758217"
---
# <a name="timeouts"></a><span data-ttu-id="cbc36-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="cbc36-101">\<timeOuts></span></span>
<span data-ttu-id="cbc36-102">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="cbc36-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="cbc36-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cbc36-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="cbc36-104">\<client></span><span class="sxs-lookup"><span data-stu-id="cbc36-104">\<client></span></span>  
<span data-ttu-id="cbc36-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="cbc36-105">\<endpoint></span></span>  
<span data-ttu-id="cbc36-106">\<host></span><span class="sxs-lookup"><span data-stu-id="cbc36-106">\<host></span></span>  
<span data-ttu-id="cbc36-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="cbc36-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc36-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbc36-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbc36-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cbc36-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cbc36-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cbc36-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbc36-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="cbc36-111">Attributes</span></span>  
  
|<span data-ttu-id="cbc36-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="cbc36-112">Attribute</span></span>|<span data-ttu-id="cbc36-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbc36-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="cbc36-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="cbc36-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="cbc36-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="cbc36-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbc36-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cbc36-116">Child Elements</span></span>  
 <span data-ttu-id="cbc36-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="cbc36-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbc36-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cbc36-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cbc36-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="cbc36-119">Element</span></span>|<span data-ttu-id="cbc36-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbc36-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbc36-121">\<host></span><span class="sxs-lookup"><span data-stu-id="cbc36-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="cbc36-122">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="cbc36-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbc36-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbc36-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="cbc36-124">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="cbc36-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
