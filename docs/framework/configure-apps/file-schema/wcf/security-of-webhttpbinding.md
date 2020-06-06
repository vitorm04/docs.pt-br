---
title: <security> de <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738629"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="679cf-102">\<security> de \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="679cf-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="679cf-103">Especifica os requisitos de segurança para um ponto de extremidade configurado com um [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="679cf-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="679cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="679cf-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="679cf-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="679cf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="679cf-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="679cf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="679cf-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="679cf-107">Attributes</span></span>  
  
|<span data-ttu-id="679cf-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="679cf-108">Attribute</span></span>|<span data-ttu-id="679cf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="679cf-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="679cf-110">mode</span><span class="sxs-lookup"><span data-stu-id="679cf-110">mode</span></span>|<span data-ttu-id="679cf-111">Especifica se a segurança em nível de transporte ou nenhuma segurança é usada por um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="679cf-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="679cf-112">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="679cf-112">The default is `None`.</span></span> <span data-ttu-id="679cf-113">Esse atributo é do tipo <xref:System.ServiceModel.WebHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="679cf-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="679cf-114">Atributo Mode</span><span class="sxs-lookup"><span data-stu-id="679cf-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="679cf-115">Valor</span><span class="sxs-lookup"><span data-stu-id="679cf-115">Value</span></span>|<span data-ttu-id="679cf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="679cf-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="679cf-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="679cf-117">None</span></span>|<span data-ttu-id="679cf-118">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="679cf-118">Security is disabled.</span></span>|  
|<span data-ttu-id="679cf-119">Transport</span><span class="sxs-lookup"><span data-stu-id="679cf-119">Transport</span></span>|<span data-ttu-id="679cf-120">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="679cf-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="679cf-121">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="679cf-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="679cf-122">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="679cf-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="679cf-123">A autenticação do cliente é controlada por meio do `ClientCredentialType` atributo do [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="679cf-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="679cf-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="679cf-124">TransportCredentialOnly</span></span>|<span data-ttu-id="679cf-125">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="679cf-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="679cf-126">Ele fornece autenticação de cliente baseada em HTTP.</span><span class="sxs-lookup"><span data-stu-id="679cf-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="679cf-127">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="679cf-127">This mode should be used with caution.</span></span> <span data-ttu-id="679cf-128">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="679cf-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="679cf-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="679cf-129">Child Elements</span></span>  
  
|<span data-ttu-id="679cf-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="679cf-130">Element</span></span>|<span data-ttu-id="679cf-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="679cf-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="679cf-132">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="679cf-132">Defines the transport security settings.</span></span> <span data-ttu-id="679cf-133">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="679cf-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="679cf-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="679cf-134">Parent Elements</span></span>  
  
|<span data-ttu-id="679cf-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="679cf-135">Element</span></span>|<span data-ttu-id="679cf-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="679cf-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="679cf-137">Um elemento de associação que é usado para configurar pontos de extremidade para serviços da Web Windows Communication Foundation (WCF) que respondem a solicitações HTTP em vez de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="679cf-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="679cf-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="679cf-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="679cf-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="679cf-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="679cf-140">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="679cf-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="679cf-141">Associações</span><span class="sxs-lookup"><span data-stu-id="679cf-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="679cf-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="679cf-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="679cf-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="679cf-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="679cf-144">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="679cf-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
