---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 2f0bc97e10fcd72f2f33cc20730320cbbfc42dd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399759"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="6e16c-102">\<> de segurança \<de WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6e16c-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="6e16c-103">Especifica os requisitos de segurança para um ponto de extremidade configurado com um [ \<WebHttpBinding >](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6e16c-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="6e16c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e16c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e16c-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6e16c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6e16c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6e16c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6e16c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> WebHttpBinding**](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6e16c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="6e16c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="6e16c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6e16c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="6e16c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e16c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e16c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e16c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e16c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6e16c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6e16c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e16c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e16c-113">Attributes</span></span>  
  
|<span data-ttu-id="6e16c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e16c-114">Attribute</span></span>|<span data-ttu-id="6e16c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e16c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e16c-116">modo</span><span class="sxs-lookup"><span data-stu-id="6e16c-116">mode</span></span>|<span data-ttu-id="6e16c-117">Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6e16c-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="6e16c-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="6e16c-118">The default is `None`.</span></span> <span data-ttu-id="6e16c-119">Esse atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6e16c-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6e16c-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="6e16c-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6e16c-121">Valor</span><span class="sxs-lookup"><span data-stu-id="6e16c-121">Value</span></span>|<span data-ttu-id="6e16c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e16c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6e16c-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6e16c-123">None</span></span>|<span data-ttu-id="6e16c-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6e16c-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6e16c-125">Porta</span><span class="sxs-lookup"><span data-stu-id="6e16c-125">Transport</span></span>|<span data-ttu-id="6e16c-126">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6e16c-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="6e16c-127">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="6e16c-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="6e16c-128">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="6e16c-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6e16c-129">A autenticação do cliente é controlada por `ClientCredentialType` meio do atributo [ \<do > de transporte](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6e16c-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="6e16c-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6e16c-130">TransportCredentialOnly</span></span>|<span data-ttu-id="6e16c-131">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="6e16c-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6e16c-132">Ele fornece autenticação de cliente baseada em HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e16c-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="6e16c-133">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="6e16c-133">This mode should be used with caution.</span></span> <span data-ttu-id="6e16c-134">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="6e16c-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e16c-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e16c-135">Child Elements</span></span>  
  
|<span data-ttu-id="6e16c-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e16c-136">Element</span></span>|<span data-ttu-id="6e16c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e16c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e16c-138">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="6e16c-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="6e16c-139">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="6e16c-139">Defines the transport security settings.</span></span> <span data-ttu-id="6e16c-140">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="6e16c-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e16c-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e16c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="6e16c-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e16c-142">Element</span></span>|<span data-ttu-id="6e16c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e16c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e16c-144">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6e16c-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="6e16c-145">Um elemento de associação que é usado para configurar pontos de extremidade para serviços da Web Windows Communication Foundation (WCF) que respondem a solicitações HTTP em vez de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="6e16c-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e16c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e16c-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="6e16c-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6e16c-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6e16c-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="6e16c-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6e16c-149">Associações</span><span class="sxs-lookup"><span data-stu-id="6e16c-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6e16c-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="6e16c-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6e16c-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6e16c-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6e16c-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="6e16c-152">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="6e16c-153">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="6e16c-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
