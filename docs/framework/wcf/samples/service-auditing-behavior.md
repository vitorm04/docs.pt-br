---
title: "Comportamento de auditoria de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f84bff892a35288a75738d9cfa326ffc4119b433
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="service-auditing-behavior"></a>Comportamento de auditoria de serviço
Este exemplo demonstra como usar o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> para habilitar a auditoria de eventos de segurança durante operações de serviço. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço e o cliente tiverem sido configurados usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definida como `Message` e `clientCredentialType` foi definida como `Windows`. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O arquivo de configuração de serviço usa o `serviceSecurityAudit` elemento para configurar a auditoria.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do console para desligar o cliente.  
  
 Os logs de auditoria resultante podem ser vistos ao executar o Visualizador de eventos. Por padrão, no Windows XP, os eventos de auditoria podem ser vistos no Log do aplicativo ao mesmo tempo no Windows Server 2003 e Windows Vista, os eventos de auditoria podem ser vistos no Log de segurança. No Windows Server 2008 e Windows 7, os eventos de auditoria podem ser vistos nos logs de aplicativos e serviços. O local dos eventos de auditoria pode ser especificado definindo a `auditLogLocation` atributo "Aplicativo" ou "Segurança". Para obter mais informações, consulte [como: eventos de auditoria de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Se os eventos são gravados no Log de segurança do LocalSecurityPolicy -> que habilitar acesso do objeto deve ser definido como "Êxito" e "Falha".  
  
 Ao examinar o log de eventos, a origem dos eventos de auditoria é "ServiceModel auditoria 3.0.0.0". Registros de auditoria de autenticação de mensagem tem uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço tem uma categoria de "ServiceAuthorization".  
  
 Eventos de auditoria de autenticação de mensagem abrangem se a mensagem foi violada, se a mensagem expirou, e se o cliente pode autenticar para o serviço. Eles fornecem informações sobre se a autenticação foi bem-sucedida ou falhou com a identidade do cliente e o ponto de extremidade a mensagem foi enviado ao junto com a ação associada à mensagem.  
  
 Eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização do serviço. Eles fornecem informações sobre se a autorização teve êxito ou falha com a identidade do cliente, o ponto de extremidade a mensagem foi enviado para a ação associada à mensagem, o identificador do contexto de autorização que foi gerado a partir de mensagem de entrada e o tipo do Gerenciador de autorização que fez a decisão de acesso.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [A auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Como: auditoria de eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
