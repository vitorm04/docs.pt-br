---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: b35e2f365e82291d3f8b827850fdebfe8fa2237d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780361"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="c395a-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="c395a-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="c395a-102">Define uma associação de canal mensagens TCP específicas par.</span><span class="sxs-lookup"><span data-stu-id="c395a-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="c395a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c395a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c395a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c395a-104">\<bindings></span></span>  
<span data-ttu-id="c395a-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="c395a-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c395a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c395a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c395a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c395a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c395a-108">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="c395a-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c395a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c395a-109">Attributes</span></span>  
  
|<span data-ttu-id="c395a-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="c395a-110">Attribute</span></span>|<span data-ttu-id="c395a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c395a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c395a-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c395a-112">closeTimeout</span></span>|<span data-ttu-id="c395a-113">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="c395a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c395a-114">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c395a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c395a-115">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="c395a-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c395a-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="c395a-116">listenIPAddress</span></span>|<span data-ttu-id="c395a-117">Uma cadeia de caracteres que especifica um endereço IP no qual o nó par escutará mensagens TCP.</span><span class="sxs-lookup"><span data-stu-id="c395a-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="c395a-118">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="c395a-118">The default is `null`.</span></span>|  
|<span data-ttu-id="c395a-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c395a-119">maxBufferPoolSize</span></span>|<span data-ttu-id="c395a-120">Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c395a-121">O padrão é 524.288 bytes (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="c395a-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c395a-122">Muitas partes do Windows Communication Foundation (WCF) usam buffers.</span><span class="sxs-lookup"><span data-stu-id="c395a-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c395a-123">Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é dispendiosa.</span><span class="sxs-lookup"><span data-stu-id="c395a-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c395a-124">Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar.</span><span class="sxs-lookup"><span data-stu-id="c395a-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c395a-125">Portanto, a sobrecarga na criação e destruição de buffers é evitada.</span><span class="sxs-lookup"><span data-stu-id="c395a-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="c395a-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c395a-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="c395a-127">Um inteiro positivo que especifica o tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, que podem ser recebidos em um canal configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c395a-128">O remetente de uma mensagem exceder esse limite receberá uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="c395a-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c395a-129">O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c395a-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c395a-130">O padrão é 65536.</span><span class="sxs-lookup"><span data-stu-id="c395a-130">The default is 65536.</span></span>|  
|<span data-ttu-id="c395a-131">name</span><span class="sxs-lookup"><span data-stu-id="c395a-131">name</span></span>|<span data-ttu-id="c395a-132">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c395a-133">Esse valor deve ser exclusivo porque ele é usado como identificação para a associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c395a-134">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="c395a-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c395a-135">Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c395a-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="c395a-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c395a-136">openTimeout</span></span>|<span data-ttu-id="c395a-137">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="c395a-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c395a-138">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c395a-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c395a-139">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="c395a-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="c395a-140">porta</span><span class="sxs-lookup"><span data-stu-id="c395a-140">port</span></span>|<span data-ttu-id="c395a-141">Um inteiro que especifica a porta de interface de rede no qual esta associação irá processar mensagens do TCP de canal par.</span><span class="sxs-lookup"><span data-stu-id="c395a-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="c395a-142">Esse valor deve estar entre <xref:System.Net.IPEndPoint.MinPort> e <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="c395a-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="c395a-143">O padrão é 0.</span><span class="sxs-lookup"><span data-stu-id="c395a-143">The default is 0.</span></span>|  
|<span data-ttu-id="c395a-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c395a-144">receiveTimeout</span></span>|<span data-ttu-id="c395a-145">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="c395a-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c395a-146">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c395a-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c395a-147">O padrão é 10:00:00.</span><span class="sxs-lookup"><span data-stu-id="c395a-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="c395a-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c395a-148">sendTimeout</span></span>|<span data-ttu-id="c395a-149">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="c395a-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c395a-150">Esse valor deve ser maior que ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="c395a-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c395a-151">O padrão é 01:00:00.</span><span class="sxs-lookup"><span data-stu-id="c395a-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c395a-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c395a-152">Child Elements</span></span>  
  
|<span data-ttu-id="c395a-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="c395a-153">Element</span></span>|<span data-ttu-id="c395a-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="c395a-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c395a-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c395a-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c395a-156">Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c395a-157">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="c395a-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="c395a-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="c395a-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="c395a-159">Especifica um resolvedor de par usado por essa associação para resolver um par de ID de malha para os endereços IP do ponto de extremidade de nós dentro da malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="c395a-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="c395a-160">\<security></span><span class="sxs-lookup"><span data-stu-id="c395a-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="c395a-161">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c395a-161">Defines the security settings for the message.</span></span> <span data-ttu-id="c395a-162">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c395a-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c395a-163">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c395a-163">Parent Elements</span></span>  
  
|<span data-ttu-id="c395a-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="c395a-164">Element</span></span>|<span data-ttu-id="c395a-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="c395a-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c395a-166">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c395a-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="c395a-167">Esse elemento contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c395a-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c395a-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="c395a-168">Remarks</span></span>  
 <span data-ttu-id="c395a-169">Esta associação oferece suporte para a criação de aplicativos ponto a ponto ou com vários participantes usando o transporte de par sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="c395a-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="c395a-170">Cada nó par pode hospedar vários canais pares definidos com esse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="c395a-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c395a-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c395a-171">Example</span></span>  
 <span data-ttu-id="c395a-172">O exemplo a seguir demonstra como usar a ligação de NetPeerTcpBinding, que fornece comunicação entre vários participantes usando um canal par.</span><span class="sxs-lookup"><span data-stu-id="c395a-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="c395a-173">Para um cenário detalhado de como usar essa associação, consulte [Net TCP de mesmo nível](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c395a-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c395a-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c395a-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="c395a-175">Associações</span><span class="sxs-lookup"><span data-stu-id="c395a-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c395a-176">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c395a-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c395a-177">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c395a-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c395a-178">\<binding></span><span class="sxs-lookup"><span data-stu-id="c395a-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- <span data-ttu-id="c395a-179">[NET TCP de mesmo nível](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c395a-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="c395a-180">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="c395a-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
