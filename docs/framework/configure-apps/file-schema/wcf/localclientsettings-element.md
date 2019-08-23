---
title: Elemento <localClientSettings>
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e7331105582a4a48b7edd8cd4f6a691771b0b8ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930807"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="b9b87-102">\<elemento de > localClientSettings</span><span class="sxs-lookup"><span data-stu-id="b9b87-102">\<localClientSettings> element</span></span>
<span data-ttu-id="b9b87-103">Especifica as configurações de segurança de um cliente local para esta associação.</span><span class="sxs-lookup"><span data-stu-id="b9b87-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="b9b87-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9b87-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b9b87-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b9b87-105">\<bindings></span></span>  
<span data-ttu-id="b9b87-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b9b87-106">\<customBinding></span></span>  
<span data-ttu-id="b9b87-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="b9b87-107">\<binding></span></span>  
<span data-ttu-id="b9b87-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="b9b87-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b87-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9b87-109">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9b87-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b9b87-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b9b87-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b9b87-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9b87-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b9b87-112">Attributes</span></span>  
  
|<span data-ttu-id="b9b87-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9b87-113">Attribute</span></span>|<span data-ttu-id="b9b87-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9b87-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="b9b87-115">Um valor booliano que especifica se o Caching de cookie está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b9b87-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="b9b87-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b9b87-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="b9b87-117">Um inteiro que especifica a porcentagem máxima de cookies que podem ser renovados.</span><span class="sxs-lookup"><span data-stu-id="b9b87-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="b9b87-118">Esse valor deve estar entre 0 e 100, inclusive.</span><span class="sxs-lookup"><span data-stu-id="b9b87-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="b9b87-119">O padrão é 90.</span><span class="sxs-lookup"><span data-stu-id="b9b87-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="b9b87-120">Um valor booliano que especifica se os ataques de repetição no canal são detectados e tratados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b9b87-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="b9b87-121">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b9b87-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="b9b87-122">Um <xref:System.TimeSpan> valor que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes que se comunicam.</span><span class="sxs-lookup"><span data-stu-id="b9b87-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="b9b87-123">O valor padrão é "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="b9b87-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b9b87-124">Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de hora de tempo de envio de até 5 minutos depois ou antes da hora em que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="b9b87-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="b9b87-125">As mensagens que não passam no teste de tempo de envio são rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="b9b87-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="b9b87-126">Essa configuração é usada em conjunto com o `replayWindow` atributo.</span><span class="sxs-lookup"><span data-stu-id="b9b87-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="b9b87-127">Um <xref:System.TimeSpan> valor que especifica o tempo de vida máximo de cookies.</span><span class="sxs-lookup"><span data-stu-id="b9b87-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="b9b87-128">O valor padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="b9b87-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="b9b87-129">Um valor booliano que especifica se as conexões que usam o sistema de mensagens WS-Reliable tentarão se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="b9b87-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="b9b87-130">O padrão é `true`, o que significa que tentativas infinitas de reconexão são tentadas.</span><span class="sxs-lookup"><span data-stu-id="b9b87-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="b9b87-131">O ciclo é rompido pelo tempo limite de inatividade, o que faz com que o canal lance uma exceção quando não pode ser reconectado.</span><span class="sxs-lookup"><span data-stu-id="b9b87-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="b9b87-132">Um inteiro positivo que especifica o número de nonces em cache usados para detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="b9b87-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="b9b87-133">Se esse limite for excedido, o nonce mais antigo será removido e um novo nonce será criado para a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="b9b87-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="b9b87-134">O valor padrão é 500000.</span><span class="sxs-lookup"><span data-stu-id="b9b87-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="b9b87-135">Um <xref:System.TimeSpan> que especifica a duração em que os nonces de mensagem individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="b9b87-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="b9b87-136">Após essa duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não será aceita.</span><span class="sxs-lookup"><span data-stu-id="b9b87-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="b9b87-137">Esse atributo é usado em conjunto com o `maxClockSkew` atributo para evitar ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="b9b87-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="b9b87-138">Um invasor pode repetir uma mensagem depois que sua janela de reprodução tiver expirado.</span><span class="sxs-lookup"><span data-stu-id="b9b87-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="b9b87-139">Essa mensagem, no entanto, falharia no `maxClockSkew` teste que rejeitava mensagens com carimbos de data/hora em tempo de envio até um tempo especificado depois ou antes da hora em que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="b9b87-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="b9b87-140">Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="b9b87-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="b9b87-141">O padrão é "10:00:00".</span><span class="sxs-lookup"><span data-stu-id="b9b87-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="b9b87-142">Um <xref:System.TimeSpan> que especifica o intervalo de tempo que uma chave de sessão anterior é válida em mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="b9b87-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="b9b87-143">O padrão é "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="b9b87-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b9b87-144">Durante a renovação da chave, o cliente e o servidor devem sempre enviar mensagens usando a chave mais atual disponível.</span><span class="sxs-lookup"><span data-stu-id="b9b87-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="b9b87-145">Ambas as partes aceitarão mensagens de entrada protegidas com a chave de sessão anterior até que o tempo de substituição expire.</span><span class="sxs-lookup"><span data-stu-id="b9b87-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="b9b87-146">Um positivo <xref:System.TimeSpan> que especifica a duração em que um carimbo de data/hora é válido.</span><span class="sxs-lookup"><span data-stu-id="b9b87-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="b9b87-147">O padrão é "00:15:00".</span><span class="sxs-lookup"><span data-stu-id="b9b87-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9b87-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9b87-148">Child Elements</span></span>  
 <span data-ttu-id="b9b87-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9b87-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9b87-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9b87-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b9b87-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9b87-151">Element</span></span>|<span data-ttu-id="b9b87-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9b87-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9b87-153">\<security></span><span class="sxs-lookup"><span data-stu-id="b9b87-153">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="b9b87-154">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b9b87-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="b9b87-155">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="b9b87-155">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="b9b87-156">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="b9b87-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b87-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9b87-157">Remarks</span></span>  
 <span data-ttu-id="b9b87-158">As configurações são locais no sentido de que elas não são configurações derivadas da política de segurança do serviço.</span><span class="sxs-lookup"><span data-stu-id="b9b87-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b87-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9b87-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b9b87-160">Associações</span><span class="sxs-lookup"><span data-stu-id="b9b87-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9b87-161">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b9b87-161">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b9b87-162">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="b9b87-162">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b9b87-163">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b9b87-163">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b9b87-164">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b9b87-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b9b87-165">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="b9b87-165">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
