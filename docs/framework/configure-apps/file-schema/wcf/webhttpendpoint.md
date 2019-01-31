---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 9b4dd3a61a9b5ad1b35cce4025a50ac4220fd77e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256427"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="b7d3f-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="b7d3f-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="b7d3f-102">Este elemento de configuração define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="b7d3f-103">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="b7d3f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7d3f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7d3f-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b7d3f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d3f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7d3f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7d3f-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7d3f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b7d3f-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7d3f-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7d3f-109">Attributes</span></span>  
  
|<span data-ttu-id="b7d3f-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7d3f-110">Attribute</span></span>|<span data-ttu-id="b7d3f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7d3f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7d3f-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="b7d3f-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="b7d3f-113">Um valor booliano que indica se a seleção automática de formato está habilitada.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="b7d3f-114">Quando a seleção automática de formato estiver habilitada, a infra-estrutura analisa o `Accept` cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="b7d3f-115">Se o `Accept` cabeçalho não especifica um formato de resposta adequada, a infraestrutura usa a `Content-Type` da mensagem de solicitação ou o formato da resposta da operação padrão.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="b7d3f-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="b7d3f-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="b7d3f-117">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="b7d3f-118">Esse atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="b7d3f-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="b7d3f-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="b7d3f-119">helpEnabled</span></span>|<span data-ttu-id="b7d3f-120">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="b7d3f-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="b7d3f-121">webEndpointType</span></span>|<span data-ttu-id="b7d3f-122">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7d3f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7d3f-123">Child Elements</span></span>  
 <span data-ttu-id="b7d3f-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7d3f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7d3f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b7d3f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7d3f-126">Element</span></span>|<span data-ttu-id="b7d3f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7d3f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7d3f-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="b7d3f-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b7d3f-129">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="b7d3f-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7d3f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7d3f-130">See also</span></span>
- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
