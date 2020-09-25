---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 572ff7e119828897860944a430e5f51f5d1c3cad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194837"
---
# \<workflowControlEndpoint>

<span data-ttu-id="0d026-101">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, encerrar, etc.).</span><span class="sxs-lookup"><span data-stu-id="0d026-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0d026-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d026-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d026-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d026-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0d026-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d026-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d026-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d026-105">Attributes</span></span>  
  
|<span data-ttu-id="0d026-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d026-106">Attribute</span></span>|<span data-ttu-id="0d026-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d026-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d026-108">name</span><span class="sxs-lookup"><span data-stu-id="0d026-108">name</span></span>|<span data-ttu-id="0d026-109">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="0d026-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0d026-110">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="0d026-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d026-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d026-111">Child Elements</span></span>  

 <span data-ttu-id="0d026-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0d026-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d026-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d026-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0d026-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d026-114">Element</span></span>|<span data-ttu-id="0d026-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d026-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0d026-116">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="0d026-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d026-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="0d026-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
