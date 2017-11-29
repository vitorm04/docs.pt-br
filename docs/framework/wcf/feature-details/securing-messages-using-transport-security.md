---
title: "Mensagens de segurança que usam a segurança de transporte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f36351c04b3849b5364e00cec55769628d89af11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-messages-using-transport-security"></a>Mensagens de segurança que usam a segurança de transporte
Esta seção aborda a segurança de transporte do serviço de enfileiramento de mensagens (MSMQ) que você pode usar para proteger as mensagens enviadas para uma fila.  
  
> [!NOTE]
>  Antes de ler este tópico, é recomendável que você leia [conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 A ilustração a seguir fornece um modelo conceitual de comunicação em fila usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Esta ilustração e terminologia é usado para explicar os conceitos de segurança de transporte.  
  
 ![Na fila de diagrama do aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Ao enviar mensagens em fila usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com <xref:System.ServiceModel.NetMsmqBinding>, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem for anexada como um corpo da mensagem do MSMQ. Segurança de transporte protege a mensagem inteira do MSMQ (cabeçalhos de mensagem MSMQ ou propriedades e o corpo da mensagem). Como o corpo da mensagem do MSMQ, usando a segurança de transporte também protege o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem.  
  
 O conceito principal por trás da segurança de transporte é que o cliente precisa atender aos requisitos de segurança para receber a mensagem à fila de destino. Isso é diferente de segurança de mensagem, onde a mensagem é protegida para o aplicativo que recebe a mensagem.  
  
 Uso da segurança de transporte <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> afeta como mensagens MSMQ são protegidas em trânsito entre a fila de transmissão e a fila de destino onde protegidos implica:  
  
-   Assinar a mensagem para garantir que ela não foi violado.  
  
-   Criptografar a mensagem para garantir que ele não pode ser visto ou violado. Isso é recomendado mas opcional.  
  
-   O Gerenciador de filas de destino que identifica o remetente da mensagem de não-repúdio.  
  
 MSMQ, independente de autenticação, a fila de destino tem uma lista de controle de acesso (ACL) para verificar se o cliente tem permissão para enviar a mensagem para a fila de destino. O aplicativo de recebimento também é verificado para permissão para receber a mensagem da fila de destino.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Propriedades de segurança de transporte MSMQ do WCF  
 MSMQ usa a segurança do Windows para autenticação. Ele usa o identificador de segurança (SID) do Windows para identificar o cliente e usa o serviço de diretório do Active Directory como a autoridade de certificação na autenticação do cliente. Isso exige que o MSMQ ser instalado com a integração do Active Directory. Como o SID de domínio do Windows é usado para identificar o cliente, essa opção de segurança só é significativa quando o cliente e o serviço são parte do mesmo domínio do Windows.  
  
 MSMQ também fornece a capacidade de anexar um certificado com a mensagem que não está registrado com o Active Directory. Nesse caso, ele garante que a mensagem foi assinada usando o certificado anexado.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece segurança de transporte essas opções como parte do MSMQ e são a chave dinâmica para segurança de transporte.  
  
 Por padrão, a segurança de transporte é ativada.  
  
 Devido a essas Noções básicas, as seções a seguir propriedades de segurança de transporte detalhes agrupadas com <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Modo de autenticação do MSMQ  
 O <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> determina se deve usar a segurança de domínio do Windows ou uma de segurança externa baseada em certificado para proteger a mensagem. Em ambos os modos de autenticação, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o canal de transporte em fila o `CertificateValidationMode` especificado na configuração do serviço. O modo de validação de certificado Especifica o mecanismo usado para verificar a validade do certificado.  
  
 Quando a segurança de transporte é ativada, a configuração padrão é <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Modo de autenticação de domínio do Windows  
 A opção de usar a segurança do Windows requer a integração do Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>é o modo de segurança de transporte padrão. Quando isso for definido, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel anexa o SID do Windows para a mensagem do MSMQ e usa seu certificado interno obtido do Active Directory. MSMQ usa esse certificado interno para proteger a mensagem. Gerenciador de fila de recebimento usa o Active Directory para pesquisar e localizar um certificado correspondente ao autenticar o cliente e verifica se o SID também corresponde do cliente. Essa etapa de autenticação será executada se um certificado, geradas internamente no caso de `WindowsDomain` modo de autenticação ou gerados externamente no caso de `Certificate` o modo de autenticação é anexado à mensagem, mesmo se a fila de destino não é marcado como exigir autenticação.  
  
> [!NOTE]
>  Ao criar uma fila, você pode marcar a fila como uma fila autenticada para indicar que a fila requer autenticação do cliente enviar mensagens à fila. Isso garante que nenhuma mensagem não autenticadas é aceitos na fila.  
  
 O SID anexado com a mensagem também é usada para verificar em relação a ACL da fila de destino para garantir que o cliente tem autoridade para enviar mensagens à fila.  
  
#### <a name="certificate-authentication-mode"></a>Modo de autenticação de certificado  
 A opção de usar o modo de autenticação de certificado não exige a integração do Active Directory. Na verdade, em alguns casos, como quando o MSMQ está instalado no modo de grupo de trabalho (sem a integração do Active Directory) ou quando usando o protocolo de mensagens confiável SOAP (SRMP) para enviar mensagens à fila, somente o protocolo de transferência <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> funciona.  
  
 Ao enviar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem com <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal não é anexado a um SID do Windows para a mensagem do MSMQ. Como tal, a fila de destino ACL deve permitir `Anonymous` acesso do usuário para enviar para a fila. Gerenciador de fila de recebimento verifica se a mensagem do MSMQ foi assinada com o certificado, mas não realiza nenhuma autenticação.  
  
 O certificado com suas declarações e informações de identidade é populado no <xref:System.ServiceModel.ServiceSecurityContext> pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em fila o canal de transporte. O serviço pode usar essas informações para executar sua própria autenticação do remetente.  
  
### <a name="msmq-protection-level"></a>Nível de proteção do MSMQ  
 O nível de proteção determina como proteger a mensagem do MSMQ para garantir que ele não foi violado. Isso é especificado no <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> propriedade. O valor padrão é <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Nível de proteção de sinal  
 A mensagem do MSMQ é assinada usando o certificado gerado internamente ao usar `WindowsDomain` modo de autenticação ou um certificado gerado externamente ao usar `Certificate` modo de autenticação.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Assinar e criptografar o nível de proteção  
 A mensagem do MSMQ é assinada usando o certificado gerado internamente ao usar `WindowsDomain` modo de autenticação ou certificados gerados externamente ao usar `Certificate` modo de autenticação.  
  
 Além de assinar a mensagem, a mensagem do MSMQ é criptografada usando a chave pública do certificado obtido do Active Directory que pertence ao Gerenciador de fila de recebimento que hospeda a fila de destino. O Gerenciador de fila de envio garante que a mensagem do MSMQ sejam criptografada em trânsito. Gerenciador de fila de recebimento descriptografa a mensagem MSMQ usando a chave privada do certificado interno e armazena a mensagem na fila (se autenticado e autorizado) em texto não criptografado.  
  
> [!NOTE]
>  Para criptografar a mensagem, é necessário ter acesso de Active Directory (`UseActiveDirectory` propriedade <xref:System.ServiceModel.NetMsmqBinding> deve ser definido como `true`) e pode ser usado com ambos <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> e <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Nenhum nível de proteção  
 Isso é indicado quando <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.None>. Isso não pode ser um valor válido para outros modos de autenticação.  
  
> [!NOTE]
>  Se a mensagem do MSMQ é assinada, MSMQ verifica se a mensagem está assinada com o certificado anexado (interno ou externo) independentemente do estado da fila, ou seja, autenticado fila ou não.  
  
### <a name="msmq-encryption-algorithm"></a>Algoritmo de criptografia do MSMQ  
 O algoritmo de criptografia Especifica o algoritmo a ser usado para criptografar a mensagem do MSMQ na conexão. Esta propriedade é usada somente se <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Os algoritmos com suporte são `RC4Stream` e `AES` e o padrão é `RC4Stream`.  
  
 Você pode usar o `AES` algoritmo apenas se o remetente tem MSMQ 4.0 instalado. Além disso, a fila de destino também deve ser hospedada no MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algoritmo de Hash do MSMQ  
 O algoritmo de hash Especifica o algoritmo usado para criar uma assinatura digital da mensagem do MSMQ. Gerenciador de fila de recebimento usa esse mesmo algoritmo para autenticar a mensagem do MSMQ. Esta propriedade é usada somente se <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.Sign> ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Os algoritmos com suporte são `MD5`, `SHA1`, `SHA256`, e `SHA512`. O padrão é `SHA1`.  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento de mensagens](http://msdn.microsoft.com/en-us/ff917e87-05d5-478f-9430-0f560675ece1)  
 [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
