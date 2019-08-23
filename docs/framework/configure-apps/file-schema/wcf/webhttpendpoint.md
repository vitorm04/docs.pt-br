---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940477"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="e0d33-101">\<> webHttpEndpoint</span><span class="sxs-lookup"><span data-stu-id="e0d33-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="e0d33-102">Este elemento de configuração define um ponto de extremidade padrão com uma associação WebHttpBinding fixa [ \<>](webhttpbinding.md) que adiciona automaticamente o comportamento de [ \<> Webhttp](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="e0d33-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="e0d33-103">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="e0d33-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="e0d33-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e0d33-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0d33-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e0d33-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d33-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0d33-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0d33-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e0d33-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e0d33-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e0d33-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0d33-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0d33-109">Attributes</span></span>  
  
|<span data-ttu-id="e0d33-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="e0d33-110">Attribute</span></span>|<span data-ttu-id="e0d33-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0d33-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0d33-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="e0d33-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="e0d33-113">Um valor booliano que indica se a seleção automática de formato está habilitada.</span><span class="sxs-lookup"><span data-stu-id="e0d33-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="e0d33-114">Quando a seleção de formato automático está habilitada, a infraestrutura `Accept` analisa o cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="e0d33-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="e0d33-115">Se o `Accept` cabeçalho não especificar um formato de resposta adequado, a infraestrutura usará `Content-Type` a da mensagem de solicitação ou o formato de resposta padrão da operação.</span><span class="sxs-lookup"><span data-stu-id="e0d33-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="e0d33-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="e0d33-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="e0d33-117">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="e0d33-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="e0d33-118">Este atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="e0d33-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="e0d33-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="e0d33-119">helpEnabled</span></span>|<span data-ttu-id="e0d33-120">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e0d33-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="e0d33-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e0d33-121">webEndpointType</span></span>|<span data-ttu-id="e0d33-122">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e0d33-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0d33-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e0d33-123">Child Elements</span></span>  
 <span data-ttu-id="e0d33-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e0d33-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0d33-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e0d33-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e0d33-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0d33-126">Element</span></span>|<span data-ttu-id="e0d33-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0d33-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d33-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e0d33-128">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e0d33-129">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="e0d33-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0d33-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0d33-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
