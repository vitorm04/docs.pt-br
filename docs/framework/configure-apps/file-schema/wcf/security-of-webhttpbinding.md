---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738629"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="ce45b-102">\<> de segurança do \<WebHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ce45b-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="ce45b-103">Especifica os requisitos de segurança para um ponto de extremidade configurado com um [\<Webhttpbinding >](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ce45b-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="ce45b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce45b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce45b-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ce45b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce45b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="ce45b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ce45b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WebHttpBinding**](webhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ce45b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="ce45b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="ce45b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ce45b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="ce45b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce45b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce45b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce45b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce45b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ce45b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce45b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce45b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce45b-113">Attributes</span></span>  
  
|<span data-ttu-id="ce45b-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce45b-114">Attribute</span></span>|<span data-ttu-id="ce45b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce45b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce45b-116">modo</span><span class="sxs-lookup"><span data-stu-id="ce45b-116">mode</span></span>|<span data-ttu-id="ce45b-117">Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ce45b-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="ce45b-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="ce45b-118">The default is `None`.</span></span> <span data-ttu-id="ce45b-119">Este atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ce45b-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ce45b-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="ce45b-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="ce45b-121">Valor</span><span class="sxs-lookup"><span data-stu-id="ce45b-121">Value</span></span>|<span data-ttu-id="ce45b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce45b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce45b-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ce45b-123">None</span></span>|<span data-ttu-id="ce45b-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ce45b-124">Security is disabled.</span></span>|  
|<span data-ttu-id="ce45b-125">Porta</span><span class="sxs-lookup"><span data-stu-id="ce45b-125">Transport</span></span>|<span data-ttu-id="ce45b-126">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ce45b-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="ce45b-127">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="ce45b-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="ce45b-128">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="ce45b-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="ce45b-129">A autenticação do cliente é controlada por meio do atributo `ClientCredentialType` do [> de transporte\<](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ce45b-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="ce45b-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="ce45b-130">TransportCredentialOnly</span></span>|<span data-ttu-id="ce45b-131">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ce45b-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="ce45b-132">Ele fornece autenticação de cliente baseada em HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce45b-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="ce45b-133">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="ce45b-133">This mode should be used with caution.</span></span> <span data-ttu-id="ce45b-134">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="ce45b-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce45b-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce45b-135">Child Elements</span></span>  
  
|<span data-ttu-id="ce45b-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce45b-136">Element</span></span>|<span data-ttu-id="ce45b-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce45b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce45b-138">> de transporte de \<</span><span class="sxs-lookup"><span data-stu-id="ce45b-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="ce45b-139">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="ce45b-139">Defines the transport security settings.</span></span> <span data-ttu-id="ce45b-140">Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ce45b-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce45b-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce45b-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ce45b-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce45b-142">Element</span></span>|<span data-ttu-id="ce45b-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce45b-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce45b-144">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ce45b-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="ce45b-145">Um elemento de associação que é usado para configurar pontos de extremidade para serviços da Web Windows Communication Foundation (WCF) que respondem a solicitações HTTP em vez de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="ce45b-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce45b-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce45b-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="ce45b-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ce45b-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ce45b-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="ce45b-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ce45b-149">Associações</span><span class="sxs-lookup"><span data-stu-id="ce45b-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce45b-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ce45b-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ce45b-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ce45b-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ce45b-152">\<binding ></span><span class="sxs-lookup"><span data-stu-id="ce45b-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="ce45b-153">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="ce45b-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
