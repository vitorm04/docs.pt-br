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
ms.openlocfilehash: df56d3f2bfe351c38ca2e64539de13e4cc556d2a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405039"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="b5244-102">Como habilitar a detecção de repetição de mensagem</span><span class="sxs-lookup"><span data-stu-id="b5244-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="b5244-103">Um ataque de repetição ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo a um ou mais das partes.</span><span class="sxs-lookup"><span data-stu-id="b5244-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="b5244-104">A menos que atenuado, os computadores sujeita a ataque processará o fluxo como mensagens legítimas, resultando em um intervalo de consequências incorretas, como com redundância de pedidos de um item.</span><span class="sxs-lookup"><span data-stu-id="b5244-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="b5244-105">Para obter mais informações sobre a detecção de reprodução de mensagem, consulte [detecção de reprodução de mensagem](https://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="b5244-105">For more information about message replay detection, see [Message Replay Detection](https://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="b5244-106">O procedimento a seguir demonstra as várias propriedades que você pode usar para controlar a detecção de reprodução usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b5244-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="b5244-107">Para controlar a detecção de reprodução no cliente usando código</span><span class="sxs-lookup"><span data-stu-id="b5244-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="b5244-108">Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="b5244-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="b5244-109">Para obter mais informações, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="b5244-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="b5244-110">O exemplo a seguir usa uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> criado com o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> da <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="b5244-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="b5244-111">Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> de classe e definir qualquer uma das propriedades a seguir, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="b5244-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="b5244-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="b5244-112">`DetectReplay`.</span></span> <span data-ttu-id="b5244-113">Um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="b5244-113">A Boolean value.</span></span> <span data-ttu-id="b5244-114">Isso determina se o cliente deve detectar repetições do servidor.</span><span class="sxs-lookup"><span data-stu-id="b5244-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="b5244-115">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b5244-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="b5244-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="b5244-116">`MaxClockSkew`.</span></span> <span data-ttu-id="b5244-117">Um valor <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b5244-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="b5244-118">Controla quanto distorção de tempo que o mecanismo de reprodução pode tolerar entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="b5244-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="b5244-119">O mecanismo de segurança examina o tempo de carimbo de data / enviados e determina se ele foi enviado muito distante no passado.</span><span class="sxs-lookup"><span data-stu-id="b5244-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="b5244-120">O padrão é 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="b5244-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="b5244-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="b5244-121">`ReplayWindow`.</span></span> <span data-ttu-id="b5244-122">Um valor `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="b5244-122">A `TimeSpan` value.</span></span> <span data-ttu-id="b5244-123">Isso controla quanto tempo uma mensagem podem residir na rede depois que o servidor envia a ele (por meio de intermediários) antes de alcançar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b5244-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="b5244-124">O cliente controla as assinaturas das mensagens enviadas dentro a versão mais recente `ReplayWindow` para fins de detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="b5244-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="b5244-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="b5244-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="b5244-126">Um valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="b5244-126">An integer value.</span></span> <span data-ttu-id="b5244-127">O cliente armazena as assinaturas da mensagem em um cache.</span><span class="sxs-lookup"><span data-stu-id="b5244-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="b5244-128">Essa configuração especifica quantas assinaturas, o cache pode armazenar.</span><span class="sxs-lookup"><span data-stu-id="b5244-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="b5244-129">Se o número de mensagens enviadas dentro a última janela reprodução atingir o limite de cache, novas mensagens são rejeitadas até que as assinaturas em cache mais antigas alcance o limite de tempo.</span><span class="sxs-lookup"><span data-stu-id="b5244-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="b5244-130">O padrão é 500000.</span><span class="sxs-lookup"><span data-stu-id="b5244-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="b5244-131">Para controlar a detecção de reprodução no serviço usando código</span><span class="sxs-lookup"><span data-stu-id="b5244-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="b5244-132">Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="b5244-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="b5244-133">Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> de classe e defina as propriedades conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b5244-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="b5244-134">Para controlar a detecção de reprodução na configuração do cliente ou serviço</span><span class="sxs-lookup"><span data-stu-id="b5244-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="b5244-135">Criar uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b5244-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="b5244-136">Criar um `<security>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b5244-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="b5244-137">Criar uma [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) ou [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="b5244-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="b5244-138">Defina os seguintes valores de atributo, conforme apropriado: `detectReplays`, `maxClockSkew`, `replayWindow`, e `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="b5244-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="b5244-139">O exemplo a seguir define os atributos de ambos um `<localServiceSettings>` e um `<localClientSettings>` elemento:</span><span class="sxs-lookup"><span data-stu-id="b5244-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b5244-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5244-140">Example</span></span>  
 <span data-ttu-id="b5244-141">O exemplo a seguir cria uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> método e define as propriedades de reprodução da associação.</span><span class="sxs-lookup"><span data-stu-id="b5244-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="b5244-142">Escopo da reprodução: somente segurança da mensagem</span><span class="sxs-lookup"><span data-stu-id="b5244-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="b5244-143">Observe que os procedimentos a seguir se aplicam somente ao modo de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b5244-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="b5244-144">Para o transporte com modos de credencial de mensagem e transporte, os mecanismos de transporte detectam repetições.</span><span class="sxs-lookup"><span data-stu-id="b5244-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="b5244-145">Proteger as notas de conversa</span><span class="sxs-lookup"><span data-stu-id="b5244-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="b5244-146">Para associações que permitem que conversas seguras, você pode ajustar essas configurações tanto para o canal de aplicativo, bem como para a associação de inicialização de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="b5244-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="b5244-147">Por exemplo, você pode desativar repetições para o canal de aplicativo, mas habilitá-los para o canal de bootstrap que estabelece a conversa segura.</span><span class="sxs-lookup"><span data-stu-id="b5244-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="b5244-148">Se você não usar sessões de conversa segura, detecção de reprodução não garante a detecção de repetições em cenários de farm de servidor e quando o processo ser reciclado.</span><span class="sxs-lookup"><span data-stu-id="b5244-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="b5244-149">Isso se aplica às seguintes associações fornecidas pelo sistema:</span><span class="sxs-lookup"><span data-stu-id="b5244-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="b5244-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b5244-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="b5244-151"><xref:System.ServiceModel.WSHttpBinding> com o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="b5244-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5244-152">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b5244-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b5244-153">Os seguintes namespaces são necessários para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="b5244-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="b5244-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5244-154">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="b5244-155">Sessões e conversas seguras</span><span class="sxs-lookup"><span data-stu-id="b5244-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [<span data-ttu-id="b5244-156">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="b5244-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [<span data-ttu-id="b5244-157">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b5244-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
