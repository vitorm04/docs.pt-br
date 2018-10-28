---
title: '&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 77e7191b345e59116874e70aaa28241223938eea
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193728"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="20abe-102">&lt;segurança&gt; de &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="20abe-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="20abe-103">Define os recursos de segurança de [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="20abe-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="20abe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="20abe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="20abe-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="20abe-105">\<bindings></span></span>  
<span data-ttu-id="20abe-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="20abe-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="20abe-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="20abe-107">\<binding></span></span>  
<span data-ttu-id="20abe-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="20abe-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20abe-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20abe-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20abe-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20abe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20abe-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20abe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20abe-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="20abe-112">Attributes</span></span>  
  
|<span data-ttu-id="20abe-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="20abe-113">Attribute</span></span>|<span data-ttu-id="20abe-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="20abe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20abe-115">modo</span><span class="sxs-lookup"><span data-stu-id="20abe-115">mode</span></span>|<span data-ttu-id="20abe-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="20abe-116">-   Optional.</span></span> <span data-ttu-id="20abe-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="20abe-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="20abe-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="20abe-118">The default value is `Message`.</span></span> <span data-ttu-id="20abe-119">Esse atributo é do tipo <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="20abe-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="20abe-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="20abe-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="20abe-121">Valor</span><span class="sxs-lookup"><span data-stu-id="20abe-121">Value</span></span>|<span data-ttu-id="20abe-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="20abe-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20abe-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="20abe-123">None</span></span>|<span data-ttu-id="20abe-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="20abe-124">Security is disabled.</span></span>|  
|<span data-ttu-id="20abe-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="20abe-125">Message</span></span>|<span data-ttu-id="20abe-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="20abe-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20abe-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20abe-127">Child Elements</span></span>  
  
|<span data-ttu-id="20abe-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="20abe-128">Element</span></span>|<span data-ttu-id="20abe-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="20abe-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20abe-130">\<message></span><span class="sxs-lookup"><span data-stu-id="20abe-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="20abe-131">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="20abe-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="20abe-132">Esse elemento é do tipo <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="20abe-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20abe-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20abe-133">Parent Elements</span></span>  
  
|<span data-ttu-id="20abe-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="20abe-134">Element</span></span>|<span data-ttu-id="20abe-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="20abe-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20abe-136">\<associação ></span><span class="sxs-lookup"><span data-stu-id="20abe-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="20abe-137">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="20abe-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20abe-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="20abe-138">Remarks</span></span>  
 <span data-ttu-id="20abe-139">Uma dupla associação expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="20abe-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="20abe-140">O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="20abe-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20abe-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20abe-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="20abe-142">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="20abe-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="20abe-143">Associações</span><span class="sxs-lookup"><span data-stu-id="20abe-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="20abe-144">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="20abe-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="20abe-145">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="20abe-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="20abe-146">\<associação ></span><span class="sxs-lookup"><span data-stu-id="20abe-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
