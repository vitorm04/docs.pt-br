---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271688"
---
# <a name="mexendpoint"></a><span data-ttu-id="df8fc-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="df8fc-101">\<mexEndpoint></span></span>
<span data-ttu-id="df8fc-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="df8fc-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="df8fc-103">Uma vez que todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="df8fc-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="df8fc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="df8fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="df8fc-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="df8fc-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8fc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df8fc-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df8fc-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df8fc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="df8fc-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df8fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df8fc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="df8fc-109">Attributes</span></span>  
  
|<span data-ttu-id="df8fc-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="df8fc-110">Attribute</span></span>|<span data-ttu-id="df8fc-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="df8fc-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df8fc-112">name</span><span class="sxs-lookup"><span data-stu-id="df8fc-112">name</span></span>|<span data-ttu-id="df8fc-113">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="df8fc-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="df8fc-114">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="df8fc-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df8fc-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df8fc-115">Child Elements</span></span>  
 <span data-ttu-id="df8fc-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="df8fc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df8fc-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df8fc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df8fc-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="df8fc-118">Element</span></span>|<span data-ttu-id="df8fc-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="df8fc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df8fc-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="df8fc-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="df8fc-121">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="df8fc-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
