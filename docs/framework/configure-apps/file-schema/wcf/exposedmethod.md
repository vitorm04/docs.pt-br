---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 2947f0de6a88f39463e58a3b39bda52588fe4baa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203898"
---
# \<exposedMethod>

<span data-ttu-id="048fb-101">Representa um método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="048fb-101">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="048fb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="048fb-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="048fb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="048fb-103">Attributes and Elements</span></span>  

 <span data-ttu-id="048fb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="048fb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="048fb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="048fb-105">Attributes</span></span>  
  
|<span data-ttu-id="048fb-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="048fb-106">Attribute</span></span>|<span data-ttu-id="048fb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="048fb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="048fb-108">name</span><span class="sxs-lookup"><span data-stu-id="048fb-108">name</span></span>|<span data-ttu-id="048fb-109">Uma cadeia de caracteres que contém o método COM+ que é exposto quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="048fb-109">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="048fb-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="048fb-110">Child Elements</span></span>  

 <span data-ttu-id="048fb-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="048fb-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="048fb-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="048fb-112">Parent Elements</span></span>  
  
|<span data-ttu-id="048fb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="048fb-113">Element</span></span>|<span data-ttu-id="048fb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="048fb-114">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="048fb-115">Uma coleção de [\<exposedMethod>](exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="048fb-115">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="048fb-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="048fb-116">Remarks</span></span>  

 <span data-ttu-id="048fb-117">A ferramenta de configuração de integração COM+ (ComSvcConfig.exe) pode ser usada para adicionar métodos específicos de uma interface COM para aparecer no contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="048fb-117">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="048fb-118">Por exemplo, você pode usar o comando a seguir para adicionar os três métodos nomeados da `IFinances` interface com no `ItemOrders` . Componente financeiro, para o contrato de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="048fb-118">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="048fb-119">Quando você também executa o ComSvcConfig.exe, ele gera o seguinte contrato de serviço listando os métodos mencionados anteriormente como [\<exposedMethod>](exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="048fb-119">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="048fb-120">No momento da inicialização do serviço, o tempo de execução tenta gerar um contrato de serviço refletindo e adicionando apenas os métodos incluídos na lista de [\<exposedMethod>](exposedmethod.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="048fb-120">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="048fb-121">Um rastreamento é produzido para cada método de interface que não está incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="048fb-121">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048fb-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="048fb-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="048fb-123">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="048fb-123">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="048fb-124">Como: definir configurações de serviço de COM+</span><span class="sxs-lookup"><span data-stu-id="048fb-124">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
