---
title: Como habilitar a detecção de repetição de mensagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184946"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="7e71d-102">Como habilitar a detecção de repetição de mensagem</span><span class="sxs-lookup"><span data-stu-id="7e71d-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="7e71d-103">Um ataque de repetição ocorre quando um invasor copia um fluxo de mensagens entre duas partes e reproduz o fluxo para uma ou mais das partes.</span><span class="sxs-lookup"><span data-stu-id="7e71d-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="7e71d-104">A menos que mitigado, os computadores sujeitos ao ataque processarão o fluxo como mensagens legítimas, resultando em uma série de consequências ruins, como ordens redundantes de um item.</span><span class="sxs-lookup"><span data-stu-id="7e71d-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="7e71d-105">Para obter mais informações sobre a detecção de repetição de mensagens, consulte [Detecção de reprodução de mensagens](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="7e71d-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="7e71d-106">O procedimento a seguir demonstra várias propriedades que você pode usar para controlar a detecção de repetição usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7e71d-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="7e71d-107">Para controlar a detecção de repetição no cliente usando código</span><span class="sxs-lookup"><span data-stu-id="7e71d-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="7e71d-108">Crie <xref:System.ServiceModel.Channels.SecurityBindingElement> um para <xref:System.ServiceModel.Channels.CustomBinding>usar em um .</span><span class="sxs-lookup"><span data-stu-id="7e71d-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="7e71d-109">Para obter mais informações, [consulte Como: Criar uma vinculação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7e71d-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="7e71d-110">O exemplo a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> seguir usa <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> um <xref:System.ServiceModel.Channels.SecurityBindingElement> criado com o da classe.</span><span class="sxs-lookup"><span data-stu-id="7e71d-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="7e71d-111">Use <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> a propriedade para retornar <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> uma referência à classe e definir qualquer uma das seguintes propriedades, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="7e71d-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="7e71d-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-112">`DetectReplay`.</span></span> <span data-ttu-id="7e71d-113">Um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="7e71d-113">A Boolean value.</span></span> <span data-ttu-id="7e71d-114">Isso rege se o cliente deve detectar replays do servidor.</span><span class="sxs-lookup"><span data-stu-id="7e71d-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="7e71d-115">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="7e71d-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-116">`MaxClockSkew`.</span></span> <span data-ttu-id="7e71d-117">Um valor <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="7e71d-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="7e71d-118">Ele governa quanto tempo o mecanismo de repetição pode tolerar entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="7e71d-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="7e71d-119">O mecanismo de segurança examina o carimbo de hora enviado e determina se foi enviado muito para trás no passado.</span><span class="sxs-lookup"><span data-stu-id="7e71d-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="7e71d-120">O padrão é 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e71d-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="7e71d-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-121">`ReplayWindow`.</span></span> <span data-ttu-id="7e71d-122">Um valor `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-122">A `TimeSpan` value.</span></span> <span data-ttu-id="7e71d-123">Isso rege o tempo que uma mensagem pode viver na rede depois que o servidor a envia (através de intermediários) antes de chegar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7e71d-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="7e71d-124">O cliente rastreia as assinaturas das mensagens enviadas no mais recente `ReplayWindow` para fins de detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="7e71d-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="7e71d-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="7e71d-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="7e71d-126">Um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="7e71d-126">An integer value.</span></span> <span data-ttu-id="7e71d-127">O cliente armazena as assinaturas da mensagem em um cache.</span><span class="sxs-lookup"><span data-stu-id="7e71d-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="7e71d-128">Esta configuração especifica quantas assinaturas o cache pode armazenar.</span><span class="sxs-lookup"><span data-stu-id="7e71d-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="7e71d-129">Se o número de mensagens enviadas na última janela de replay atingir o limite de cache, novas mensagens serão rejeitadas até que as assinaturas armazenadas em cache mais antigas atinjam o limite de tempo.</span><span class="sxs-lookup"><span data-stu-id="7e71d-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="7e71d-130">O padrão é 500000.</span><span class="sxs-lookup"><span data-stu-id="7e71d-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="7e71d-131">Para controlar a detecção de repetição no serviço usando código</span><span class="sxs-lookup"><span data-stu-id="7e71d-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="7e71d-132">Crie <xref:System.ServiceModel.Channels.SecurityBindingElement> um para <xref:System.ServiceModel.Channels.CustomBinding>usar em um .</span><span class="sxs-lookup"><span data-stu-id="7e71d-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="7e71d-133">Use <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> a propriedade para retornar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> uma referência à classe e defina as propriedades como descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e71d-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="7e71d-134">Para controlar a detecção de repetição na configuração para o cliente ou serviço</span><span class="sxs-lookup"><span data-stu-id="7e71d-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="7e71d-135">Crie um [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="7e71d-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="7e71d-136">Crie `<security>` um elemento.</span><span class="sxs-lookup"><span data-stu-id="7e71d-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="7e71d-137">Crie um [ \<>de configurações de cliente sumido](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) local ou [ \<>de serviços locais ](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="7e71d-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="7e71d-138">Defina os seguintes valores `maxClockSkew` `replayWindow`de `replayCacheSize`atributo, conforme apropriado: `detectReplays`, e .</span><span class="sxs-lookup"><span data-stu-id="7e71d-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="7e71d-139">O exemplo a seguir define `<localServiceSettings>` os `<localClientSettings>` atributos de a e de um elemento:</span><span class="sxs-lookup"><span data-stu-id="7e71d-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="7e71d-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e71d-140">Example</span></span>  
 <span data-ttu-id="7e71d-141">O exemplo a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> seguir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> cria um uso do método e define as propriedades de repetição da vinculação.</span><span class="sxs-lookup"><span data-stu-id="7e71d-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="7e71d-142">Escopo de replay: somente segurança de mensagens</span><span class="sxs-lookup"><span data-stu-id="7e71d-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="7e71d-143">Observe que os procedimentos a seguir se aplicam apenas ao modo de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7e71d-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="7e71d-144">Para os modos Transport and Transport with Message Credential, os mecanismos de transporte detectam repetições.</span><span class="sxs-lookup"><span data-stu-id="7e71d-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="7e71d-145">Notas de conversação seguras</span><span class="sxs-lookup"><span data-stu-id="7e71d-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="7e71d-146">Para vinculações que permitem conversas seguras, você pode ajustar essas configurações tanto para o canal do aplicativo quanto para a vinculação de bootstrap de conversação segura.</span><span class="sxs-lookup"><span data-stu-id="7e71d-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="7e71d-147">Por exemplo, você pode desativar replays para o canal do aplicativo, mas habilitá-los para o canal bootstrap que estabelece a conversa segura.</span><span class="sxs-lookup"><span data-stu-id="7e71d-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="7e71d-148">Se você não usar sessões de conversação seguras, a detecção de repetição não garante a detecção de replays em cenários de fazendas de servidores e quando o processo é reciclado.</span><span class="sxs-lookup"><span data-stu-id="7e71d-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="7e71d-149">Isso se aplica às seguintes vinculações fornecidas pelo sistema:</span><span class="sxs-lookup"><span data-stu-id="7e71d-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="7e71d-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="7e71d-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="7e71d-151"><xref:System.ServiceModel.WSHttpBinding>com <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> a propriedade `false`definida para .</span><span class="sxs-lookup"><span data-stu-id="7e71d-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e71d-152">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7e71d-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="7e71d-153">Os seguintes namespaces são necessários para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="7e71d-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="7e71d-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e71d-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="7e71d-155">Sessões seguras e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="7e71d-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="7e71d-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="7e71d-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="7e71d-157">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7e71d-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
