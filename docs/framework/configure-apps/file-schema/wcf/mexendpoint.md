---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931251"
---
# <a name="mexendpoint"></a><span data-ttu-id="fe5f6-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="fe5f6-101">\<mexEndpoint></span></span>
<span data-ttu-id="fe5f6-102">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="fe5f6-103">Como todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um para você mesmo.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="fe5f6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fe5f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fe5f6-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="fe5f6-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5f6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe5f6-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe5f6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe5f6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fe5f6-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe5f6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe5f6-109">Attributes</span></span>  
  
|<span data-ttu-id="fe5f6-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="fe5f6-110">Attribute</span></span>|<span data-ttu-id="fe5f6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe5f6-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe5f6-112">name</span><span class="sxs-lookup"><span data-stu-id="fe5f6-112">name</span></span>|<span data-ttu-id="fe5f6-113">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="fe5f6-114">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe5f6-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe5f6-115">Child Elements</span></span>  
 <span data-ttu-id="fe5f6-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe5f6-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe5f6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fe5f6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe5f6-118">Element</span></span>|<span data-ttu-id="fe5f6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe5f6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe5f6-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="fe5f6-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="fe5f6-121">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
