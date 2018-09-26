---
title: '&lt;segurança&gt; de &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
ms.openlocfilehash: 045fb60f6ae0fb54dce7fd9bc8c634caee5fddcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205312"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="64b16-102">&lt;segurança&gt; de &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="64b16-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="64b16-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="64b16-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="64b16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="64b16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="64b16-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="64b16-105">\<bindings></span></span>  
<span data-ttu-id="64b16-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="64b16-106">\<netTcpBinding></span></span>  
<span data-ttu-id="64b16-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="64b16-107">\<binding></span></span>  
<span data-ttu-id="64b16-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="64b16-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b16-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64b16-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64b16-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="64b16-110">Attributes and Elements</span></span>  
 <span data-ttu-id="64b16-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="64b16-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64b16-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="64b16-112">Attributes</span></span>  
  
|<span data-ttu-id="64b16-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="64b16-113">Attribute</span></span>|<span data-ttu-id="64b16-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b16-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64b16-115">modo</span><span class="sxs-lookup"><span data-stu-id="64b16-115">mode</span></span>|<span data-ttu-id="64b16-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="64b16-116">Optional.</span></span> <span data-ttu-id="64b16-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="64b16-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="64b16-118">Os valores válidos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="64b16-118">Valid values are shown below.</span></span> <span data-ttu-id="64b16-119">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="64b16-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="64b16-120">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="64b16-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="64b16-121">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="64b16-121">mode Attribute</span></span>  
  
|<span data-ttu-id="64b16-122">Valor</span><span class="sxs-lookup"><span data-stu-id="64b16-122">Value</span></span>|<span data-ttu-id="64b16-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b16-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64b16-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="64b16-124">None</span></span>|<span data-ttu-id="64b16-125">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="64b16-125">Security is disabled.</span></span>|  
|<span data-ttu-id="64b16-126">Transporte</span><span class="sxs-lookup"><span data-stu-id="64b16-126">Transport</span></span>|<span data-ttu-id="64b16-127">Segurança de transporte é fornecida com o uso de TLS via TCP ou SPNego.</span><span class="sxs-lookup"><span data-stu-id="64b16-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="64b16-128">O serviço precisará ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="64b16-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="64b16-129">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="64b16-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="64b16-130">Mensagem</span><span class="sxs-lookup"><span data-stu-id="64b16-130">Message</span></span>|<span data-ttu-id="64b16-131">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="64b16-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="64b16-132">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="64b16-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="64b16-133">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e o nível de proteção a ser aplicado ao corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="64b16-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="64b16-134">Autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="64b16-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="64b16-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="64b16-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="64b16-136">Segurança de transporte está acoplada com segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="64b16-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="64b16-137">Segurança de transporte é fornecida pelo TLS via TCP ou SPNego e garante a integridade, confidencialidade e autenticação de servidor.</span><span class="sxs-lookup"><span data-stu-id="64b16-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="64b16-138">Segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="64b16-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="64b16-139">Por padrão, autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="64b16-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64b16-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="64b16-140">Child Elements</span></span>  
  
|<span data-ttu-id="64b16-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="64b16-141">Element</span></span>|<span data-ttu-id="64b16-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b16-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64b16-143">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="64b16-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="64b16-144">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="64b16-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="64b16-145">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="64b16-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="64b16-146">\<message></span><span class="sxs-lookup"><span data-stu-id="64b16-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="64b16-147">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="64b16-147">Defines the security settings for the message.</span></span> <span data-ttu-id="64b16-148">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="64b16-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64b16-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="64b16-149">Parent Elements</span></span>  
  
|<span data-ttu-id="64b16-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="64b16-150">Element</span></span>|<span data-ttu-id="64b16-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="64b16-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64b16-152">associação</span><span class="sxs-lookup"><span data-stu-id="64b16-152">binding</span></span>|<span data-ttu-id="64b16-153">O elemento de associação do [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="64b16-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64b16-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="64b16-154">Remarks</span></span>  
 <span data-ttu-id="64b16-155">Cada uma das associações padrão fornece parâmetros para controlar os requisitos de segurança de transferência.</span><span class="sxs-lookup"><span data-stu-id="64b16-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="64b16-156">Normalmente, esses parâmetros incluem o modo de segurança especificado se a segurança de nível de mensagem ou o nível de transporte é usada e a escolha do tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="64b16-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="64b16-157">Com base na escolha das opções esses parâmetros estiver presentes, uma pilha de canais é construído com a segurança apropriada.</span><span class="sxs-lookup"><span data-stu-id="64b16-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="64b16-158">As associações fornecidas pelo sistema fornecidas pelo Windows Communication Foundation (WCF) são um conjunto projetado para atender a alguns dos requisitos do cenário mais comuns.</span><span class="sxs-lookup"><span data-stu-id="64b16-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="64b16-159">Cada uma dessas vinculações permite a especificação dos requisitos de segurança para alguns cenários de destino específicos.</span><span class="sxs-lookup"><span data-stu-id="64b16-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="64b16-160">Este elemento de configuração fornece as especificações de segurança para `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="64b16-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="64b16-161">Isso é uma associação segura, confiável e otimizada adequada para comunicação entre computadores.</span><span class="sxs-lookup"><span data-stu-id="64b16-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="64b16-162">Por padrão, ele gera uma pilha de comunicação em tempo de execução que dão suporte a TCP para entrega de mensagens e segurança do Windows para autenticação, WS-ReliableMessaging para confiabilidade e a codificação de mensagem binária e de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="64b16-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b16-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64b16-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="64b16-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="64b16-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="64b16-165">Associações</span><span class="sxs-lookup"><span data-stu-id="64b16-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="64b16-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="64b16-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="64b16-167">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="64b16-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="64b16-168">\<associação ></span><span class="sxs-lookup"><span data-stu-id="64b16-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
