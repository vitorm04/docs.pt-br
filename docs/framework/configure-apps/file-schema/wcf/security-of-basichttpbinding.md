---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738707"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="8dd11-102">\<> de segurança do \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8dd11-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="8dd11-103">Define os recursos de segurança do [\<BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dd11-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="8dd11-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8dd11-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8dd11-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="8dd11-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8dd11-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="8dd11-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="8dd11-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**BasicHttpBinding**](basichttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="8dd11-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="8dd11-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="8dd11-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="8dd11-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="8dd11-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd11-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dd11-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dd11-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8dd11-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8dd11-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="8dd11-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dd11-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="8dd11-113">Attributes</span></span>  
  
|<span data-ttu-id="8dd11-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="8dd11-114">Attribute</span></span>|<span data-ttu-id="8dd11-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dd11-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dd11-116">modo</span><span class="sxs-lookup"><span data-stu-id="8dd11-116">mode</span></span>|<span data-ttu-id="8dd11-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8dd11-117">Optional.</span></span> <span data-ttu-id="8dd11-118">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="8dd11-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="8dd11-119">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="8dd11-119">The default is `None`.</span></span> <span data-ttu-id="8dd11-120">Este atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8dd11-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8dd11-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="8dd11-121">mode Attribute</span></span>  
  
|<span data-ttu-id="8dd11-122">Valor</span><span class="sxs-lookup"><span data-stu-id="8dd11-122">Value</span></span>|<span data-ttu-id="8dd11-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dd11-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8dd11-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8dd11-124">None</span></span>|<span data-ttu-id="8dd11-125">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="8dd11-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="8dd11-126">Porta</span><span class="sxs-lookup"><span data-stu-id="8dd11-126">Transport</span></span>|<span data-ttu-id="8dd11-127">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8dd11-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="8dd11-128">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8dd11-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="8dd11-129">O serviço é autenticado para o cliente usando o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="8dd11-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="8dd11-130">O cliente é autenticado usando o ClientCredentialtype fornecido.</span><span class="sxs-lookup"><span data-stu-id="8dd11-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="8dd11-131">Consulte o [> de transporte\<](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dd11-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="8dd11-132">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8dd11-132">Message</span></span>|<span data-ttu-id="8dd11-133">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="8dd11-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="8dd11-134">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="8dd11-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="8dd11-135">Para essa associação, o sistema requer que o certificado do servidor seja fornecido para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="8dd11-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="8dd11-136">O único `ClientCredentialType` válido para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="8dd11-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="8dd11-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8dd11-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="8dd11-138">A integridade, a confidencialidade e a autenticação do servidor são fornecidas pela segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="8dd11-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="8dd11-139">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="8dd11-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="8dd11-140">Esse modo é relevante quando o usuário está Autenticando usando o nome de usuário/senha e há uma implantação HTTP existente para proteger a transferência de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8dd11-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="8dd11-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="8dd11-141">TransportCredentialOnly</span></span>|<span data-ttu-id="8dd11-142">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8dd11-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="8dd11-143">Ele fornece autenticação de cliente baseada em http.</span><span class="sxs-lookup"><span data-stu-id="8dd11-143">It provides http-based client authentication.</span></span> <span data-ttu-id="8dd11-144">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="8dd11-144">This mode should be used with caution.</span></span> <span data-ttu-id="8dd11-145">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="8dd11-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dd11-146">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8dd11-146">Child Elements</span></span>  
  
|<span data-ttu-id="8dd11-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dd11-147">Element</span></span>|<span data-ttu-id="8dd11-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dd11-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dd11-149">> de transporte de \<</span><span class="sxs-lookup"><span data-stu-id="8dd11-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="8dd11-150">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="8dd11-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="8dd11-151">Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="8dd11-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="8dd11-152">\<message ></span><span class="sxs-lookup"><span data-stu-id="8dd11-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="8dd11-153">Define as configurações de segurança da mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="8dd11-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="8dd11-154">Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="8dd11-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dd11-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8dd11-155">Parent Elements</span></span>  
  
|<span data-ttu-id="8dd11-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dd11-156">Element</span></span>|<span data-ttu-id="8dd11-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dd11-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8dd11-158">associação</span><span class="sxs-lookup"><span data-stu-id="8dd11-158">binding</span></span>|<span data-ttu-id="8dd11-159">O elemento Binding do [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dd11-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8dd11-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="8dd11-160">Remarks</span></span>  
 <span data-ttu-id="8dd11-161">Por padrão, a mensagem SOAP não é protegida e o cliente não é autenticado.</span><span class="sxs-lookup"><span data-stu-id="8dd11-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="8dd11-162">Esse elemento permite que você defina configurações de segurança adicionais para o elemento `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8dd11-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd11-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dd11-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="8dd11-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8dd11-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8dd11-165">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="8dd11-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8dd11-166">Associações</span><span class="sxs-lookup"><span data-stu-id="8dd11-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8dd11-167">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8dd11-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8dd11-168">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8dd11-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8dd11-169">\<binding ></span><span class="sxs-lookup"><span data-stu-id="8dd11-169">\<binding></span></span>](bindings.md)
