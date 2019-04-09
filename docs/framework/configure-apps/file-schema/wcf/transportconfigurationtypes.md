---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: b3683a198ec403fb9966bb902c936108fd043bfa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083634"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="cc739-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="cc739-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="cc739-102">Representa uma coleção de elementos de configuração que identificam o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="cc739-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="cc739-103">Isso pode ser usado para adicionar protocolos personalizados do WAS.</span><span class="sxs-lookup"><span data-stu-id="cc739-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="cc739-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc739-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc739-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="cc739-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="cc739-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="cc739-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc739-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc739-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc739-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc739-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cc739-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cc739-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc739-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc739-110">Attributes</span></span>  
  
|<span data-ttu-id="cc739-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="cc739-111">Attribute</span></span>|<span data-ttu-id="cc739-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc739-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc739-113">name</span><span class="sxs-lookup"><span data-stu-id="cc739-113">name</span></span>|<span data-ttu-id="cc739-114">O nome do transporte</span><span class="sxs-lookup"><span data-stu-id="cc739-114">The name of the transport</span></span>|  
|<span data-ttu-id="cc739-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="cc739-115">transportConfigurationType</span></span>|<span data-ttu-id="cc739-116">O tipo que implementa o transporte</span><span class="sxs-lookup"><span data-stu-id="cc739-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc739-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc739-117">Child Elements</span></span>  
  
|<span data-ttu-id="cc739-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc739-118">Element</span></span>|<span data-ttu-id="cc739-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc739-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc739-120">\<add></span><span class="sxs-lookup"><span data-stu-id="cc739-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="cc739-121">Adiciona um elemento de configuração que identifica o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="cc739-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc739-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc739-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cc739-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc739-123">Element</span></span>|<span data-ttu-id="cc739-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc739-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc739-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="cc739-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="cc739-126">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="cc739-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc739-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc739-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="cc739-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="cc739-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
