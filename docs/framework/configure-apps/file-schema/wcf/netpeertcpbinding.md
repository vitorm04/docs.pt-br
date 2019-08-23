---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: fc1930889235805d68d88aa8080f8f9fb3235612
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933035"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="dafbe-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="dafbe-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="dafbe-102">Define uma associação para mensagens TCP específicas do canal par.</span><span class="sxs-lookup"><span data-stu-id="dafbe-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="dafbe-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dafbe-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dafbe-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="dafbe-104">\<bindings></span></span>  
<span data-ttu-id="dafbe-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="dafbe-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dafbe-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dafbe-106">Syntax</span></span>  
  
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
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dafbe-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dafbe-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dafbe-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="dafbe-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dafbe-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dafbe-109">Attributes</span></span>  
  
|<span data-ttu-id="dafbe-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="dafbe-110">Attribute</span></span>|<span data-ttu-id="dafbe-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="dafbe-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dafbe-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="dafbe-112">closeTimeout</span></span>|<span data-ttu-id="dafbe-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="dafbe-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dafbe-114">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dafbe-115">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dafbe-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dafbe-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="dafbe-116">listenIPAddress</span></span>|<span data-ttu-id="dafbe-117">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="dafbe-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="dafbe-118">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="dafbe-118">The default is `null`.</span></span>|  
|<span data-ttu-id="dafbe-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="dafbe-119">maxBufferPoolSize</span></span>|<span data-ttu-id="dafbe-120">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="dafbe-121">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="dafbe-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="dafbe-122">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="dafbe-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="dafbe-123">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="dafbe-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="dafbe-124">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="dafbe-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="dafbe-125">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="dafbe-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="dafbe-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="dafbe-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="dafbe-127">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="dafbe-128">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="dafbe-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="dafbe-129">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="dafbe-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="dafbe-130">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="dafbe-130">The default is 65536.</span></span>|  
|<span data-ttu-id="dafbe-131">name</span><span class="sxs-lookup"><span data-stu-id="dafbe-131">name</span></span>|<span data-ttu-id="dafbe-132">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dafbe-133">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dafbe-134">A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dafbe-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dafbe-135">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dafbe-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="dafbe-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="dafbe-136">openTimeout</span></span>|<span data-ttu-id="dafbe-137">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="dafbe-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dafbe-138">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dafbe-139">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dafbe-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dafbe-140">porta</span><span class="sxs-lookup"><span data-stu-id="dafbe-140">port</span></span>|<span data-ttu-id="dafbe-141">Um inteiro que especifica a porta da interface de rede na qual essa associação processará as mensagens TCP do canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="dafbe-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="dafbe-142">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="dafbe-143">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="dafbe-143">The default is 0.</span></span>|  
|<span data-ttu-id="dafbe-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="dafbe-144">receiveTimeout</span></span>|<span data-ttu-id="dafbe-145">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="dafbe-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dafbe-146">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dafbe-147">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dafbe-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="dafbe-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="dafbe-148">sendTimeout</span></span>|<span data-ttu-id="dafbe-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="dafbe-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dafbe-150">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dafbe-151">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dafbe-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dafbe-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dafbe-152">Child Elements</span></span>  
  
|<span data-ttu-id="dafbe-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="dafbe-153">Element</span></span>|<span data-ttu-id="dafbe-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="dafbe-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dafbe-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dafbe-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="dafbe-156">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dafbe-157">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="dafbe-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="dafbe-158">\<resolver></span></span>](resolver.md)|<span data-ttu-id="dafbe-159">Especifica um resolvedor de pares usado por essa associação para resolver uma ID de malha de mesmo nível para os endereços IP do ponto de extremidade de nós na malha do par.</span><span class="sxs-lookup"><span data-stu-id="dafbe-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="dafbe-160">\<security></span><span class="sxs-lookup"><span data-stu-id="dafbe-160">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="dafbe-161">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="dafbe-161">Defines the security settings for the message.</span></span> <span data-ttu-id="dafbe-162">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="dafbe-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dafbe-163">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dafbe-163">Parent Elements</span></span>  
  
|<span data-ttu-id="dafbe-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="dafbe-164">Element</span></span>|<span data-ttu-id="dafbe-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="dafbe-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dafbe-166">\<bindings></span><span class="sxs-lookup"><span data-stu-id="dafbe-166">\<bindings></span></span>](bindings.md)|<span data-ttu-id="dafbe-167">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="dafbe-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dafbe-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="dafbe-168">Remarks</span></span>  
 <span data-ttu-id="dafbe-169">Essa associação fornece suporte para a criação de aplicativos ponto a ponto ou com várias partes usando o transporte de mesmo nível sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="dafbe-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="dafbe-170">Cada nó de mesmo nível pode hospedar vários canais de pares definidos com esse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="dafbe-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dafbe-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dafbe-171">Example</span></span>  
 <span data-ttu-id="dafbe-172">O exemplo a seguir demonstra como usar a associação NetPeerTcpBinding, que fornece comunicação multiparter usando um canal par.</span><span class="sxs-lookup"><span data-stu-id="dafbe-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="dafbe-173">Para obter um cenário detalhado de como usar essa associação, consulte [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="dafbe-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
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
  
## <a name="see-also"></a><span data-ttu-id="dafbe-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dafbe-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="dafbe-175">Associações</span><span class="sxs-lookup"><span data-stu-id="dafbe-175">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dafbe-176">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="dafbe-176">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dafbe-177">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="dafbe-177">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dafbe-178">\<binding></span><span class="sxs-lookup"><span data-stu-id="dafbe-178">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="dafbe-179">[TCP de mesmo nível de rede](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="dafbe-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="dafbe-180">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="dafbe-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
