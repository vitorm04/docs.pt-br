---
title: '&lt;transporte&gt; de &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: adec2ce082f063f5d3f2cff2c1c428a770aeb76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="25f0e-102">&lt;transporte&gt; de &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="25f0e-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="25f0e-103">Define o tipo de requisitos de segurança de nível de mensagem para um ponto de extremidade configurado com o [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="25f0e-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="25f0e-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="25f0e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="25f0e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="25f0e-105">\<bindings></span></span>  
<span data-ttu-id="25f0e-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="25f0e-106">\<netTcpBinding></span></span>  
<span data-ttu-id="25f0e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="25f0e-107">\<binding></span></span>  
<span data-ttu-id="25f0e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="25f0e-108">\<security></span></span>  
<span data-ttu-id="25f0e-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="25f0e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f0e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25f0e-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25f0e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="25f0e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="25f0e-112">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="25f0e-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25f0e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="25f0e-113">Attributes</span></span>  
  
|<span data-ttu-id="25f0e-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="25f0e-114">Attribute</span></span>|<span data-ttu-id="25f0e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="25f0e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25f0e-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="25f0e-116">clientCredentialType</span></span>|<span data-ttu-id="25f0e-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="25f0e-117">Optional.</span></span> <span data-ttu-id="25f0e-118">Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="25f0e-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="25f0e-119">-O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="25f0e-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="25f0e-120">-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="25f0e-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="25f0e-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="25f0e-121">protectionLevel</span></span>|<span data-ttu-id="25f0e-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="25f0e-122">Optional.</span></span> <span data-ttu-id="25f0e-123">Define a segurança no nível do transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="25f0e-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="25f0e-124">Assinatura de mensagens reduz o risco de um terceiro que viole a mensagem enquanto eles estão sendo transferidos.</span><span class="sxs-lookup"><span data-stu-id="25f0e-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="25f0e-125">A criptografia fornece privacidade de nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="25f0e-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="25f0e-126">O valor padrão é `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="25f0e-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="25f0e-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="25f0e-127">sslProtocols</span></span>|<span data-ttu-id="25f0e-128">Um valor de sinalizador de enumeração de SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="25f0e-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="25f0e-129">O padrão é Tls &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="25f0e-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="25f0e-130">policyenforcement definida como</span><span class="sxs-lookup"><span data-stu-id="25f0e-130">policyEnforcement</span></span>|<span data-ttu-id="25f0e-131">Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> devem ser impostas.</span><span class="sxs-lookup"><span data-stu-id="25f0e-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="25f0e-132">1.  Nunca – a política é aplicada nunca (proteção estendida é desabilitada).</span><span class="sxs-lookup"><span data-stu-id="25f0e-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="25f0e-133">2.  WhenSupported – a política será aplicada somente se o cliente oferece suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="25f0e-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="25f0e-134">3.  Sempre – a política sempre é aplicada.</span><span class="sxs-lookup"><span data-stu-id="25f0e-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="25f0e-135">Os clientes que não oferecem suporte a proteção estendida falhará ao autenticar.</span><span class="sxs-lookup"><span data-stu-id="25f0e-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="25f0e-136">clientCredentialType atributo</span><span class="sxs-lookup"><span data-stu-id="25f0e-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="25f0e-137">Valor</span><span class="sxs-lookup"><span data-stu-id="25f0e-137">Value</span></span>|<span data-ttu-id="25f0e-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="25f0e-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="25f0e-139">Nenhum</span><span class="sxs-lookup"><span data-stu-id="25f0e-139">None</span></span>|<span data-ttu-id="25f0e-140">O cliente é anônimo.</span><span class="sxs-lookup"><span data-stu-id="25f0e-140">The client is anonymous.</span></span> <span data-ttu-id="25f0e-141">Isso requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="25f0e-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="25f0e-142">Windows</span><span class="sxs-lookup"><span data-stu-id="25f0e-142">Windows</span></span>|<span data-ttu-id="25f0e-143">Especifica a autenticação do Windows do cliente usando o SP negociação (Kerberos negociação).</span><span class="sxs-lookup"><span data-stu-id="25f0e-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="25f0e-144">certificado</span><span class="sxs-lookup"><span data-stu-id="25f0e-144">Certificate</span></span>|<span data-ttu-id="25f0e-145">O cliente é autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="25f0e-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="25f0e-146">Isso usa a negociação SSL e requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="25f0e-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="25f0e-147">Atributo de protectionLevel</span><span class="sxs-lookup"><span data-stu-id="25f0e-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="25f0e-148">Valor</span><span class="sxs-lookup"><span data-stu-id="25f0e-148">Value</span></span>|<span data-ttu-id="25f0e-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="25f0e-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="25f0e-150">Nenhum</span><span class="sxs-lookup"><span data-stu-id="25f0e-150">None</span></span>|<span data-ttu-id="25f0e-151">Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="25f0e-151">No protection.</span></span>|  
|<span data-ttu-id="25f0e-152">Logon</span><span class="sxs-lookup"><span data-stu-id="25f0e-152">Sign</span></span>|<span data-ttu-id="25f0e-153">As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="25f0e-153">Messages are signed.</span></span>|  
|<span data-ttu-id="25f0e-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="25f0e-154">EncryptAndSign</span></span>|<span data-ttu-id="25f0e-155">-Mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="25f0e-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25f0e-156">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="25f0e-156">Child Elements</span></span>  
 <span data-ttu-id="25f0e-157">Nenhum</span><span class="sxs-lookup"><span data-stu-id="25f0e-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25f0e-158">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="25f0e-158">Parent Elements</span></span>  
  
|<span data-ttu-id="25f0e-159">Elemento</span><span class="sxs-lookup"><span data-stu-id="25f0e-159">Element</span></span>|<span data-ttu-id="25f0e-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="25f0e-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25f0e-161">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="25f0e-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="25f0e-162">Especifica os recursos de segurança de [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="25f0e-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f0e-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="25f0e-163">Remarks</span></span>  
 <span data-ttu-id="25f0e-164">Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e de autenticação mútua.</span><span class="sxs-lookup"><span data-stu-id="25f0e-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="25f0e-165">Se este modo de segurança é selecionado em uma associação, a pilha de canais é configurada por meio de um transporte seguro e as mensagens SOAP são protegidas usando a segurança de transporte, como SSL ou do Windows (negociação) sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="25f0e-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f0e-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25f0e-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="25f0e-167">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="25f0e-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="25f0e-168">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="25f0e-168">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="25f0e-169">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="25f0e-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="25f0e-170">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="25f0e-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="25f0e-171">\<associação ></span><span class="sxs-lookup"><span data-stu-id="25f0e-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
