---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140737"
---
# \<netPeerTcpBinding>
<span data-ttu-id="df5de-101">Define uma associação para mensagens TCP específicas do canal par.</span><span class="sxs-lookup"><span data-stu-id="df5de-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="df5de-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df5de-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df5de-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df5de-103">Attributes and Elements</span></span>  
 <span data-ttu-id="df5de-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="df5de-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df5de-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="df5de-105">Attributes</span></span>  
  
|<span data-ttu-id="df5de-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="df5de-106">Attribute</span></span>|<span data-ttu-id="df5de-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="df5de-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df5de-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="df5de-108">closeTimeout</span></span>|<span data-ttu-id="df5de-109">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento.</span><span class="sxs-lookup"><span data-stu-id="df5de-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="df5de-110">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="df5de-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="df5de-111">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="df5de-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="df5de-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="df5de-112">listenIPAddress</span></span>|<span data-ttu-id="df5de-113">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="df5de-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="df5de-114">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="df5de-114">The default is `null`.</span></span>|  
|<span data-ttu-id="df5de-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="df5de-115">maxBufferPoolSize</span></span>|<span data-ttu-id="df5de-116">Um inteiro que especifica o tamanho máximo do pool de buffers para essa associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="df5de-117">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="df5de-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="df5de-118">Muitas partes de Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="df5de-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="df5de-119">Criar e destruir buffers cada vez que eles são usados é caro, e a coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="df5de-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="df5de-120">Com os pools de buffers, você pode pegar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="df5de-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="df5de-121">Portanto, a sobrecarga na criação e na destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="df5de-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="df5de-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="df5de-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="df5de-123">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, que pode ser recebido em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="df5de-124">O remetente de uma mensagem que excede esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="df5de-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="df5de-125">O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="df5de-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="df5de-126">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="df5de-126">The default is 65536.</span></span>|  
|<span data-ttu-id="df5de-127">name</span><span class="sxs-lookup"><span data-stu-id="df5de-127">name</span></span>|<span data-ttu-id="df5de-128">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="df5de-129">Esse valor deve ser exclusivo porque é usado como uma identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="df5de-130">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="df5de-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="df5de-131">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="df5de-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="df5de-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="df5de-132">openTimeout</span></span>|<span data-ttu-id="df5de-133">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura.</span><span class="sxs-lookup"><span data-stu-id="df5de-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="df5de-134">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="df5de-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="df5de-135">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="df5de-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="df5de-136">porta</span><span class="sxs-lookup"><span data-stu-id="df5de-136">port</span></span>|<span data-ttu-id="df5de-137">Um inteiro que especifica a porta da interface de rede na qual essa associação processará as mensagens TCP do canal de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="df5de-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="df5de-138">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="df5de-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="df5de-139">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="df5de-139">The default is 0.</span></span>|  
|<span data-ttu-id="df5de-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="df5de-140">receiveTimeout</span></span>|<span data-ttu-id="df5de-141">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento.</span><span class="sxs-lookup"><span data-stu-id="df5de-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="df5de-142">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="df5de-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="df5de-143">O padrão é 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="df5de-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="df5de-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="df5de-144">sendTimeout</span></span>|<span data-ttu-id="df5de-145">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio.</span><span class="sxs-lookup"><span data-stu-id="df5de-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="df5de-146">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="df5de-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="df5de-147">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="df5de-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df5de-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df5de-148">Child Elements</span></span>  
  
|<span data-ttu-id="df5de-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="df5de-149">Element</span></span>|<span data-ttu-id="df5de-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="df5de-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="df5de-151">Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="df5de-152">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="df5de-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="df5de-153">Especifica um resolvedor de pares usado por essa associação para resolver uma ID de malha de mesmo nível para os endereços IP do ponto de extremidade de nós na malha do par.</span><span class="sxs-lookup"><span data-stu-id="df5de-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="df5de-154">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="df5de-154">Defines the security settings for the message.</span></span> <span data-ttu-id="df5de-155">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="df5de-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df5de-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df5de-156">Parent Elements</span></span>  
  
|<span data-ttu-id="df5de-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="df5de-157">Element</span></span>|<span data-ttu-id="df5de-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="df5de-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="df5de-159">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="df5de-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df5de-160">Comentários</span><span class="sxs-lookup"><span data-stu-id="df5de-160">Remarks</span></span>  
 <span data-ttu-id="df5de-161">Essa associação fornece suporte para a criação de aplicativos ponto a ponto ou com várias partes usando o transporte de mesmo nível sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="df5de-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="df5de-162">Cada nó de mesmo nível pode hospedar vários canais de pares definidos com esse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="df5de-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df5de-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df5de-163">Example</span></span>  
 <span data-ttu-id="df5de-164">O exemplo a seguir demonstra como usar a associação NetPeerTcpBinding, que fornece comunicação multiparter usando um canal par.</span><span class="sxs-lookup"><span data-stu-id="df5de-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="df5de-165">Para obter um cenário detalhado de como usar essa associação, consulte [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="df5de-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df5de-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="df5de-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="df5de-167">Associações</span><span class="sxs-lookup"><span data-stu-id="df5de-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="df5de-168">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="df5de-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="df5de-169">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="df5de-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="df5de-170">[TCP de mesmo nível de rede](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="df5de-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="df5de-171">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="df5de-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
