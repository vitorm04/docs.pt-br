---
title: <security> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 04e7e94f47be37dc9c4cbf404a269b9784281d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936617"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="ca05c-102">\<> de segurança \<de NetTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="ca05c-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="ca05c-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="ca05c-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="ca05c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ca05c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca05c-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ca05c-105">\<bindings></span></span>  
<span data-ttu-id="ca05c-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="ca05c-106">\<netTcpBinding></span></span>  
<span data-ttu-id="ca05c-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="ca05c-107">\<binding></span></span>  
<span data-ttu-id="ca05c-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="ca05c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca05c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca05c-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca05c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca05c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ca05c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca05c-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca05c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca05c-112">Attributes</span></span>  
  
|<span data-ttu-id="ca05c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca05c-113">Attribute</span></span>|<span data-ttu-id="ca05c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca05c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca05c-115">modo</span><span class="sxs-lookup"><span data-stu-id="ca05c-115">mode</span></span>|<span data-ttu-id="ca05c-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ca05c-116">Optional.</span></span> <span data-ttu-id="ca05c-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="ca05c-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ca05c-118">Os valores válidos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="ca05c-118">Valid values are shown below.</span></span> <span data-ttu-id="ca05c-119">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="ca05c-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="ca05c-120">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ca05c-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ca05c-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="ca05c-121">mode Attribute</span></span>  
  
|<span data-ttu-id="ca05c-122">Valor</span><span class="sxs-lookup"><span data-stu-id="ca05c-122">Value</span></span>|<span data-ttu-id="ca05c-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca05c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ca05c-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ca05c-124">None</span></span>|<span data-ttu-id="ca05c-125">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ca05c-125">Security is disabled.</span></span>|  
|<span data-ttu-id="ca05c-126">Porta</span><span class="sxs-lookup"><span data-stu-id="ca05c-126">Transport</span></span>|<span data-ttu-id="ca05c-127">A segurança de transporte é fornecida usando TLS sobre TCP ou SPNego.</span><span class="sxs-lookup"><span data-stu-id="ca05c-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="ca05c-128">O serviço pode precisar ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="ca05c-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="ca05c-129">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="ca05c-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="ca05c-130">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ca05c-130">Message</span></span>|<span data-ttu-id="ca05c-131">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="ca05c-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="ca05c-132">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="ca05c-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="ca05c-133">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca05c-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="ca05c-134">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="ca05c-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="ca05c-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ca05c-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="ca05c-136">A segurança de transporte é associada à segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca05c-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="ca05c-137">A segurança de transporte é fornecida pelo TLS sobre TCP ou SPNego e garante a integridade, a confidencialidade e a autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="ca05c-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="ca05c-138">A segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="ca05c-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="ca05c-139">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="ca05c-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca05c-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca05c-140">Child Elements</span></span>  
  
|<span data-ttu-id="ca05c-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca05c-141">Element</span></span>|<span data-ttu-id="ca05c-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca05c-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca05c-143">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="ca05c-143">\<transport></span></span>](transport-of-nettcpbinding.md)|<span data-ttu-id="ca05c-144">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="ca05c-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="ca05c-145">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ca05c-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="ca05c-146">\<message></span><span class="sxs-lookup"><span data-stu-id="ca05c-146">\<message></span></span>](message-element-of-nettcpbinding.md)|<span data-ttu-id="ca05c-147">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca05c-147">Defines the security settings for the message.</span></span> <span data-ttu-id="ca05c-148">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="ca05c-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca05c-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca05c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="ca05c-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca05c-150">Element</span></span>|<span data-ttu-id="ca05c-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca05c-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca05c-152">associação</span><span class="sxs-lookup"><span data-stu-id="ca05c-152">binding</span></span>|<span data-ttu-id="ca05c-153">O elemento Binding da [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca05c-153">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca05c-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca05c-154">Remarks</span></span>  
 <span data-ttu-id="ca05c-155">Cada uma das associações padrão fornece parâmetros para controlar os requisitos de segurança de transferência.</span><span class="sxs-lookup"><span data-stu-id="ca05c-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="ca05c-156">Esses parâmetros normalmente incluem o modo de segurança que especificou se a segurança no nível de mensagem ou de transporte é usada e a escolha do tipo de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="ca05c-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="ca05c-157">Com base na escolha das opções que esses parâmetros apresentam, uma pilha de canais é construída com a segurança apropriada.</span><span class="sxs-lookup"><span data-stu-id="ca05c-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="ca05c-158">As associações fornecidas pelo sistema fornecidas pelo Windows Communication Foundation (WCF) são um conjunto projetado para atender a alguns dos requisitos de cenário mais comuns.</span><span class="sxs-lookup"><span data-stu-id="ca05c-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="ca05c-159">Cada uma dessas associações permite a especificação de requisitos de segurança para alguns cenários específicos de destino.</span><span class="sxs-lookup"><span data-stu-id="ca05c-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="ca05c-160">Este elemento de configuração fornece as especificações de `netTcpBinding`segurança para o.</span><span class="sxs-lookup"><span data-stu-id="ca05c-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="ca05c-161">Essa é uma associação segura, confiável e otimizada adequada para comunicação entre computadores.</span><span class="sxs-lookup"><span data-stu-id="ca05c-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="ca05c-162">Por padrão, ele gera uma pilha de comunicação de tempo de execução que dá suporte a TCP para entrega de mensagens e segurança do Windows para segurança e autenticação de mensagens, WS-ReliableMessaging para confiabilidade e codificação de mensagens binárias.</span><span class="sxs-lookup"><span data-stu-id="ca05c-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca05c-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca05c-163">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="ca05c-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ca05c-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ca05c-165">Associações</span><span class="sxs-lookup"><span data-stu-id="ca05c-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ca05c-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ca05c-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ca05c-167">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ca05c-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ca05c-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="ca05c-168">\<binding></span></span>](../../../misc/binding.md)
