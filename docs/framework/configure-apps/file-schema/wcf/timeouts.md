---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854971"
---
# \<timeOuts>
<span data-ttu-id="6494b-101">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="6494b-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="6494b-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6494b-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6494b-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6494b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6494b-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6494b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6494b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="6494b-105">Attributes</span></span>  
  
|<span data-ttu-id="6494b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="6494b-106">Attribute</span></span>|<span data-ttu-id="6494b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6494b-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6494b-108">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="6494b-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="6494b-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="6494b-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6494b-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6494b-110">Child Elements</span></span>  
 <span data-ttu-id="6494b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6494b-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6494b-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6494b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6494b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6494b-113">Element</span></span>|<span data-ttu-id="6494b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6494b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="6494b-115">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="6494b-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6494b-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6494b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="6494b-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="6494b-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
