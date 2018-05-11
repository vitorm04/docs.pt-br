---
title: '&lt;segurança&gt; de &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd65b488a2d3f18f2e19191f143243204c4303d4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="8e6dd-102">&lt;segurança&gt; de &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8e6dd-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="8e6dd-103">Especifica os requisitos de segurança para um ponto de extremidade configurado com um [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8e6dd-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="8e6dd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e6dd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e6dd-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="8e6dd-105">\<bindings></span></span>  
<span data-ttu-id="8e6dd-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8e6dd-106">\<webHttpBinding></span></span>  
<span data-ttu-id="8e6dd-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8e6dd-107">\<binding></span></span>  
<span data-ttu-id="8e6dd-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="8e6dd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e6dd-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e6dd-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e6dd-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e6dd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8e6dd-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e6dd-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e6dd-112">Attributes</span></span>  
  
|<span data-ttu-id="8e6dd-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e6dd-113">Attribute</span></span>|<span data-ttu-id="8e6dd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e6dd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e6dd-115">modo</span><span class="sxs-lookup"><span data-stu-id="8e6dd-115">mode</span></span>|<span data-ttu-id="8e6dd-116">Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="8e6dd-117">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-117">The default is `None`.</span></span> <span data-ttu-id="8e6dd-118">Esse atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8e6dd-119">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="8e6dd-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="8e6dd-120">Valor</span><span class="sxs-lookup"><span data-stu-id="8e6dd-120">Value</span></span>|<span data-ttu-id="8e6dd-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e6dd-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e6dd-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8e6dd-122">None</span></span>|<span data-ttu-id="8e6dd-123">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-123">Security is disabled.</span></span>|  
|<span data-ttu-id="8e6dd-124">Transporte</span><span class="sxs-lookup"><span data-stu-id="8e6dd-124">Transport</span></span>|<span data-ttu-id="8e6dd-125">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="8e6dd-126">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="8e6dd-127">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="8e6dd-128">A autenticação do cliente é controlada por meio de `ClientCredentialType` atributo do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8e6dd-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="8e6dd-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="8e6dd-129">TransportCredentialOnly</span></span>|<span data-ttu-id="8e6dd-130">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="8e6dd-131">Ele fornece autenticação de cliente com base em HTTP.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="8e6dd-132">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-132">This mode should be used with caution.</span></span> <span data-ttu-id="8e6dd-133">Ele deve ser usado em ambientes onde a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e6dd-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e6dd-134">Child Elements</span></span>  
  
|<span data-ttu-id="8e6dd-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e6dd-135">Element</span></span>|<span data-ttu-id="8e6dd-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e6dd-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e6dd-137">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="8e6dd-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="8e6dd-138">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-138">Defines the transport security settings.</span></span> <span data-ttu-id="8e6dd-139">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="8e6dd-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e6dd-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e6dd-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8e6dd-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e6dd-141">Element</span></span>|<span data-ttu-id="8e6dd-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e6dd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e6dd-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8e6dd-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="8e6dd-144">Um elemento de associação que é usado para configurar pontos de extremidade para que responda a solicitações HTTP em vez de mensagens SOAP de serviços Web do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8e6dd-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e6dd-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e6dd-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="8e6dd-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8e6dd-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8e6dd-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="8e6dd-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="8e6dd-148">Associações</span><span class="sxs-lookup"><span data-stu-id="8e6dd-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8e6dd-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8e6dd-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8e6dd-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8e6dd-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8e6dd-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8e6dd-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="8e6dd-152">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="8e6dd-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
