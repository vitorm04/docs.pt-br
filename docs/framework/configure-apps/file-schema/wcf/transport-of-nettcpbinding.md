---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915556"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="3e8a3-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="3e8a3-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="3e8a3-103">Define o tipo de requisitos de segurança no nível de mensagem para um ponto de extremidade configurado com o [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="3e8a3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e8a3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e8a3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3e8a3-105">\<bindings></span></span>  
<span data-ttu-id="3e8a3-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="3e8a3-106">\<netTcpBinding></span></span>  
<span data-ttu-id="3e8a3-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="3e8a3-107">\<binding></span></span>  
<span data-ttu-id="3e8a3-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="3e8a3-108">\<security></span></span>  
<span data-ttu-id="3e8a3-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="3e8a3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8a3-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e8a3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e8a3-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e8a3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e8a3-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e8a3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e8a3-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e8a3-113">Attributes</span></span>  
  
|<span data-ttu-id="3e8a3-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e8a3-114">Attribute</span></span>|<span data-ttu-id="3e8a3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e8a3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e8a3-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3e8a3-116">clientCredentialType</span></span>|<span data-ttu-id="3e8a3-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-117">Optional.</span></span> <span data-ttu-id="3e8a3-118">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="3e8a3-119">-O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="3e8a3-120">-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="3e8a3-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3e8a3-121">protectionLevel</span></span>|<span data-ttu-id="3e8a3-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-122">Optional.</span></span> <span data-ttu-id="3e8a3-123">Define a segurança no nível do transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="3e8a3-124">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3e8a3-125">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="3e8a3-126">O valor padrão é `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="3e8a3-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3e8a3-127">sslProtocols</span></span>|<span data-ttu-id="3e8a3-128">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3e8a3-129">O padrão é TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="3e8a3-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="3e8a3-130">policyEnforcement</span></span>|<span data-ttu-id="3e8a3-131">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="3e8a3-132">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="3e8a3-133">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="3e8a3-134">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="3e8a3-135">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3e8a3-136">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="3e8a3-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3e8a3-137">Valor</span><span class="sxs-lookup"><span data-stu-id="3e8a3-137">Value</span></span>|<span data-ttu-id="3e8a3-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e8a3-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e8a3-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e8a3-139">None</span></span>|<span data-ttu-id="3e8a3-140">O cliente é anônimo.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-140">The client is anonymous.</span></span> <span data-ttu-id="3e8a3-141">Isso requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="3e8a3-142">Windows</span><span class="sxs-lookup"><span data-stu-id="3e8a3-142">Windows</span></span>|<span data-ttu-id="3e8a3-143">Especifica a autenticação do Windows do cliente usando a negociação do SP (negociação Kerberos).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="3e8a3-144">Certificate</span><span class="sxs-lookup"><span data-stu-id="3e8a3-144">Certificate</span></span>|<span data-ttu-id="3e8a3-145">O cliente é autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="3e8a3-146">Isso usa a negociação SSL e requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="3e8a3-147">Atributo protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3e8a3-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="3e8a3-148">Valor</span><span class="sxs-lookup"><span data-stu-id="3e8a3-148">Value</span></span>|<span data-ttu-id="3e8a3-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e8a3-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e8a3-150">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e8a3-150">None</span></span>|<span data-ttu-id="3e8a3-151">Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-151">No protection.</span></span>|  
|<span data-ttu-id="3e8a3-152">Assine</span><span class="sxs-lookup"><span data-stu-id="3e8a3-152">Sign</span></span>|<span data-ttu-id="3e8a3-153">As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-153">Messages are signed.</span></span>|  
|<span data-ttu-id="3e8a3-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="3e8a3-154">EncryptAndSign</span></span>|<span data-ttu-id="3e8a3-155">-As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e8a3-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e8a3-156">Child Elements</span></span>  
 <span data-ttu-id="3e8a3-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e8a3-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e8a3-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e8a3-158">Parent Elements</span></span>  
  
|<span data-ttu-id="3e8a3-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e8a3-159">Element</span></span>|<span data-ttu-id="3e8a3-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e8a3-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e8a3-161">\<security></span><span class="sxs-lookup"><span data-stu-id="3e8a3-161">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="3e8a3-162">Especifica os recursos de segurança do [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-162">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e8a3-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e8a3-163">Remarks</span></span>  
 <span data-ttu-id="3e8a3-164">Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e da autenticação mútua.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="3e8a3-165">Se esse modo de segurança for selecionado em uma associação, a pilha de canais será configurada usando um transporte seguro e as mensagens SOAP serão protegidas usando segurança de transporte, como Windows (Negotiate) ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8a3-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e8a3-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="3e8a3-167">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3e8a3-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3e8a3-168">Associações</span><span class="sxs-lookup"><span data-stu-id="3e8a3-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3e8a3-169">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3e8a3-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3e8a3-170">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3e8a3-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3e8a3-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="3e8a3-171">\<binding></span></span>](../../../misc/binding.md)
