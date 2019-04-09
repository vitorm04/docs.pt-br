---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 6fb31fca6ac38f6cb92ef087cc277a4d5066521c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182449"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="e4274-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="e4274-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="e4274-102">Este elemento de configuração define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="e4274-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="e4274-103">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="e4274-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="e4274-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4274-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4274-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e4274-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4274-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4274-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4274-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e4274-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e4274-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e4274-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4274-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e4274-109">Attributes</span></span>  
  
|<span data-ttu-id="e4274-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="e4274-110">Attribute</span></span>|<span data-ttu-id="e4274-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4274-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4274-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="e4274-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="e4274-113">Um valor booliano que indica se a seleção automática de formato está habilitada.</span><span class="sxs-lookup"><span data-stu-id="e4274-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="e4274-114">Quando a seleção automática de formato estiver habilitada, a infra-estrutura analisa o `Accept` cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="e4274-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="e4274-115">Se o `Accept` cabeçalho não especifica um formato de resposta adequada, a infraestrutura usa a `Content-Type` da mensagem de solicitação ou o formato da resposta da operação padrão.</span><span class="sxs-lookup"><span data-stu-id="e4274-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="e4274-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="e4274-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="e4274-117">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="e4274-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="e4274-118">Esse atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="e4274-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="e4274-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="e4274-119">helpEnabled</span></span>|<span data-ttu-id="e4274-120">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e4274-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="e4274-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e4274-121">webEndpointType</span></span>|<span data-ttu-id="e4274-122">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e4274-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4274-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e4274-123">Child Elements</span></span>  
 <span data-ttu-id="e4274-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e4274-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4274-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e4274-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e4274-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4274-126">Element</span></span>|<span data-ttu-id="e4274-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4274-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4274-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e4274-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e4274-129">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="e4274-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4274-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4274-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
