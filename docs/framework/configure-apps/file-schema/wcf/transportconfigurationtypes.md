---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941166"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="c6c27-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c6c27-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="c6c27-102">Representa uma coleção de elementos de configuração que identificam o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c6c27-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="c6c27-103">Isso pode ser usado para adicionar protocolos WAS personalizados.</span><span class="sxs-lookup"><span data-stu-id="c6c27-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="c6c27-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c6c27-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6c27-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c6c27-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="c6c27-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c6c27-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c27-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6c27-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6c27-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6c27-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c6c27-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6c27-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6c27-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6c27-110">Attributes</span></span>  
  
|<span data-ttu-id="c6c27-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6c27-111">Attribute</span></span>|<span data-ttu-id="c6c27-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c27-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6c27-113">name</span><span class="sxs-lookup"><span data-stu-id="c6c27-113">name</span></span>|<span data-ttu-id="c6c27-114">O nome do transporte</span><span class="sxs-lookup"><span data-stu-id="c6c27-114">The name of the transport</span></span>|  
|<span data-ttu-id="c6c27-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c6c27-115">transportConfigurationType</span></span>|<span data-ttu-id="c6c27-116">O tipo que implementa o transporte</span><span class="sxs-lookup"><span data-stu-id="c6c27-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6c27-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6c27-117">Child Elements</span></span>  
  
|<span data-ttu-id="c6c27-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6c27-118">Element</span></span>|<span data-ttu-id="c6c27-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c27-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c27-120">\<add></span><span class="sxs-lookup"><span data-stu-id="c6c27-120">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="c6c27-121">Adiciona um elemento de configuração que identifica o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c6c27-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6c27-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6c27-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6c27-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6c27-123">Element</span></span>|<span data-ttu-id="c6c27-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6c27-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c27-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c6c27-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="c6c27-126">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="c6c27-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6c27-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6c27-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="c6c27-128">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6c27-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
