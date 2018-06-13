---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 1b2e5030c55f8568bc418b507878ddbf202b39fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750876"
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="49eaa-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="49eaa-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="49eaa-103">Define uma associação de ponto a ponto canal mensagens TCP específicas.</span><span class="sxs-lookup"><span data-stu-id="49eaa-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="49eaa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49eaa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="49eaa-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="49eaa-105">\<bindings></span></span>  
<span data-ttu-id="49eaa-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="49eaa-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49eaa-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49eaa-107">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding name="string"  
         closeTimeout="TimeSpan"  
         openTimeout="TimeSpan"   
         receiveTimeout="TimeSpan"  
         sendTimeout="TimeSpan"  
         listenIPAddress="String"  
          maxBufferPoolSize="integer"  
         maxReceiveMessageSize="Integer"   
         port="Integer"  
         <security mode="None/Transport/Message/TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49eaa-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="49eaa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="49eaa-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="49eaa-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49eaa-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="49eaa-110">Attributes</span></span>  
  
|<span data-ttu-id="49eaa-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="49eaa-111">Attribute</span></span>|<span data-ttu-id="49eaa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="49eaa-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49eaa-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="49eaa-113">closeTimeout</span></span>|<span data-ttu-id="49eaa-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="49eaa-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="49eaa-115">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49eaa-116">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49eaa-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49eaa-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="49eaa-117">listenIPAddress</span></span>|<span data-ttu-id="49eaa-118">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="49eaa-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="49eaa-119">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="49eaa-119">The default is `null`.</span></span>|  
|<span data-ttu-id="49eaa-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="49eaa-120">maxBufferPoolSize</span></span>|<span data-ttu-id="49eaa-121">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="49eaa-122">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="49eaa-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="49eaa-123">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="49eaa-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="49eaa-124">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara.</span><span class="sxs-lookup"><span data-stu-id="49eaa-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="49eaa-125">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="49eaa-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="49eaa-126">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="49eaa-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="49eaa-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="49eaa-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="49eaa-128">Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="49eaa-129">O remetente de uma mensagem exceder esse limite recebem uma falha SOAP.</span><span class="sxs-lookup"><span data-stu-id="49eaa-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="49eaa-130">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="49eaa-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="49eaa-131">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="49eaa-131">The default is 65536.</span></span>|  
|<span data-ttu-id="49eaa-132">name</span><span class="sxs-lookup"><span data-stu-id="49eaa-132">name</span></span>|<span data-ttu-id="49eaa-133">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="49eaa-134">Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="49eaa-135">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="49eaa-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="49eaa-136">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="49eaa-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="49eaa-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="49eaa-137">openTimeout</span></span>|<span data-ttu-id="49eaa-138">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="49eaa-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="49eaa-139">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49eaa-140">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49eaa-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="49eaa-141">porta</span><span class="sxs-lookup"><span data-stu-id="49eaa-141">port</span></span>|<span data-ttu-id="49eaa-142">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="49eaa-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="49eaa-143">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="49eaa-144">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="49eaa-144">The default is 0.</span></span>|  
|<span data-ttu-id="49eaa-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="49eaa-145">receiveTimeout</span></span>|<span data-ttu-id="49eaa-146">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="49eaa-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="49eaa-147">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49eaa-148">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="49eaa-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="49eaa-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="49eaa-149">sendTimeout</span></span>|<span data-ttu-id="49eaa-150">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="49eaa-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="49eaa-151">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="49eaa-152">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="49eaa-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49eaa-153">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="49eaa-153">Child Elements</span></span>  
  
|<span data-ttu-id="49eaa-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="49eaa-154">Element</span></span>|<span data-ttu-id="49eaa-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="49eaa-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49eaa-156">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="49eaa-156">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="49eaa-157">Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="49eaa-158">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="49eaa-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="49eaa-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="49eaa-160">Especifica a ID de um resolvedor peer usado por esta associação para resolver um par de malha para os endereços IP do ponto de extremidade de nós dentro da malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="49eaa-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="49eaa-161">\<security></span><span class="sxs-lookup"><span data-stu-id="49eaa-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="49eaa-162">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="49eaa-162">Defines the security settings for the message.</span></span> <span data-ttu-id="49eaa-163">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="49eaa-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49eaa-164">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="49eaa-164">Parent Elements</span></span>  
  
|<span data-ttu-id="49eaa-165">Elemento</span><span class="sxs-lookup"><span data-stu-id="49eaa-165">Element</span></span>|<span data-ttu-id="49eaa-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="49eaa-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49eaa-167">\<associações ></span><span class="sxs-lookup"><span data-stu-id="49eaa-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="49eaa-168">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="49eaa-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49eaa-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="49eaa-169">Remarks</span></span>  
 <span data-ttu-id="49eaa-170">Essa associação oferece suporte para a criação de aplicativos ponto a ponto ou com vários participantes usando o transporte de par sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="49eaa-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="49eaa-171">Cada nó par pode hospedar vários canais par definidos com esse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="49eaa-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49eaa-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49eaa-172">Example</span></span>  
 <span data-ttu-id="49eaa-173">O exemplo a seguir demonstra como usar a associação NetPeerTcpBinding, que permite a comunicação com vários participantes usando um canal par.</span><span class="sxs-lookup"><span data-stu-id="49eaa-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="49eaa-174">Para um cenário detalhado de como usar essa associação, consulte [Net TCP de mesmo nível](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span><span class="sxs-lookup"><span data-stu-id="49eaa-174">For a detailed scenario of using this binding, see [Net Peer TCP](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<netPeerBinding>  
    <binding   
         closeTimeout="00:00:10"  
         openTimeout="00:00:20"   
         receiveTimeout="00:00:30"  
         sendTimeout="00:00:40"  
         maxBufferSize="1001"  
         maxConnections="123"   
         maxReceiveMessageSize="1000">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00"  
            enabled="true" />  
        <security mode="TransportWithMessageCredential">  
            <message clientCredentialType="CardSpace" />  
        </security>  
    </binding>  
</netPeerBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="49eaa-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49eaa-175">See Also</span></span>  
 <xref:System.ServiceModel.NetPeerTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>  
 [<span data-ttu-id="49eaa-176">Associações</span><span class="sxs-lookup"><span data-stu-id="49eaa-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="49eaa-177">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="49eaa-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="49eaa-178">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="49eaa-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="49eaa-179">\<associação ></span><span class="sxs-lookup"><span data-stu-id="49eaa-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="49eaa-180">Rede ponto a ponto TCP</span><span class="sxs-lookup"><span data-stu-id="49eaa-180">Net Peer TCP</span></span>](http://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)  
 [<span data-ttu-id="49eaa-181">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="49eaa-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
