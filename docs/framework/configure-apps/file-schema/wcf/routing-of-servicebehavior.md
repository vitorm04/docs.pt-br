---
title: <routing> De <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: b7a9be18395ef8878900d754b5aa5afdeee0cff8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202502"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="a6c5f-102">\<roteamento > de \<serviceBehavior ></span><span class="sxs-lookup"><span data-stu-id="a6c5f-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="a6c5f-103">Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="a6c5f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6c5f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6c5f-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a6c5f-105">\<behaviors></span></span>  
<span data-ttu-id="a6c5f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a6c5f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a6c5f-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a6c5f-107">\<behavior></span></span>  
<span data-ttu-id="a6c5f-108">\<routing></span><span class="sxs-lookup"><span data-stu-id="a6c5f-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c5f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6c5f-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6c5f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6c5f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6c5f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6c5f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6c5f-112">Attributes</span></span>  
  
|<span data-ttu-id="a6c5f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6c5f-113">Attribute</span></span>|<span data-ttu-id="a6c5f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c5f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6c5f-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="a6c5f-115">filterTable</span></span>|<span data-ttu-id="a6c5f-116">Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém os filtros a ser avaliada pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="a6c5f-117">Esse valor deve corresponder a `name` atributo de um [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) elemento no [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) seção.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="a6c5f-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="a6c5f-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="a6c5f-119">Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho ou apenas o cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="a6c5f-120">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-120">The default is `true`.</span></span>|  
|<span data-ttu-id="a6c5f-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="a6c5f-121">soapProcessingEnabled</span></span>|<span data-ttu-id="a6c5f-122">Um valor booliano que especifica se o processamento SOAP deve ocorrer.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6c5f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6c5f-123">Child Elements</span></span>  
 <span data-ttu-id="a6c5f-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6c5f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6c5f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a6c5f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6c5f-126">Element</span></span>|<span data-ttu-id="a6c5f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6c5f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6c5f-128">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a6c5f-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6c5f-129">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6c5f-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6c5f-130">Remarks</span></span>  
 <span data-ttu-id="a6c5f-131">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração permite que o roteamento para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="a6c5f-132">Você pode especificar a tabela de roteamento real a ser usado pelo serviço nesse elemento.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="a6c5f-133">Usando essa seção de configuração, você pode alterar suas configurações de roteamentos em tempo real quando seu padrão de implantação é alterado.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="a6c5f-134">Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamentos e o serviço de roteamento começarão a usar as informações de configuração atualizados para novas mensagens e sessões, deixando as mensagens em trânsito/sessões usando as regras que estavam em Coloque quando foram iniciados.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="a6c5f-135">Isso lhe dá a capacidade de fazer a reconfiguração de sessão segura, sem a reciclagem do serviço de roteamento de durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6c5f-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
