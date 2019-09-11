---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854788"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="7c572-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="7c572-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="7c572-102">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, encerrar, etc.).</span><span class="sxs-lookup"><span data-stu-id="7c572-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="7c572-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c572-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c572-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7c572-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7c572-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="7c572-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="7c572-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowControlEndpoint**</span><span class="sxs-lookup"><span data-stu-id="7c572-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c572-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c572-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c572-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c572-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c572-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c572-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c572-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c572-110">Attributes</span></span>  
  
|<span data-ttu-id="7c572-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7c572-111">Attribute</span></span>|<span data-ttu-id="7c572-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c572-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c572-113">name</span><span class="sxs-lookup"><span data-stu-id="7c572-113">name</span></span>|<span data-ttu-id="7c572-114">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="7c572-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="7c572-115">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular um ponto de extremidade padrão à sua configuração.</span><span class="sxs-lookup"><span data-stu-id="7c572-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c572-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c572-116">Child Elements</span></span>  
 <span data-ttu-id="7c572-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7c572-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c572-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c572-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7c572-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c572-119">Element</span></span>|<span data-ttu-id="7c572-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c572-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c572-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7c572-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="7c572-122">Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.</span><span class="sxs-lookup"><span data-stu-id="7c572-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c572-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c572-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
