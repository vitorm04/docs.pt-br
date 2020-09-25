---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177976"
---
# \<webHttpEndpoint>

<span data-ttu-id="b381a-101">Este elemento de configuração define um ponto de extremidade padrão com uma [\<webHttpBinding>](webhttpbinding.md) Associação fixa que adiciona automaticamente o [\<webHttp>](webhttp.md) comportamento.</span><span class="sxs-lookup"><span data-stu-id="b381a-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="b381a-102">Use esse ponto de extremidade ao escrever um serviço REST.</span><span class="sxs-lookup"><span data-stu-id="b381a-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="b381a-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b381a-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b381a-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b381a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b381a-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b381a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b381a-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="b381a-106">Attributes</span></span>  
  
|<span data-ttu-id="b381a-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="b381a-107">Attribute</span></span>|<span data-ttu-id="b381a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b381a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b381a-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="b381a-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="b381a-110">Um valor booliano que indica se a seleção automática de formato está habilitada.</span><span class="sxs-lookup"><span data-stu-id="b381a-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="b381a-111">Quando a seleção de formato automático está habilitada, a infraestrutura analisa o `Accept` cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="b381a-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="b381a-112">Se o `Accept` cabeçalho não especificar um formato de resposta adequado, a infraestrutura usará a `Content-Type` da mensagem de solicitação ou o formato de resposta padrão da operação.</span><span class="sxs-lookup"><span data-stu-id="b381a-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="b381a-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="b381a-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="b381a-114">Um atributo que especifica o formato de resposta de saída padrão.</span><span class="sxs-lookup"><span data-stu-id="b381a-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="b381a-115">Este atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo</span><span class="sxs-lookup"><span data-stu-id="b381a-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="b381a-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="b381a-116">helpEnabled</span></span>|<span data-ttu-id="b381a-117">Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b381a-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="b381a-118">WebEndpointType</span><span class="sxs-lookup"><span data-stu-id="b381a-118">webEndpointType</span></span>|<span data-ttu-id="b381a-119">Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b381a-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b381a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b381a-120">Child Elements</span></span>  

 <span data-ttu-id="b381a-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b381a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b381a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b381a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b381a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="b381a-123">Element</span></span>|<span data-ttu-id="b381a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b381a-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b381a-125">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="b381a-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b381a-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="b381a-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
