---
title: <security> de <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936553"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="35919-102">\<> de segurança \<do WSDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="35919-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="35919-103">Define os recursos de segurança do [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="35919-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="35919-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35919-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="35919-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="35919-105">\<bindings></span></span>  
<span data-ttu-id="35919-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="35919-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="35919-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="35919-107">\<binding></span></span>  
<span data-ttu-id="35919-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="35919-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35919-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35919-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35919-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="35919-110">Attributes and Elements</span></span>  
 <span data-ttu-id="35919-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="35919-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35919-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="35919-112">Attributes</span></span>  
  
|<span data-ttu-id="35919-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="35919-113">Attribute</span></span>|<span data-ttu-id="35919-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="35919-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35919-115">modo</span><span class="sxs-lookup"><span data-stu-id="35919-115">mode</span></span>|<span data-ttu-id="35919-116">Adicional.</span><span class="sxs-lookup"><span data-stu-id="35919-116">-   Optional.</span></span> <span data-ttu-id="35919-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="35919-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="35919-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="35919-118">The default value is `Message`.</span></span> <span data-ttu-id="35919-119">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="35919-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="35919-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="35919-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="35919-121">Valor</span><span class="sxs-lookup"><span data-stu-id="35919-121">Value</span></span>|<span data-ttu-id="35919-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="35919-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="35919-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="35919-123">None</span></span>|<span data-ttu-id="35919-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="35919-124">Security is disabled.</span></span>|  
|<span data-ttu-id="35919-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="35919-125">Message</span></span>|<span data-ttu-id="35919-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="35919-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35919-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="35919-127">Child Elements</span></span>  
  
|<span data-ttu-id="35919-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="35919-128">Element</span></span>|<span data-ttu-id="35919-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="35919-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35919-130">\<message></span><span class="sxs-lookup"><span data-stu-id="35919-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="35919-131">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="35919-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="35919-132">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="35919-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35919-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="35919-133">Parent Elements</span></span>  
  
|<span data-ttu-id="35919-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="35919-134">Element</span></span>|<span data-ttu-id="35919-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="35919-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35919-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="35919-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="35919-137">Define todos os recursos de associação do [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="35919-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35919-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="35919-138">Remarks</span></span>  
 <span data-ttu-id="35919-139">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="35919-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="35919-140">O cliente deve usar a segurança para garantir que ele se conecte apenas aos serviços que confia.</span><span class="sxs-lookup"><span data-stu-id="35919-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35919-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35919-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="35919-142">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="35919-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="35919-143">Associações</span><span class="sxs-lookup"><span data-stu-id="35919-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="35919-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="35919-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="35919-145">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="35919-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="35919-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="35919-146">\<binding></span></span>](../../../misc/binding.md)
