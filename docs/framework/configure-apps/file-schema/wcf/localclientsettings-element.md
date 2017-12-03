---
title: '&lt;localClientSettings&gt; element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cabde7eb9dd122c2f7060b2f2e2c16f5949dc1f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalclientsettingsgt-element"></a><span data-ttu-id="5bb63-102">&lt;localClientSettings&gt; element</span><span class="sxs-lookup"><span data-stu-id="5bb63-102">&lt;localClientSettings&gt; element</span></span>
<span data-ttu-id="5bb63-103">Especifica as configurações de segurança de um cliente local para esta associação.</span><span class="sxs-lookup"><span data-stu-id="5bb63-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="5bb63-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5bb63-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5bb63-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="5bb63-105">\<bindings></span></span>  
<span data-ttu-id="5bb63-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5bb63-106">\<customBinding></span></span>  
<span data-ttu-id="5bb63-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5bb63-107">\<binding></span></span>  
<span data-ttu-id="5bb63-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="5bb63-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb63-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bb63-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bb63-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5bb63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5bb63-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5bb63-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bb63-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5bb63-112">Attributes</span></span>  
  
|<span data-ttu-id="5bb63-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5bb63-113">Attribute</span></span>|<span data-ttu-id="5bb63-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bb63-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="5bb63-115">Um valor booleano que especifica se o cache de cookie está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5bb63-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="5bb63-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5bb63-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="5bb63-117">Um inteiro que especifica o percentual máximo de cookies que podem ser renovados.</span><span class="sxs-lookup"><span data-stu-id="5bb63-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="5bb63-118">Esse valor deve estar entre 0 e 100, inclusive.</span><span class="sxs-lookup"><span data-stu-id="5bb63-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="5bb63-119">O padrão é 90.</span><span class="sxs-lookup"><span data-stu-id="5bb63-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="5bb63-120">Um valor booleano que especifica se os ataques por repetição contra o canal são detectados e lidados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5bb63-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="5bb63-121">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="5bb63-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="5bb63-122">Um <xref:System.TimeSpan> que especifica a diferença máxima de tempo entre os relógios do sistema das duas partes da comunicação.</span><span class="sxs-lookup"><span data-stu-id="5bb63-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="5bb63-123">O valor padrão é "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="5bb63-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="5bb63-124">Quando esse valor é definido como o padrão, o receptor aceita mensagens com carimbos de hora de envio para cima para 5 minutos mais tarde ou antes da hora em que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="5bb63-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="5bb63-125">As mensagens que não passarem no teste de tempo de envio são rejeitadas.</span><span class="sxs-lookup"><span data-stu-id="5bb63-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="5bb63-126">Essa configuração é usada em conjunto com o `replayWindow` atributo.</span><span class="sxs-lookup"><span data-stu-id="5bb63-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="5bb63-127">Um <xref:System.TimeSpan> que especifica o tempo de vida máximo de cookies.</span><span class="sxs-lookup"><span data-stu-id="5bb63-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="5bb63-128">O valor padrão é "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="5bb63-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="5bb63-129">Um valor booleano que especifica se as conexões usando mensagens WS-Reliable tentarão reconectar após falhas de transporte.</span><span class="sxs-lookup"><span data-stu-id="5bb63-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="5bb63-130">O padrão é `true`, que significa a tentativa de infinita tenta se reconectar.</span><span class="sxs-lookup"><span data-stu-id="5bb63-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="5bb63-131">O ciclo é interrompido pelo tempo limite de inatividade, que faz com que o canal lançar uma exceção quando ele não pode ser reconectado.</span><span class="sxs-lookup"><span data-stu-id="5bb63-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="5bb63-132">Um inteiro positivo que especifica o número de momentos em cache usados para detecção de repetição.</span><span class="sxs-lookup"><span data-stu-id="5bb63-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="5bb63-133">Se esse limite for excedido, o valor de uso único mais antigo é removido e um novo valor de uso único é criado para a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="5bb63-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="5bb63-134">O valor padrão é 500000.</span><span class="sxs-lookup"><span data-stu-id="5bb63-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="5bb63-135">Um <xref:System.TimeSpan> que especifica a duração em que momentos de mensagens individuais são válidos.</span><span class="sxs-lookup"><span data-stu-id="5bb63-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="5bb63-136">Após a duração, uma mensagem enviada com o mesmo nonce como aquela enviada antes não serão aceitas.</span><span class="sxs-lookup"><span data-stu-id="5bb63-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="5bb63-137">Este atributo é usado em conjunto com o `maxClockSkew` atributo para impedir ataques de repetição.</span><span class="sxs-lookup"><span data-stu-id="5bb63-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="5bb63-138">Um invasor pode repetir uma mensagem depois de sua janela de reprodução tiver expirado.</span><span class="sxs-lookup"><span data-stu-id="5bb63-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="5bb63-139">Esta mensagem, no entanto, falhará a `maxClockSkew` teste que rejeita mensagens com carimbos de hora de envio até uma hora especificada posterior ou anterior à hora que a mensagem foi recebida.</span><span class="sxs-lookup"><span data-stu-id="5bb63-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="5bb63-140">Um <xref:System.TimeSpan> que especifica a duração após a qual o iniciador renovará a chave da sessão de segurança.</span><span class="sxs-lookup"><span data-stu-id="5bb63-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="5bb63-141">O padrão é "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="5bb63-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="5bb63-142">Um <xref:System.TimeSpan> que especifica o intervalo de tempo, uma chave de sessão anterior é válido nas mensagens de entrada durante uma renovação de chave.</span><span class="sxs-lookup"><span data-stu-id="5bb63-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="5bb63-143">O padrão é "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="5bb63-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="5bb63-144">Durante a renovação de chave, o cliente e o servidor sempre devem enviar mensagens usando a chave disponível mais recente.</span><span class="sxs-lookup"><span data-stu-id="5bb63-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="5bb63-145">Ambas as partes aceitará as mensagens de entrada protegidas com a chave de sessão anterior até que o tempo de sobreposição expire.</span><span class="sxs-lookup"><span data-stu-id="5bb63-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="5bb63-146">Um positivo <xref:System.TimeSpan> que especifica a duração na qual um carimbo de data / hora é válido.</span><span class="sxs-lookup"><span data-stu-id="5bb63-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="5bb63-147">O padrão é "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="5bb63-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bb63-148">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5bb63-148">Child Elements</span></span>  
 <span data-ttu-id="5bb63-149">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5bb63-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bb63-150">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5bb63-150">Parent Elements</span></span>  
  
|<span data-ttu-id="5bb63-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="5bb63-151">Element</span></span>|<span data-ttu-id="5bb63-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bb63-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bb63-153">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="5bb63-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="5bb63-154">Especifica as opções de segurança para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5bb63-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="5bb63-155">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="5bb63-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="5bb63-156">Especifica os valores padrão usados para iniciar um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="5bb63-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bb63-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb63-157">Remarks</span></span>  
 <span data-ttu-id="5bb63-158">As configurações são locais no sentido de que eles não são derivadas da política de segurança do serviço de configurações.</span><span class="sxs-lookup"><span data-stu-id="5bb63-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb63-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bb63-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <span data-ttu-id="5bb63-160">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="5bb63-160">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="5bb63-161">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5bb63-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5bb63-162">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5bb63-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5bb63-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5bb63-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="5bb63-164">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5bb63-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="5bb63-165">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="5bb63-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
