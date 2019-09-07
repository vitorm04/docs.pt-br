---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 41f11be9b4ae8f7a7535c9766965de8575cff784
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399310"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="7a834-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="7a834-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="7a834-103">Define o tipo de requisitos de segurança no nível de mensagem para um ponto de extremidade configurado com o [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7a834-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="7a834-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a834-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a834-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a834-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a834-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7a834-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7a834-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> netTcpbinding**](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7a834-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="7a834-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="7a834-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7a834-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7a834-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="7a834-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="7a834-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a834-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a834-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a834-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7a834-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7a834-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7a834-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a834-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a834-114">Attributes</span></span>  
  
|<span data-ttu-id="7a834-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7a834-115">Attribute</span></span>|<span data-ttu-id="7a834-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a834-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a834-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="7a834-117">clientCredentialType</span></span>|<span data-ttu-id="7a834-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7a834-118">Optional.</span></span> <span data-ttu-id="7a834-119">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="7a834-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="7a834-120">-O valor padrão é `Windows`.</span><span class="sxs-lookup"><span data-stu-id="7a834-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="7a834-121">-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7a834-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="7a834-122">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="7a834-122">protectionLevel</span></span>|<span data-ttu-id="7a834-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7a834-123">Optional.</span></span> <span data-ttu-id="7a834-124">Define a segurança no nível do transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="7a834-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="7a834-125">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="7a834-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="7a834-126">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="7a834-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="7a834-127">O valor padrão é `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="7a834-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="7a834-128">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="7a834-128">sslProtocols</span></span>|<span data-ttu-id="7a834-129">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="7a834-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="7a834-130">O padrão é TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="7a834-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="7a834-131">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="7a834-131">policyEnforcement</span></span>|<span data-ttu-id="7a834-132">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="7a834-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="7a834-133">1.  Nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="7a834-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="7a834-134">2.  WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="7a834-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="7a834-135">3.  Sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="7a834-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="7a834-136">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="7a834-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="7a834-137">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="7a834-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7a834-138">Valor</span><span class="sxs-lookup"><span data-stu-id="7a834-138">Value</span></span>|<span data-ttu-id="7a834-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a834-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a834-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7a834-140">None</span></span>|<span data-ttu-id="7a834-141">O cliente é anônimo.</span><span class="sxs-lookup"><span data-stu-id="7a834-141">The client is anonymous.</span></span> <span data-ttu-id="7a834-142">Isso requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7a834-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="7a834-143">Windows</span><span class="sxs-lookup"><span data-stu-id="7a834-143">Windows</span></span>|<span data-ttu-id="7a834-144">Especifica a autenticação do Windows do cliente usando a negociação do SP (negociação Kerberos).</span><span class="sxs-lookup"><span data-stu-id="7a834-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="7a834-145">Certificate</span><span class="sxs-lookup"><span data-stu-id="7a834-145">Certificate</span></span>|<span data-ttu-id="7a834-146">O cliente é autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="7a834-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="7a834-147">Isso usa a negociação SSL e requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7a834-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="7a834-148">Atributo protectionLevel</span><span class="sxs-lookup"><span data-stu-id="7a834-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="7a834-149">Valor</span><span class="sxs-lookup"><span data-stu-id="7a834-149">Value</span></span>|<span data-ttu-id="7a834-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a834-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a834-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7a834-151">None</span></span>|<span data-ttu-id="7a834-152">Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="7a834-152">No protection.</span></span>|  
|<span data-ttu-id="7a834-153">Assine</span><span class="sxs-lookup"><span data-stu-id="7a834-153">Sign</span></span>|<span data-ttu-id="7a834-154">As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="7a834-154">Messages are signed.</span></span>|  
|<span data-ttu-id="7a834-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="7a834-155">EncryptAndSign</span></span>|<span data-ttu-id="7a834-156">-As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="7a834-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a834-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7a834-157">Child Elements</span></span>  
 <span data-ttu-id="7a834-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7a834-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a834-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7a834-159">Parent Elements</span></span>  
  
|<span data-ttu-id="7a834-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a834-160">Element</span></span>|<span data-ttu-id="7a834-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a834-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a834-162">\<security></span><span class="sxs-lookup"><span data-stu-id="7a834-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="7a834-163">Especifica os recursos de segurança do [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7a834-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a834-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a834-164">Remarks</span></span>  
 <span data-ttu-id="7a834-165">Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e da autenticação mútua.</span><span class="sxs-lookup"><span data-stu-id="7a834-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="7a834-166">Se esse modo de segurança for selecionado em uma associação, a pilha de canais será configurada usando um transporte seguro e as mensagens SOAP serão protegidas usando segurança de transporte, como Windows (Negotiate) ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="7a834-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a834-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a834-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="7a834-168">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7a834-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7a834-169">Associações</span><span class="sxs-lookup"><span data-stu-id="7a834-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a834-170">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="7a834-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7a834-171">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7a834-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7a834-172">\<binding></span><span class="sxs-lookup"><span data-stu-id="7a834-172">\<binding></span></span>](../../../misc/binding.md)
