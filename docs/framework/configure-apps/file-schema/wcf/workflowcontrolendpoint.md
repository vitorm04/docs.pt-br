---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 178ccc8ac35b0ac76d74c818dce43dcffc5c0835
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144945"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="e10fb-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="e10fb-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="e10fb-103">Este elemento de configuração define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, finalizar, etc).</span><span class="sxs-lookup"><span data-stu-id="e10fb-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="e10fb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e10fb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e10fb-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e10fb-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10fb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e10fb-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e10fb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e10fb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e10fb-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e10fb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e10fb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e10fb-109">Attributes</span></span>  
  
|<span data-ttu-id="e10fb-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="e10fb-110">Attribute</span></span>|<span data-ttu-id="e10fb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e10fb-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e10fb-112">name</span><span class="sxs-lookup"><span data-stu-id="e10fb-112">name</span></span>|<span data-ttu-id="e10fb-113">Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="e10fb-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e10fb-114">O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.</span><span class="sxs-lookup"><span data-stu-id="e10fb-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e10fb-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e10fb-115">Child Elements</span></span>  
 <span data-ttu-id="e10fb-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e10fb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e10fb-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e10fb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e10fb-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e10fb-118">Element</span></span>|<span data-ttu-id="e10fb-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e10fb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e10fb-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e10fb-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e10fb-121">Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.</span><span class="sxs-lookup"><span data-stu-id="e10fb-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e10fb-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e10fb-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
