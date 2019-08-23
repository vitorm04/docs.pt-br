---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940404"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="b27f2-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="b27f2-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="b27f2-102">Este elemento de configuração define um ponto de extremidade padrão com uma associação WebHttpBinding fixa [ \<>](webhttpbinding.md) que adiciona automaticamente o comportamento de [ \<> enableWebScript](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="b27f2-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="b27f2-103">Use esse ponto de extremidade quando estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b27f2-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="b27f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b27f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b27f2-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b27f2-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27f2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b27f2-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b27f2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b27f2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b27f2-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b27f2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b27f2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b27f2-109">Attributes</span></span>  
  
|<span data-ttu-id="b27f2-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="b27f2-110">Attribute</span></span>|<span data-ttu-id="b27f2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b27f2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b27f2-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="b27f2-112">webEndpointType</span></span>|<span data-ttu-id="b27f2-113">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b27f2-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b27f2-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b27f2-114">Child Elements</span></span>  
 <span data-ttu-id="b27f2-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b27f2-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b27f2-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b27f2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b27f2-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b27f2-117">Element</span></span>|<span data-ttu-id="b27f2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b27f2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b27f2-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b27f2-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="b27f2-120">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="b27f2-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b27f2-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b27f2-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
