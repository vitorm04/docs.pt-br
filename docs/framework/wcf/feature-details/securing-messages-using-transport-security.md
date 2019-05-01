---
title: Mensagens de segurança que usam a segurança de transporte
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
ms.openlocfilehash: f32e932bb6616911baa8991cb46a5940c8d285ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990958"
---
# <a name="securing-messages-using-transport-security"></a>Mensagens de segurança que usam a segurança de transporte
Esta seção aborda a segurança de transporte de enfileiramento de mensagens (MSMQ) que você pode usar para proteger as mensagens enviadas para uma fila.  
  
> [!NOTE]
>  Antes de ler este tópico, é recomendável que você leia [conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 A ilustração a seguir fornece um modelo conceitual de comunicação em fila usando o Windows Communication Foundation (WCF). Esta ilustração e a terminologia é usado para explicar conceitos de segurança de transporte.  
  
 ![Na fila de diagrama de aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Ao enviar mensagens na fila usando o WCF com <xref:System.ServiceModel.NetMsmqBinding>, a mensagem do WCF é anexada como um corpo da mensagem do MSMQ. Segurança de transporte protege a mensagem inteira do MSMQ (cabeçalhos de mensagem do MSMQ ou as propriedades e o corpo da mensagem). Como é o corpo da mensagem do MSMQ, também usando a segurança de transporte protege a mensagem do WCF.  
  
 O conceito fundamental por trás da segurança de transporte é que o cliente deve atender aos requisitos de segurança para obter a mensagem à fila de destino. Isso é diferente de segurança da mensagem, em que a mensagem é protegida para o aplicativo que recebe a mensagem.  
  
 Segurança de transporte usando <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> afeta como mensagens MSMQ são protegidas em trânsito entre a fila de transmissão e a fila de destino onde protegido implica:  
  
- Assinar a mensagem para assegurar que ele não seja violado.  
  
- Criptografar a mensagem para garantir que não podem ser visto ou violado. Isso é opcional mas recomendado.  
  
- O Gerenciador de fila de destino que identifica o remetente da mensagem de não-repúdio.  
  
 No MSMQ, independente de autenticação, a fila de destino tem uma lista de controle de acesso (ACL) para verificar se o cliente tem permissão para enviar a mensagem à fila de destino. O aplicativo de recebimento também é verificado para a permissão receber a mensagem da fila de destino.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Propriedades de segurança do transporte MSMQ do WCF  
 MSMQ usa a segurança do Windows para autenticação. Ele usa o identificador de segurança (SID) do Windows para identificar o cliente e usa o serviço de diretório do Active Directory como a autoridade de certificação ao autenticar o cliente. Isso requer que o MSMQ ser instalado com a integração do Active Directory. Como o SID de domínio do Windows é usado para identificar o cliente, essa opção de segurança só é significativa quando o cliente e o serviço fazem parte do mesmo domínio do Windows.  
  
 MSMQ também fornece a capacidade de anexar um certificado com a mensagem que não está registrado com o Active Directory. Nesse caso, ele garante que a mensagem foi assinada usando o certificado anexado.  
  
 O WCF fornece essas duas opções como parte da segurança do transporte MSMQ e são o pivô central de segurança de transporte.  
  
 Por padrão, a segurança de transporte é ativada.  
  
 Dada a estas noções básicas, as seções a seguir propriedades de segurança de transporte de detalhes fornecidas com <xref:System.ServiceModel.NetMsmqBinding> e <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Modo de autenticação do MSMQ  
 O <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> determina se deve usar a segurança de domínio do Windows ou um segurança externa baseada em certificado para proteger a mensagem. Em ambos os modos de autenticação, o canal de transporte enfileiradas de WCF usa o `CertificateValidationMode` especificado na configuração do serviço. O modo de validação de certificado Especifica o mecanismo usado para verificar a validade do certificado.  
  
 Quando a segurança de transporte é ativada, a configuração padrão é <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Modo de autenticação de domínio do Windows  
 A opção de usar a segurança do Windows requer a integração do Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> é o modo de segurança de transporte padrão. Quando isso for definido, o canal do WCF anexa o SID do Windows para a mensagem do MSMQ e usa seu certificado interno obtido do Active Directory. MSMQ usa esse certificado interno para proteger a mensagem. Gerenciador de fila de recebimento usa o Active Directory para pesquisar e encontrar um certificado correspondente para autenticar o cliente e verifica se o SID também corresponde do cliente. Essa etapa de autenticação será executada se um certificado, geradas internamente no caso de `WindowsDomain` modo de autenticação ou gerados externamente no caso de `Certificate` o modo de autenticação é anexado à mensagem, mesmo se a fila de destino não é marcado como exigindo autenticação.  
  
> [!NOTE]
>  Ao criar uma fila, você pode marcar a fila como uma fila autenticada para indicar que a fila requer autenticação do cliente enviar mensagens à fila. Isso garante que nenhuma mensagem não autenticadas é aceitos na fila.  
  
 O SID é anexado com a mensagem também é usada para verificar em relação a ACL da fila de destino para garantir que o cliente tem autoridade para enviar mensagens à fila.  
  
#### <a name="certificate-authentication-mode"></a>Modo de autenticação de certificado  
 A opção de usar o modo de autenticação de certificado não requer integração do Active Directory. Na verdade, em alguns casos, como quando o MSMQ está instalado no modo de grupo de trabalho (sem a integração do Active Directory) ou quando usando o Reliable Messaging protocolo SRMP (SOAP) para enviar mensagens à fila, somente o protocolo de transferência <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> funciona.  
  
 Ao enviar uma mensagem do WCF com <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, o canal do WCF não for anexado a um SID do Windows para a mensagem do MSMQ. Como tal, a fila de destino ACL deve permitir `Anonymous` acesso do usuário para enviar para a fila. Gerenciador de fila de recebimento verifica se a mensagem do MSMQ foi assinada com o certificado, mas não realiza qualquer autenticação.  
  
 O certificado com suas declarações e informações de identidade é preenchido no <xref:System.ServiceModel.ServiceSecurityContext> pelo canal de transporte em fila do WCF. O serviço pode usar essas informações para executar sua própria autenticação do remetente.  
  
### <a name="msmq-protection-level"></a>Nível de proteção do MSMQ  
 O nível de proteção determina como proteger a mensagem do MSMQ para garantir que ele não seja violado. Ele é especificado no <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> propriedade. O valor padrão é <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Nível de proteção de entrada  
 A mensagem do MSMQ é assinada usando o certificado gerado internamente ao usar `WindowsDomain` modo de autenticação ou um certificado gerado externamente ao usar `Certificate` modo de autenticação.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Assinar e criptografar o nível de proteção  
 A mensagem do MSMQ é assinada usando o certificado gerado internamente ao usar `WindowsDomain` modo de autenticação ou certificados gerados externamente ao usar `Certificate` modo de autenticação.  
  
 Além de se a mensagem, a mensagem do MSMQ é criptografada usando a chave pública do certificado obtido do Active Directory que pertence ao Gerenciador de fila de recebimento que hospeda a fila de destino. O Gerenciador de fila de envio garante que a mensagem do MSMQ é criptografada em trânsito. Gerenciador de fila de recebimento descriptografa a mensagem do MSMQ usando a chave privada do seu certificado interno e armazena a mensagem na fila (se autenticado e autorizado) em texto não criptografado.  
  
> [!NOTE]
>  Para criptografar a mensagem, o acesso do Active Directory é necessário (`UseActiveDirectory` propriedade de <xref:System.ServiceModel.NetMsmqBinding> deve ser definida como `true`) e podem ser usados com ambos <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> e <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Nenhum nível de proteção  
 Isso é indicado quando <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.None>. Isso não pode ser um valor válido para outros modos de autenticação.  
  
> [!NOTE]
>  Se a mensagem do MSMQ é assinada, MSMQ verifica se a mensagem for assinada com o certificado anexado (interno ou externo) independentemente do estado da fila, autenticado ou seja, a fila ou não.  
  
### <a name="msmq-encryption-algorithm"></a>Algoritmo de criptografia do MSMQ  
 O algoritmo de criptografia Especifica o algoritmo a ser usado para criptografar a mensagem do MSMQ durante a transmissão. Essa propriedade é usada somente se <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Os algoritmos compatíveis são `RC4Stream` e `AES` e o padrão é `RC4Stream`.  
  
 Você pode usar o `AES` algoritmo somente se o remetente tem MSMQ 4.0 instalado. Além disso, a fila de destino também deve ser hospedada no MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algoritmo de Hash do MSMQ  
 O algoritmo de hash Especifica o algoritmo usado para criar uma assinatura digital da mensagem do MSMQ. Gerenciador de fila de recebimento usa esse mesmo algoritmo para autenticar a mensagem do MSMQ. Essa propriedade é usada somente se <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> é definido como <xref:System.Net.Security.ProtectionLevel.Sign> ou <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Os algoritmos com suporte são `MD5`, `SHA1`, `SHA256` e `SHA512`. O padrão é `SHA1`.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de filas](queues-overview.md)
- [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
