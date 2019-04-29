---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: b6375a64ea157df01f903901e0414a2989287aee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670450"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="151ed-102">\<segurança > de \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="151ed-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="151ed-103">Especifica os requisitos de segurança para um ponto de extremidade configurado com um [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="151ed-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="151ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="151ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="151ed-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="151ed-105">\<bindings></span></span>  
<span data-ttu-id="151ed-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="151ed-106">\<webHttpBinding></span></span>  
<span data-ttu-id="151ed-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="151ed-107">\<binding></span></span>  
<span data-ttu-id="151ed-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="151ed-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="151ed-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="151ed-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="151ed-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="151ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="151ed-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="151ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="151ed-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="151ed-112">Attributes</span></span>  
  
|<span data-ttu-id="151ed-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="151ed-113">Attribute</span></span>|<span data-ttu-id="151ed-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="151ed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="151ed-115">modo</span><span class="sxs-lookup"><span data-stu-id="151ed-115">mode</span></span>|<span data-ttu-id="151ed-116">Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="151ed-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="151ed-117">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="151ed-117">The default is `None`.</span></span> <span data-ttu-id="151ed-118">Esse atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="151ed-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="151ed-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="151ed-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="151ed-120">Valor</span><span class="sxs-lookup"><span data-stu-id="151ed-120">Value</span></span>|<span data-ttu-id="151ed-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="151ed-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="151ed-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="151ed-122">None</span></span>|<span data-ttu-id="151ed-123">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="151ed-123">Security is disabled.</span></span>|  
|<span data-ttu-id="151ed-124">Transporte</span><span class="sxs-lookup"><span data-stu-id="151ed-124">Transport</span></span>|<span data-ttu-id="151ed-125">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="151ed-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="151ed-126">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="151ed-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="151ed-127">A mensagem é totalmente protegida usando o HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="151ed-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="151ed-128">A autenticação do cliente é controlada por meio de `ClientCredentialType` atributo do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="151ed-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="151ed-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="151ed-129">TransportCredentialOnly</span></span>|<span data-ttu-id="151ed-130">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="151ed-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="151ed-131">Ele fornece autenticação de cliente com base em HTTP.</span><span class="sxs-lookup"><span data-stu-id="151ed-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="151ed-132">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="151ed-132">This mode should be used with caution.</span></span> <span data-ttu-id="151ed-133">Ele deve ser usado em ambientes onde a segurança do transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="151ed-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="151ed-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="151ed-134">Child Elements</span></span>  
  
|<span data-ttu-id="151ed-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="151ed-135">Element</span></span>|<span data-ttu-id="151ed-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="151ed-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="151ed-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="151ed-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="151ed-138">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="151ed-138">Defines the transport security settings.</span></span> <span data-ttu-id="151ed-139">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="151ed-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="151ed-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="151ed-140">Parent Elements</span></span>  
  
|<span data-ttu-id="151ed-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="151ed-141">Element</span></span>|<span data-ttu-id="151ed-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="151ed-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="151ed-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="151ed-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="151ed-144">Um elemento de associação que é usado para configurar pontos de extremidade do Windows Communication Foundation (WCF) dos serviços da Web que respondem a solicitações HTTP em vez de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="151ed-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="151ed-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="151ed-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="151ed-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="151ed-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="151ed-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="151ed-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="151ed-148">Associações</span><span class="sxs-lookup"><span data-stu-id="151ed-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="151ed-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="151ed-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="151ed-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="151ed-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="151ed-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="151ed-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="151ed-152">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="151ed-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
