---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918995"
---
# <a name="exposedmethod"></a><span data-ttu-id="120cd-101">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="120cd-101">\<exposedMethod></span></span>
<span data-ttu-id="120cd-102">Representa um método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="120cd-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="120cd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="120cd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="120cd-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="120cd-104">\<comContracts></span></span>  
<span data-ttu-id="120cd-105">\<> de descontrato</span><span class="sxs-lookup"><span data-stu-id="120cd-105">\<comContract></span></span>  
<span data-ttu-id="120cd-106">\<métodos ></span><span class="sxs-lookup"><span data-stu-id="120cd-106">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120cd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="120cd-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="120cd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="120cd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="120cd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="120cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="120cd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="120cd-110">Attributes</span></span>  
  
|<span data-ttu-id="120cd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="120cd-111">Attribute</span></span>|<span data-ttu-id="120cd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="120cd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="120cd-113">name</span><span class="sxs-lookup"><span data-stu-id="120cd-113">name</span></span>|<span data-ttu-id="120cd-114">Uma cadeia de caracteres que contém o método COM+ que é exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="120cd-114">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="120cd-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="120cd-115">Child Elements</span></span>  
 <span data-ttu-id="120cd-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="120cd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="120cd-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="120cd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="120cd-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="120cd-118">Element</span></span>|<span data-ttu-id="120cd-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="120cd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="120cd-120">\<exposedMethods></span><span class="sxs-lookup"><span data-stu-id="120cd-120">\<exposedMethods></span></span>](exposedmethods.md)|<span data-ttu-id="120cd-121">Uma coleção de elementos de [ \<> ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="120cd-121">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="120cd-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="120cd-122">Remarks</span></span>  
 <span data-ttu-id="120cd-123">A ferramenta de configuração de integração COM+ (ComSvcConfig. exe) pode ser usada para adicionar métodos específicos de uma interface COM para aparecer no contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="120cd-123">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="120cd-124">Por exemplo, você pode usar o comando a seguir para adicionar os três métodos nomeados `IFinances` da interface com `ItemOrders`no. Componente financeiro, para o contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="120cd-124">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="120cd-125">Quando você também executa o ComSvcConfig. exe, ele gera o seguinte contrato de serviço listando os métodos mencionados anteriormente [ \<](exposedmethod.md) como elementos do ExposedMethod >.</span><span class="sxs-lookup"><span data-stu-id="120cd-125">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="120cd-126">No momento da inicialização do serviço, o tempo de execução tenta gerar um contrato de serviço refletindo e adicionando apenas os métodos incluídos na lista de elementos de [ \<> de ExposedMethod](exposedmethod.md) .</span><span class="sxs-lookup"><span data-stu-id="120cd-126">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="120cd-127">Um rastreamento é produzido para cada método de interface que não está incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="120cd-127">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120cd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="120cd-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [<span data-ttu-id="120cd-129">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="120cd-129">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="120cd-130">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="120cd-130">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="120cd-131">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="120cd-131">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
