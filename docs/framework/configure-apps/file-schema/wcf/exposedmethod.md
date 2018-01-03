---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e5c9f61d67850d249d54ed5adfc08bf40bad47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="10901-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="10901-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="10901-103">Representa um método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="10901-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="10901-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="10901-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="10901-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="10901-105">\<comContracts></span></span>  
<span data-ttu-id="10901-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="10901-106">\<comContract></span></span>  
<span data-ttu-id="10901-107">\<métodos ></span><span class="sxs-lookup"><span data-stu-id="10901-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10901-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10901-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10901-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10901-109">Attributes and Elements</span></span>  
 <span data-ttu-id="10901-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="10901-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10901-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="10901-111">Attributes</span></span>  
  
|<span data-ttu-id="10901-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="10901-112">Attribute</span></span>|<span data-ttu-id="10901-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="10901-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10901-114">name</span><span class="sxs-lookup"><span data-stu-id="10901-114">name</span></span>|<span data-ttu-id="10901-115">Uma cadeia de caracteres que contém o método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="10901-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10901-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10901-116">Child Elements</span></span>  
 <span data-ttu-id="10901-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="10901-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10901-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10901-118">Parent Elements</span></span>  
  
|<span data-ttu-id="10901-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="10901-119">Element</span></span>|<span data-ttu-id="10901-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="10901-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10901-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="10901-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="10901-122">Uma coleção de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="10901-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10901-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="10901-123">Remarks</span></span>  
 <span data-ttu-id="10901-124">COM+ integration ferramenta de configuração (ComSvcConfig.exe) pode ser usada para adicionar métodos específicos de uma interface COM apareçam no contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="10901-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="10901-125">Por exemplo, você pode usar o comando a seguir para adicionar três métodos nomeados no `IFinances` interface COM o `ItemOrders`. Componente financeiro ao contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="10901-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="10901-126">Quando você também pode executar o ComSvcConfig.exe, em seguida, gera o seguinte contrato de serviço listando os métodos mencionados anteriormente como [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="10901-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="10901-127">No momento da inicialização de serviço, o tempo de execução tenta gerar um contrato de serviço refletir sobre e adicionando apenas os métodos incluídos na lista de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="10901-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="10901-128">Um rastreamento é produzido para cada método de interface não está incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="10901-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10901-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10901-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="10901-130">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="10901-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="10901-131">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="10901-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="10901-132">Como definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="10901-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
