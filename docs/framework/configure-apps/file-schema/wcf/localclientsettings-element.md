---
title: Elemento <localClientSettings>
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 19eaea71fdaad1b945524cca5cf15634e0b0fa14
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158728"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="90259-102">Elemento \<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="90259-102">\<localClientSettings> element</span></span>

<span data-ttu-id="90259-103">Especifica as configurações de segurança de um cliente local para esta associação.</span><span class="sxs-lookup"><span data-stu-id="90259-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="90259-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="90259-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90259-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90259-105">Attributes and Elements</span></span>  

 <span data-ttu-id="90259-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="90259-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90259-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="90259-107">Attributes</span></span>  
  
|<span data-ttu-id="90259-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="90259-108">Attribute</span></span>|<span data-ttu-id="90259-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="90259-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="90259-110">Um valor booliano que especifica se o Caching de cookie está habilitado.</span><span class="sxs-lookup"><span data-stu-id="90259-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="90259-111">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="90259-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="90259-112">Um inteiro que especifica a porcentagem máxima de cookies que podem ser renovados.</span><span class="sxs-lookup"><span data-stu-id="90259-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="90259-113">Esse valor deve estar entre 0 e 100, inclusive.</span><span class="sxs-lookup"><span data-stu-id="90259-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="90259-114">O padrão é 90.</span><span class="sxs-lookup"><span data-stu-id="90259-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="90259-115">Um valor booliano que especifica se os ataques de repetição no canal são detectados e tratados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="90259-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="90259-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="90259-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="90259-117">Um <xref:System.TimeSpan> valor que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes que se comunicam.</span><span class="sxs-lookup"><span data-stu-id="90259-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="90259-118">O valor padrão é "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="90259-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="90259-119">Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de hora de tempo de envio de até 5 minutos depois ou antes da hora em que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="90259-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="90259-120">As mensagens que não passam no teste de tempo de envio são rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="90259-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="90259-121">Essa configuração é usada em conjunto com o `replayWindow` atributo.</span><span class="sxs-lookup"><span data-stu-id="90259-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="90259-122">Um <xref:System.TimeSpan> valor que especifica o tempo de vida máximo de cookies.</span><span class="sxs-lookup"><span data-stu-id="90259-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="90259-123">O valor padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="90259-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="90259-124">Um valor booliano que especifica se as conexões que usam o sistema de mensagens WS-Reliable tentarão se reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="90259-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="90259-125">O padrão é `true` , o que significa que tentativas infinitas de reconexão são tentadas.</span><span class="sxs-lookup"><span data-stu-id="90259-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="90259-126">O ciclo é rompido pelo tempo limite de inatividade, o que faz com que o canal lance uma exceção quando não pode ser reconectado.</span><span class="sxs-lookup"><span data-stu-id="90259-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="90259-127">Um inteiro positivo que especifica o número de nonces em cache usados para detecção de reprodução.</span><span class="sxs-lookup"><span data-stu-id="90259-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="90259-128">Se esse limite for excedido, o nonce mais antigo será removido e um novo nonce será criado para a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="90259-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="90259-129">O valor padrão é 500000.</span><span class="sxs-lookup"><span data-stu-id="90259-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="90259-130">Um <xref:System.TimeSpan> que especifica a duração em que os nonces de mensagem individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="90259-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="90259-131">Após essa duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não será aceita.</span><span class="sxs-lookup"><span data-stu-id="90259-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="90259-132">Esse atributo é usado em conjunto com o `maxClockSkew` atributo para evitar ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="90259-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="90259-133">Um invasor pode repetir uma mensagem depois que sua janela de reprodução tiver expirado.</span><span class="sxs-lookup"><span data-stu-id="90259-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="90259-134">Essa mensagem, no entanto, falharia no `maxClockSkew` teste que rejeitava mensagens com carimbos de data/hora em tempo de envio até um tempo especificado depois ou antes da hora em que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="90259-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="90259-135">Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="90259-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="90259-136">O padrão é "10:00:00".</span><span class="sxs-lookup"><span data-stu-id="90259-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="90259-137">Um <xref:System.TimeSpan> que especifica o intervalo de tempo que uma chave de sessão anterior é válida em mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="90259-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="90259-138">O padrão é "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="90259-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="90259-139">Durante a renovação da chave, o cliente e o servidor devem sempre enviar mensagens usando a chave mais atual disponível.</span><span class="sxs-lookup"><span data-stu-id="90259-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="90259-140">Ambas as partes aceitarão mensagens de entrada protegidas com a chave de sessão anterior até que o tempo de substituição expire.</span><span class="sxs-lookup"><span data-stu-id="90259-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="90259-141">Um positivo <xref:System.TimeSpan> que especifica a duração em que um carimbo de data/hora é válido.</span><span class="sxs-lookup"><span data-stu-id="90259-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="90259-142">O padrão é "00:15:00".</span><span class="sxs-lookup"><span data-stu-id="90259-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90259-143">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="90259-143">Child Elements</span></span>  

 <span data-ttu-id="90259-144">Nenhum</span><span class="sxs-lookup"><span data-stu-id="90259-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90259-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="90259-145">Parent Elements</span></span>  
  
|<span data-ttu-id="90259-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="90259-146">Element</span></span>|<span data-ttu-id="90259-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="90259-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="90259-148">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="90259-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="90259-149">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="90259-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90259-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="90259-150">Remarks</span></span>  

 <span data-ttu-id="90259-151">As configurações são locais no sentido de que elas não são configurações derivadas da política de segurança do serviço.</span><span class="sxs-lookup"><span data-stu-id="90259-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90259-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="90259-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="90259-153">Associações</span><span class="sxs-lookup"><span data-stu-id="90259-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="90259-154">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="90259-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="90259-155">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="90259-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="90259-156">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="90259-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="90259-157">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="90259-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
