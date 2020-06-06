---
title: <security> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736377"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="2e1b6-102">\<security> de \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2e1b6-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="2e1b6-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="2e1b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e1b6-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e1b6-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2e1b6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2e1b6-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2e1b6-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e1b6-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="2e1b6-107">Attributes</span></span>  
  
|<span data-ttu-id="2e1b6-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="2e1b6-108">Attribute</span></span>|<span data-ttu-id="2e1b6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e1b6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e1b6-110">mode</span><span class="sxs-lookup"><span data-stu-id="2e1b6-110">mode</span></span>|<span data-ttu-id="2e1b6-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-111">Optional.</span></span> <span data-ttu-id="2e1b6-112">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="2e1b6-113">Os valores válidos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-113">Valid values are shown below.</span></span> <span data-ttu-id="2e1b6-114">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="2e1b6-115">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="2e1b6-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2e1b6-116">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="2e1b6-116">mode Attribute</span></span>  
  
|<span data-ttu-id="2e1b6-117">Valor</span><span class="sxs-lookup"><span data-stu-id="2e1b6-117">Value</span></span>|<span data-ttu-id="2e1b6-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e1b6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e1b6-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2e1b6-119">None</span></span>|<span data-ttu-id="2e1b6-120">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-120">Security is disabled.</span></span>|  
|<span data-ttu-id="2e1b6-121">Transport</span><span class="sxs-lookup"><span data-stu-id="2e1b6-121">Transport</span></span>|<span data-ttu-id="2e1b6-122">A segurança de transporte é fornecida usando TLS sobre TCP ou SPNego.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="2e1b6-123">O serviço pode precisar ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="2e1b6-124">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="2e1b6-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="2e1b6-125">Message</span></span>|<span data-ttu-id="2e1b6-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="2e1b6-127">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="2e1b6-128">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="2e1b6-129">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="2e1b6-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2e1b6-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="2e1b6-131">A segurança de transporte é associada à segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="2e1b6-132">A segurança de transporte é fornecida pelo TLS sobre TCP ou SPNego e garante a integridade, a confidencialidade e a autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="2e1b6-133">A segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="2e1b6-134">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e1b6-135">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2e1b6-135">Child Elements</span></span>  
  
|<span data-ttu-id="2e1b6-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e1b6-136">Element</span></span>|<span data-ttu-id="2e1b6-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e1b6-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="2e1b6-138">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="2e1b6-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="2e1b6-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="2e1b6-140">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-140">Defines the security settings for the message.</span></span> <span data-ttu-id="2e1b6-141">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> .</span><span class="sxs-lookup"><span data-stu-id="2e1b6-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e1b6-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2e1b6-142">Parent Elements</span></span>  
  
|<span data-ttu-id="2e1b6-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="2e1b6-143">Element</span></span>|<span data-ttu-id="2e1b6-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e1b6-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e1b6-145">associação</span><span class="sxs-lookup"><span data-stu-id="2e1b6-145">binding</span></span>|<span data-ttu-id="2e1b6-146">O elemento Binding do [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2e1b6-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e1b6-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e1b6-147">Remarks</span></span>  
 <span data-ttu-id="2e1b6-148">Cada uma das associações padrão fornece parâmetros para controlar os requisitos de segurança de transferência.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="2e1b6-149">Esses parâmetros normalmente incluem o modo de segurança que especificou se a segurança no nível de mensagem ou de transporte é usada e a escolha do tipo de credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="2e1b6-150">Com base na escolha das opções que esses parâmetros apresentam, uma pilha de canais é construída com a segurança apropriada.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="2e1b6-151">As associações fornecidas pelo sistema fornecidas pelo Windows Communication Foundation (WCF) são um conjunto projetado para atender a alguns dos requisitos de cenário mais comuns.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="2e1b6-152">Cada uma dessas associações permite a especificação de requisitos de segurança para alguns cenários específicos de destino.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="2e1b6-153">Este elemento de configuração fornece as especificações de segurança para o `netTcpBinding` .</span><span class="sxs-lookup"><span data-stu-id="2e1b6-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="2e1b6-154">Essa é uma associação segura, confiável e otimizada adequada para comunicação entre computadores.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="2e1b6-155">Por padrão, ele gera uma pilha de comunicação de tempo de execução que dá suporte a TCP para entrega de mensagens e segurança do Windows para segurança e autenticação de mensagens, WS-ReliableMessaging para confiabilidade e codificação de mensagens binárias.</span><span class="sxs-lookup"><span data-stu-id="2e1b6-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e1b6-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e1b6-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="2e1b6-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2e1b6-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2e1b6-158">Associações</span><span class="sxs-lookup"><span data-stu-id="2e1b6-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2e1b6-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="2e1b6-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2e1b6-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2e1b6-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
