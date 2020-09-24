---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8f752373c51992c51b747f5f4dc4a63910a387c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162186"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="980ef-102">\<transport> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="980ef-102">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="980ef-103">Define o tipo de requisitos de segurança no nível de mensagem para um ponto de extremidade configurado com o [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="980ef-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="980ef-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="980ef-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="980ef-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="980ef-105">Attributes and Elements</span></span>  

 <span data-ttu-id="980ef-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="980ef-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="980ef-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="980ef-107">Attributes</span></span>  
  
|<span data-ttu-id="980ef-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="980ef-108">Attribute</span></span>|<span data-ttu-id="980ef-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="980ef-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="980ef-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="980ef-110">clientCredentialType</span></span>|<span data-ttu-id="980ef-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="980ef-111">Optional.</span></span> <span data-ttu-id="980ef-112">Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="980ef-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="980ef-113">-O valor padrão é `Windows` .</span><span class="sxs-lookup"><span data-stu-id="980ef-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="980ef-114">-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="980ef-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="980ef-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="980ef-115">protectionLevel</span></span>|<span data-ttu-id="980ef-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="980ef-116">Optional.</span></span> <span data-ttu-id="980ef-117">Define a segurança no nível do transporte TCP.</span><span class="sxs-lookup"><span data-stu-id="980ef-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="980ef-118">A assinatura de mensagens reduz o risco de violação de terceiros com a mensagem enquanto ela está sendo transferida.</span><span class="sxs-lookup"><span data-stu-id="980ef-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="980ef-119">A criptografia fornece privacidade no nível de dados durante o transporte.</span><span class="sxs-lookup"><span data-stu-id="980ef-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="980ef-120">O valor padrão é `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="980ef-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="980ef-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="980ef-121">sslProtocols</span></span>|<span data-ttu-id="980ef-122">Um valor de sinalizador de enumeração SslProtocols que especifica quais SslProtocols têm suporte.</span><span class="sxs-lookup"><span data-stu-id="980ef-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="980ef-123">O padrão é TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="980ef-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="980ef-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="980ef-124">policyEnforcement</span></span>|<span data-ttu-id="980ef-125">Essa enumeração especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposto.</span><span class="sxs-lookup"><span data-stu-id="980ef-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="980ef-126">1. nunca – a política nunca é imposta (a proteção estendida está desabilitada).</span><span class="sxs-lookup"><span data-stu-id="980ef-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="980ef-127">2. WhenSupported – a política será imposta somente se o cliente oferecer suporte à proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="980ef-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="980ef-128">3. sempre – a política é sempre imposta.</span><span class="sxs-lookup"><span data-stu-id="980ef-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="980ef-129">Os clientes que não dão suporte à proteção estendida não serão autenticados.</span><span class="sxs-lookup"><span data-stu-id="980ef-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="980ef-130">Atributo clientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="980ef-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="980ef-131">Valor</span><span class="sxs-lookup"><span data-stu-id="980ef-131">Value</span></span>|<span data-ttu-id="980ef-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="980ef-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="980ef-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="980ef-133">None</span></span>|<span data-ttu-id="980ef-134">O cliente é anônimo.</span><span class="sxs-lookup"><span data-stu-id="980ef-134">The client is anonymous.</span></span> <span data-ttu-id="980ef-135">Isso requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="980ef-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="980ef-136">Windows</span><span class="sxs-lookup"><span data-stu-id="980ef-136">Windows</span></span>|<span data-ttu-id="980ef-137">Especifica a autenticação do Windows do cliente usando a negociação do SP (negociação Kerberos).</span><span class="sxs-lookup"><span data-stu-id="980ef-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="980ef-138">Certificado</span><span class="sxs-lookup"><span data-stu-id="980ef-138">Certificate</span></span>|<span data-ttu-id="980ef-139">O cliente é autenticado usando um certificado.</span><span class="sxs-lookup"><span data-stu-id="980ef-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="980ef-140">Isso usa a negociação SSL e requer um certificado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="980ef-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="980ef-141">Atributo protectionLevel</span><span class="sxs-lookup"><span data-stu-id="980ef-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="980ef-142">Valor</span><span class="sxs-lookup"><span data-stu-id="980ef-142">Value</span></span>|<span data-ttu-id="980ef-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="980ef-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="980ef-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="980ef-144">None</span></span>|<span data-ttu-id="980ef-145">Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="980ef-145">No protection.</span></span>|  
|<span data-ttu-id="980ef-146">Assinar</span><span class="sxs-lookup"><span data-stu-id="980ef-146">Sign</span></span>|<span data-ttu-id="980ef-147">As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="980ef-147">Messages are signed.</span></span>|  
|<span data-ttu-id="980ef-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="980ef-148">EncryptAndSign</span></span>|<span data-ttu-id="980ef-149">-As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="980ef-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="980ef-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="980ef-150">Child Elements</span></span>  

 <span data-ttu-id="980ef-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="980ef-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="980ef-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="980ef-152">Parent Elements</span></span>  
  
|<span data-ttu-id="980ef-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="980ef-153">Element</span></span>|<span data-ttu-id="980ef-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="980ef-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="980ef-155">Especifica os recursos de segurança do [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="980ef-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="980ef-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="980ef-156">Remarks</span></span>  

 <span data-ttu-id="980ef-157">Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e da autenticação mútua.</span><span class="sxs-lookup"><span data-stu-id="980ef-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="980ef-158">Se esse modo de segurança for selecionado em uma associação, a pilha de canais será configurada usando um transporte seguro e as mensagens SOAP serão protegidas usando segurança de transporte, como Windows (Negotiate) ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="980ef-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980ef-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="980ef-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="980ef-160">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="980ef-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="980ef-161">Associações</span><span class="sxs-lookup"><span data-stu-id="980ef-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="980ef-162">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="980ef-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="980ef-163">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="980ef-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
