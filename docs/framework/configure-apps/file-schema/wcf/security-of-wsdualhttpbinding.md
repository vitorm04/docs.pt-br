---
title: <security> De <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: c6f9e34724ccc3a0d05da3e1886b4f0bcbaae064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171503"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="e26e0-102">\<segurança > de \<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e26e0-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="e26e0-103">Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e26e0-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e26e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e26e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e26e0-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e26e0-105">\<bindings></span></span>  
<span data-ttu-id="e26e0-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e26e0-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="e26e0-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="e26e0-107">\<binding></span></span>  
<span data-ttu-id="e26e0-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="e26e0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e26e0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e26e0-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e26e0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e26e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e26e0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e26e0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e26e0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e26e0-112">Attributes</span></span>  
  
|<span data-ttu-id="e26e0-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e26e0-113">Attribute</span></span>|<span data-ttu-id="e26e0-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26e0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e26e0-115">modo</span><span class="sxs-lookup"><span data-stu-id="e26e0-115">mode</span></span>|<span data-ttu-id="e26e0-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="e26e0-116">-   Optional.</span></span> <span data-ttu-id="e26e0-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="e26e0-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e26e0-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="e26e0-118">The default value is `Message`.</span></span> <span data-ttu-id="e26e0-119">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e26e0-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e26e0-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="e26e0-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="e26e0-121">Valor</span><span class="sxs-lookup"><span data-stu-id="e26e0-121">Value</span></span>|<span data-ttu-id="e26e0-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26e0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e26e0-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e26e0-123">None</span></span>|<span data-ttu-id="e26e0-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="e26e0-124">Security is disabled.</span></span>|  
|<span data-ttu-id="e26e0-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e26e0-125">Message</span></span>|<span data-ttu-id="e26e0-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="e26e0-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e26e0-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e26e0-127">Child Elements</span></span>  
  
|<span data-ttu-id="e26e0-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="e26e0-128">Element</span></span>|<span data-ttu-id="e26e0-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26e0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e26e0-130">\<message></span><span class="sxs-lookup"><span data-stu-id="e26e0-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="e26e0-131">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e26e0-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e26e0-132">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="e26e0-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e26e0-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e26e0-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e26e0-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="e26e0-134">Element</span></span>|<span data-ttu-id="e26e0-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="e26e0-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e26e0-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="e26e0-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e26e0-137">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e26e0-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e26e0-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="e26e0-138">Remarks</span></span>  
 <span data-ttu-id="e26e0-139">Uma dupla associação expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e26e0-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="e26e0-140">O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="e26e0-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26e0-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e26e0-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="e26e0-142">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e26e0-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e26e0-143">Associações</span><span class="sxs-lookup"><span data-stu-id="e26e0-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e26e0-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="e26e0-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e26e0-145">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e26e0-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e26e0-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="e26e0-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
