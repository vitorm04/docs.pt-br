---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 524226cbb826486def18c1b3b66c5b4a3c456dec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185672"
---
# \<host>

<span data-ttu-id="77f78-101">Especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="77f78-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="77f78-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77f78-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="77f78-103">Tipo</span><span class="sxs-lookup"><span data-stu-id="77f78-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77f78-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="77f78-104">Attributes and Elements</span></span>  

 <span data-ttu-id="77f78-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="77f78-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77f78-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="77f78-106">Attributes</span></span>  

 <span data-ttu-id="77f78-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="77f78-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="77f78-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="77f78-108">Child Elements</span></span>  
  
|<span data-ttu-id="77f78-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="77f78-109">Element</span></span>|<span data-ttu-id="77f78-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="77f78-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="77f78-111">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="77f78-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="77f78-112">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="77f78-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77f78-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="77f78-113">Parent Elements</span></span>  
  
|<span data-ttu-id="77f78-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="77f78-114">Element</span></span>|<span data-ttu-id="77f78-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="77f78-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="77f78-116">Especifica as configurações para um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="77f78-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77f78-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="77f78-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="77f78-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="77f78-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
