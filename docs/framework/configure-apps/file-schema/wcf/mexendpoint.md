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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6eefecb696c88d160e56c7f12a1b03ea67e531b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="428e5-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="428e5-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="428e5-103">Este elemento de configuração define um ponto de extremidade padrão com um contrato IMetadataExchange fixo.</span><span class="sxs-lookup"><span data-stu-id="428e5-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="428e5-104">Desde que todos os pontos de extremidade de troca de metadados especificarem IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="428e5-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="428e5-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="428e5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="428e5-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="428e5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428e5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="428e5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="428e5-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="428e5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="428e5-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="428e5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="428e5-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="428e5-110">Attributes</span></span>  
  
|<span data-ttu-id="428e5-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="428e5-111">Attribute</span></span>|<span data-ttu-id="428e5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="428e5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="428e5-113">name</span><span class="sxs-lookup"><span data-stu-id="428e5-113">name</span></span>|<span data-ttu-id="428e5-114">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="428e5-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="428e5-115">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="428e5-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="428e5-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="428e5-116">Child Elements</span></span>  
 <span data-ttu-id="428e5-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="428e5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="428e5-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="428e5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="428e5-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="428e5-119">Element</span></span>|<span data-ttu-id="428e5-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="428e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="428e5-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="428e5-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="428e5-122">Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="428e5-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
