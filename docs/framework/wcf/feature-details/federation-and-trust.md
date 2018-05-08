---
title: Federação e confiabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: fc6a14ed825fa447e80a8389684d10ed07a00815
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="federation-and-trust"></a>Federação e confiabilidade
Este tópico abrange vários aspectos relacionados a aplicativos federados, limites de confiança e configuração e uso de tokens emitidos no Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Serviços, serviços de Token de segurança e confiança  
 Serviços que expõem pontos de extremidade federados normalmente esperam que os clientes se autentiquem usando um token fornecido por um emissor específico. É importante que o serviço está configurado com as credenciais corretas para o emissor; Caso contrário, não será capaz de verificar assinaturas em tokens emitidos, e o cliente será capaz de se comunicar com o serviço. Para obter mais informações sobre como configurar credenciais de emissor do serviço, consulte [como: configurar credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Da mesma forma, ao usar chaves simétricas, as chaves são criptografadas para o serviço de destino, assim você deve configurar o serviço de token de segurança com as credenciais corretas para o serviço de destino; Caso contrário, ele será não é possível criptografar a chave para o serviço de destino, e novamente, o cliente será capaz de se comunicar com o serviço.  
  
 Serviços WCF usam o valor da <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> propriedade o [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) para permitir o relógio defasagem horária entre o cliente e o serviço. Na federação, o `MaxClockSkew` configuração se aplica a inclina relógio entre o cliente e o serviço de token de segurança do qual o cliente obteve o token emitido. Portanto, os serviços de token de segurança não precisam fazer concessões defasagem horária ao definir tempos de efetivação e expiração do token emitido.  
  
> [!NOTE]
>  A importância de distorção do relógio aumenta à medida que reduz o tempo de vida do token emitido. Na maioria dos casos, defasagem horária não é um problema significativo se o tempo de vida do token é 30 minutos ou mais. Cenários com tempos de vida mais curto ou em que o tempo de validade exato do token é importante devem ser projetados para levar o distorção do relógio em conta.  
  
## <a name="federated-endpoints-and-time-outs"></a>Tempos limite e pontos de extremidade federados  
 Quando um cliente se comunica com um ponto de extremidade federado, ele deve primeiro adquirir um token apropriado de um serviço de token de segurança. Se o serviço de token de segurança expõe um ponto de extremidade federado, o cliente deve primeiro obter um token do emissor para esse ponto de extremidade. Cada aquisição de token leva tempo e tempo está sujeito ao tempo limite geral para enviar a mensagem real para o ponto de extremidade final.  
  
 Por exemplo, o tempo limite no canal do lado do cliente é definido como 30 segundos. Emissores de token dois precisam ser chamado para recuperar tokens antes de enviar a mensagem para o ponto de extremidade final e cada uma usa 15 segundos para emitir um token. Nesse caso, a tentativa falhará e um <xref:System.TimeoutException> é gerada. Portanto, você precisará definir o <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> valor o canal do cliente para um valor grande o suficiente para incluir o tempo necessário para recuperar todos os tokens emitidos. No caso em que um valor não for especificado para o <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> propriedade, o <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> propriedade ou o <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> propriedade (ou ambos) precisam ser definidos para um valor grande o suficiente para incluir o tempo necessário para recuperar os tokens emitidos todos.  
  
## <a name="token-lifetime-and-renewal"></a>Vida útil do token e renovação  
 Clientes do WCF não verifica o token emitido ao fazer uma solicitação inicial para um serviço.  Em vez disso, o WCF confia o serviço de token de segurança para emitir um token com momentos apropriados de efetivação e expiração. Se o token é armazenado em cache pelo cliente e reutilizado, a vida útil do token é verificada em solicitações subsequentes e o cliente renova automaticamente o token se necessário. Para obter mais informações sobre o cache de token, consulte [como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Especificar tempos de vida curtos, de 30 segundos ou menos para emitidos símbolos ou tokens de contexto de segurança, pode resultar em tempos limite de negociação ou outras exceções que está sendo geradas pelos clientes do WCF ao solicitar tokens emitidos ou quando a negociação ou renovação de segurança tokens de contexto.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Tokens emitidos e InclusionMode  
 Se um token emitido é serializado em uma mensagem enviada de um cliente para um ponto de extremidade federado ou não é controlado pela configuração de <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> propriedade o <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> classe. Essa propriedade pode ser definida para uma da <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> valores de enumeração, mas não é útil em cenários mais federados. O `SecurityTokenInclusionMode.Never` e `SecurityTokenInclusionMode.AlwaysToInitiator` valores fazem com que o cliente envie uma referência para o token emitido pelo serviço de token de segurança para a terceira parte confiável. A menos que a terceira parte confiável tiver uma cópia da autenticação do token emitida falhará porque a referência de token não for resolvida. O WCF trata `SecurityTokenInclusionMode.Once` como equivalente à `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>  
 [Como criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Como configurar as credenciais em um Serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Como criar um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
