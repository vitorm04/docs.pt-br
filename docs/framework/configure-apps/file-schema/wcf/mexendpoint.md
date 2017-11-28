---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75886c08d3e358d4ed6d3d3048594ef28f06a7af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="58c5f-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="58c5f-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="58c5f-103">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="58c5f-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="58c5f-104">Desde que todos os pontos de extremidade de troca de metadados especificarem IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="58c5f-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="58c5f-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="58c5f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="58c5f-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="58c5f-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c5f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58c5f-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58c5f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58c5f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="58c5f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58c5f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58c5f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="58c5f-110">Attributes</span></span>  
  
|<span data-ttu-id="58c5f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="58c5f-111">Attribute</span></span>|<span data-ttu-id="58c5f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="58c5f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58c5f-113">name</span><span class="sxs-lookup"><span data-stu-id="58c5f-113">name</span></span>|<span data-ttu-id="58c5f-114">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="58c5f-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="58c5f-115">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="58c5f-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58c5f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58c5f-116">Child Elements</span></span>  
 <span data-ttu-id="58c5f-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="58c5f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58c5f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58c5f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="58c5f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="58c5f-119">Element</span></span>|<span data-ttu-id="58c5f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="58c5f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58c5f-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="58c5f-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="58c5f-122">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="58c5f-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
