---
title: "&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6680d01b068a6ac1c4f9abcda69779c9cd0786a0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="b7e9d-102">&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b7e9d-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="b7e9d-103">Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9d-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="b7e9d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7e9d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7e9d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b7e9d-105">\<bindings></span></span>  
<span data-ttu-id="b7e9d-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b7e9d-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="b7e9d-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="b7e9d-107">\<binding></span></span>  
<span data-ttu-id="b7e9d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="b7e9d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e9d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7e9d-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7e9d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7e9d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7e9d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7e9d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7e9d-112">Attributes</span></span>  
  
|<span data-ttu-id="b7e9d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7e9d-113">Attribute</span></span>|<span data-ttu-id="b7e9d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7e9d-115">modo</span><span class="sxs-lookup"><span data-stu-id="b7e9d-115">mode</span></span>|<span data-ttu-id="b7e9d-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-116">-   Optional.</span></span> <span data-ttu-id="b7e9d-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b7e9d-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-118">The default value is `Message`.</span></span> <span data-ttu-id="b7e9d-119">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b7e9d-120">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="b7e9d-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="b7e9d-121">Valor</span><span class="sxs-lookup"><span data-stu-id="b7e9d-121">Value</span></span>|<span data-ttu-id="b7e9d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b7e9d-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b7e9d-123">None</span></span>|<span data-ttu-id="b7e9d-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-124">Security is disabled.</span></span>|  
|<span data-ttu-id="b7e9d-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b7e9d-125">Message</span></span>|<span data-ttu-id="b7e9d-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7e9d-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7e9d-127">Child Elements</span></span>  
  
|<span data-ttu-id="b7e9d-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7e9d-128">Element</span></span>|<span data-ttu-id="b7e9d-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e9d-130">\<message></span><span class="sxs-lookup"><span data-stu-id="b7e9d-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="b7e9d-131">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b7e9d-132">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7e9d-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7e9d-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b7e9d-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7e9d-134">Element</span></span>|<span data-ttu-id="b7e9d-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7e9d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7e9d-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="b7e9d-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b7e9d-137">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b7e9d-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7e9d-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7e9d-138">Remarks</span></span>  
 <span data-ttu-id="b7e9d-139">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="b7e9d-140">O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="b7e9d-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e9d-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7e9d-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="b7e9d-142">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b7e9d-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b7e9d-143">Associações</span><span class="sxs-lookup"><span data-stu-id="b7e9d-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b7e9d-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b7e9d-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b7e9d-145">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b7e9d-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b7e9d-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="b7e9d-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
