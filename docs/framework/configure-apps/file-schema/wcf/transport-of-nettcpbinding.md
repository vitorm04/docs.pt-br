---
title: <transport> De <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: de1f87d8074bbf3d85f6092a4ac316f5fd20052c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355578"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="074f8-102">\<transport> of \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="074f8-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="074f8-103">Define o tipo de requisitos de segurança de nível de mensagem para um ponto de extremidade configurado com o [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="074f8-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="074f8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="074f8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="074f8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="074f8-105">\<bindings></span></span>  
<span data-ttu-id="074f8-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="074f8-106">\<netTcpBinding></span></span>  
<span data-ttu-id="074f8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="074f8-107">\<binding></span></span>  
<span data-ttu-id="074f8-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="074f8-108">\<security></span></span>  
<span data-ttu-id="074f8-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="074f8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074f8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="074f8-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="074f8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="074f8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="074f8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="074f8-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="074f8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="074f8-113">Attributes</span></span>  
  
|<span data-ttu-id="074f8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="074f8-114">Attribute</span></span>|<span data-ttu-id="074f8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="074f8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="074f8-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="074f8-116">clientCredentialType</span></span>|<span data-ttu-id="074f8-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="074f8-117">Optional.</span></span> <span data-ttu-id="074f8-118">Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="074f8-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="074f8-119">-O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="074f8-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="074f8-120">-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="074f8-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="074f8-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="074f8-121">protectionLevel</span></span>|<span data-ttu-id="074f8-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="074f8-122">Optional.</span></span> <span data-ttu-id="074f8-123">Define a segurança no nível de transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="074f8-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="074f8-124">Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="074f8-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="074f8-125">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="074f8-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="074f8-126">O valor padrão é `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="074f8-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="074f8-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="074f8-127">sslProtocols</span></span>|<span data-ttu-id="074f8-128">Um valor de sinalizador de enum de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="074f8-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="074f8-129">O padrão é Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="074f8-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="074f8-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="074f8-130">policyEnforcement</span></span>|<span data-ttu-id="074f8-131">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.</span><span class="sxs-lookup"><span data-stu-id="074f8-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="074f8-132">1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="074f8-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="074f8-133">2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="074f8-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="074f8-134">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="074f8-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="074f8-135">Os clientes que não dão suporte a proteção estendida falharão ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="074f8-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="074f8-136">clientCredentialType de atributo</span><span class="sxs-lookup"><span data-stu-id="074f8-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="074f8-137">Valor</span><span class="sxs-lookup"><span data-stu-id="074f8-137">Value</span></span>|<span data-ttu-id="074f8-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="074f8-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="074f8-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="074f8-139">None</span></span>|<span data-ttu-id="074f8-140">O cliente é anônimo.</span><span class="sxs-lookup"><span data-stu-id="074f8-140">The client is anonymous.</span></span> <span data-ttu-id="074f8-141">Isso requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="074f8-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="074f8-142">Windows</span><span class="sxs-lookup"><span data-stu-id="074f8-142">Windows</span></span>|<span data-ttu-id="074f8-143">Especifica a autenticação do Windows do cliente usando a negociação do SP (negociação de Kerberos).</span><span class="sxs-lookup"><span data-stu-id="074f8-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="074f8-144">Certificado</span><span class="sxs-lookup"><span data-stu-id="074f8-144">Certificate</span></span>|<span data-ttu-id="074f8-145">O cliente é autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="074f8-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="074f8-146">Isso usa a negociação SSL e requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="074f8-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="074f8-147">Atributo de protectionLevel</span><span class="sxs-lookup"><span data-stu-id="074f8-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="074f8-148">Valor</span><span class="sxs-lookup"><span data-stu-id="074f8-148">Value</span></span>|<span data-ttu-id="074f8-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="074f8-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="074f8-150">Nenhum</span><span class="sxs-lookup"><span data-stu-id="074f8-150">None</span></span>|<span data-ttu-id="074f8-151">Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="074f8-151">No protection.</span></span>|  
|<span data-ttu-id="074f8-152">logon</span><span class="sxs-lookup"><span data-stu-id="074f8-152">Sign</span></span>|<span data-ttu-id="074f8-153">As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="074f8-153">Messages are signed.</span></span>|  
|<span data-ttu-id="074f8-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="074f8-154">EncryptAndSign</span></span>|<span data-ttu-id="074f8-155">-As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="074f8-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="074f8-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="074f8-156">Child Elements</span></span>  
 <span data-ttu-id="074f8-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="074f8-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="074f8-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="074f8-158">Parent Elements</span></span>  
  
|<span data-ttu-id="074f8-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="074f8-159">Element</span></span>|<span data-ttu-id="074f8-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="074f8-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="074f8-161">\<security></span><span class="sxs-lookup"><span data-stu-id="074f8-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="074f8-162">Especifica os recursos de segurança de [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="074f8-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="074f8-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="074f8-163">Remarks</span></span>  
 <span data-ttu-id="074f8-164">Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e para autenticação mútua.</span><span class="sxs-lookup"><span data-stu-id="074f8-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="074f8-165">Se este modo de segurança é selecionado em uma associação, a pilha de canais é configurada usando um transporte seguro e as mensagens SOAP são protegidas usando a segurança de transporte, como Windows (negociação) ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="074f8-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074f8-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="074f8-166">See also</span></span>
- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="074f8-167">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="074f8-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="074f8-168">Associações</span><span class="sxs-lookup"><span data-stu-id="074f8-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="074f8-169">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="074f8-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="074f8-170">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="074f8-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="074f8-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="074f8-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
