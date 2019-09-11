---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854803"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="6d785-101">\<> webHttpEndpoint</span><span class="sxs-lookup"><span data-stu-id="6d785-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="6d785-102">Este elemento de configuração define um ponto de extremidade padrão com uma associação [ \<WebHttpBinding fixa >](webhttpbinding.md) que adiciona automaticamente o comportamento de [ \<> Webhttp](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="6d785-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="6d785-103">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="6d785-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="6d785-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6d785-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6d785-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6d785-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6d785-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="6d785-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="6d785-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> webHttpEndpoint**</span><span class="sxs-lookup"><span data-stu-id="6d785-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d785-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d785-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d785-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6d785-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6d785-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6d785-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d785-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6d785-111">Attributes</span></span>  
  
|<span data-ttu-id="6d785-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="6d785-112">Attribute</span></span>|<span data-ttu-id="6d785-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d785-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d785-114">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="6d785-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="6d785-115">Um valor booliano que indica se a seleção automática de formato está habilitada.</span><span class="sxs-lookup"><span data-stu-id="6d785-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="6d785-116">Quando a seleção de formato automático está habilitada, a infraestrutura `Accept` analisa o cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="6d785-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="6d785-117">Se o `Accept` cabeçalho não especificar um formato de resposta adequado, a infraestrutura usará `Content-Type` a da mensagem de solicitação ou o formato de resposta padrão da operação.</span><span class="sxs-lookup"><span data-stu-id="6d785-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="6d785-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="6d785-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="6d785-119">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="6d785-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="6d785-120">Este atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="6d785-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="6d785-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="6d785-121">helpEnabled</span></span>|<span data-ttu-id="6d785-122">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6d785-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="6d785-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="6d785-123">webEndpointType</span></span>|<span data-ttu-id="6d785-124">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6d785-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d785-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6d785-125">Child Elements</span></span>  
 <span data-ttu-id="6d785-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6d785-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d785-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6d785-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6d785-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="6d785-128">Element</span></span>|<span data-ttu-id="6d785-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d785-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d785-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="6d785-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="6d785-131">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="6d785-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d785-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d785-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
