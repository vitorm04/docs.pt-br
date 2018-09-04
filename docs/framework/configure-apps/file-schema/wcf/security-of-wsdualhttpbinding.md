---
title: '&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 023e0dd2a89c005928625cf95f3de61af81c7b6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514523"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="5ef40-102">&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5ef40-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="5ef40-103">Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ef40-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="5ef40-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ef40-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ef40-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="5ef40-105">\<bindings></span></span>  
<span data-ttu-id="5ef40-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5ef40-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="5ef40-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5ef40-107">\<binding></span></span>  
<span data-ttu-id="5ef40-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="5ef40-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef40-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ef40-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ef40-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ef40-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ef40-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ef40-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ef40-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ef40-112">Attributes</span></span>  
  
|<span data-ttu-id="5ef40-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ef40-113">Attribute</span></span>|<span data-ttu-id="5ef40-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ef40-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ef40-115">modo</span><span class="sxs-lookup"><span data-stu-id="5ef40-115">mode</span></span>|<span data-ttu-id="5ef40-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="5ef40-116">-   Optional.</span></span> <span data-ttu-id="5ef40-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="5ef40-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5ef40-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="5ef40-118">The default value is `Message`.</span></span> <span data-ttu-id="5ef40-119">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5ef40-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5ef40-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="5ef40-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="5ef40-121">Valor</span><span class="sxs-lookup"><span data-stu-id="5ef40-121">Value</span></span>|<span data-ttu-id="5ef40-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ef40-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ef40-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ef40-123">None</span></span>|<span data-ttu-id="5ef40-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="5ef40-124">Security is disabled.</span></span>|  
|<span data-ttu-id="5ef40-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5ef40-125">Message</span></span>|<span data-ttu-id="5ef40-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="5ef40-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ef40-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ef40-127">Child Elements</span></span>  
  
|<span data-ttu-id="5ef40-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ef40-128">Element</span></span>|<span data-ttu-id="5ef40-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ef40-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ef40-130">\<message></span><span class="sxs-lookup"><span data-stu-id="5ef40-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="5ef40-131">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5ef40-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5ef40-132">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="5ef40-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ef40-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ef40-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5ef40-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ef40-134">Element</span></span>|<span data-ttu-id="5ef40-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ef40-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ef40-136">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5ef40-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5ef40-137">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ef40-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ef40-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ef40-138">Remarks</span></span>  
 <span data-ttu-id="5ef40-139">Uma dupla associação expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="5ef40-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="5ef40-140">O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="5ef40-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef40-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ef40-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="5ef40-142">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5ef40-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5ef40-143">Associações</span><span class="sxs-lookup"><span data-stu-id="5ef40-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5ef40-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5ef40-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5ef40-145">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5ef40-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5ef40-146">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5ef40-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
