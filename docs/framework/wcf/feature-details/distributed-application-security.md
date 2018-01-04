---
title: "Segurança de aplicativos distribuídos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: "32"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1e67c5da534e7b35d4d27c0164d9389c8afe252b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="distributed-application-security"></a>Segurança de aplicativos distribuídos
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]segurança é dividida em três áreas funcionais principais: transferir a segurança, controle de acesso e auditoria. Segurança de transferência fornece autenticação, integridade e confidencialidade. Transferência de segurança é fornecida por um dos seguintes: segurança, segurança de mensagem de transporte ou `TransportWithMessageCredential`.  
  
 Para obter uma visão geral de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança de mensagem, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]duas partes da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança, consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) e [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Cenários de segurança de transferência  
 Cenários comuns que empregam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transferência segurança incluem o seguinte:  
  
-   Transferência segura usando o Windows. Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e serviço são implantados em um domínio do Windows (ou uma floresta do Windows). As mensagens de contenham dados pessoais, para que os requisitos incluem a autenticação mútua do cliente e serviço, integridade e confidencialidade da mensagem. Além disso, é necessária uma prova que uma transação específica ocorreu, por exemplo, o receptor da mensagem deve registrar as informações de assinatura.  
  
-   Transferência segura usando `UserName` e HTTPS. Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e o serviço devem ser desenvolvidos para funcionar com a Internet. Autenticam as credenciais do cliente em relação a um banco de dados de pares de nome/senha do usuário. O serviço é implantado em um endereço HTTPS usando um certificado Secure Sockets Layer (SSL). Como as mensagens passam pela Internet, o cliente e o serviço precisam ser autenticadas mutuamente e confidencialidade e a integridade as mensagens devem ser preservadas durante a transferência.  
  
-   Transferência segura usando certificados. Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e o serviço precisam ser desenvolvidos para trabalhar na Internet pública. O cliente e o serviço têm certificados que podem ser usados para proteger as mensagens. O cliente e o serviço usem a Internet para se comunicar entre si e para executar transações de alto valor que exigem a autenticação mútua, confidencialidade e integridade da mensagem.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Autenticação, integridade e confidencialidade  
 Três funções — confidencialidade, integridade e a autenticação — juntos são chamados de segurança de transferência. Segurança de transferência fornece as funções que ajudam a mitigar as ameaças para um aplicativo distribuído. A tabela a seguir descreve brevemente as três funções que compõem a segurança de transferência.  
  
|Função|Descrição|  
|--------------|-----------------|  
|Integridade|*Integridade* é a garantia de que os dados são completas e precisas, principalmente depois que ele percorrida a partir de um ponto para outro e, possivelmente foram lido por vários atores. Integridade deve ser mantida para evitar a violação de dados e normalmente é obtida com a assinatura digital de uma mensagem.|  
|Confidencialidade|*Confidencialidade* é a garantia de que uma mensagem não foi lido por qualquer pessoa que não seja o leitor pretendido. Por exemplo, um número de cartão de crédito deve ser mantido confidencial quando eles são enviados pela Internet. Confidencialidade geralmente é fornecida pela criptografia de dados usando um esquema de chave pública/privada de chave.|  
|Autenticação|*Autenticação* é a verificação de uma identidade reivindicada. Por exemplo, ao usar uma conta bancária, é fundamental que somente o proprietário real da conta poderá retirar fundos. Autenticação pode ser fornecida por vários meios. Um método comum é o sistema de senha do usuário. Um segundo é o uso de um certificado x. 509 que é fornecido por terceiros.|  
  
## <a name="security-modes"></a>Modos de segurança  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tem vários modos de segurança de transferência, que são descritos na tabela a seguir.  
  
|Modo|Descrição|  
|----------|-----------------|  
|Nenhum|Nenhuma segurança é fornecida na camada de transporte ou na camada de mensagem. Nenhuma das associações predefinidas use este modo por padrão, exceto o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento ou, ao usar o código, a <xref:System.ServiceModel.BasicHttpBinding> classe.|  
|Transporte|Usa um transporte seguro, como HTTP, para autenticação mútua, integridade e confidencialidade.|  
|Mensagem|Usa a segurança de mensagem SOAP para autenticação mútua, integridade e confidencialidade. Mensagens SOAP são protegidas de acordo com os padrões WS-Security.|  
|Modo misto|Usa segurança de transporte para autenticação de servidor, integridade e confidencialidade. Usa a segurança (WS-Security e outros padrões) para autenticação de cliente de mensagens.<br /><br /> (Esta enumeração para este modo é `TransportWithMessageCredential`.)|  
|Ambos|Executa a proteção e a autenticação em ambos os níveis. Esse modo está disponível apenas no [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) elemento.|  
  
## <a name="credentials-and-transfer-security"></a>As credenciais e segurança de transferência  
 Um *credencial* são dados que são exibidos para estabelecer uma identidade reivindicada ou recursos. Apresentar uma credencial envolve apresentar os dados e a prova de posse dos dados. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte a uma variedade de tipos de credenciais em níveis de segurança de transporte e de mensagem. Você pode especificar um tipo de credencial para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação.  
  
 Em muitos países ou regiões, de motorista uma carteira é um exemplo de uma credencial. Uma licença contém dados que representa uma identidade e recursos. Ele contém uma prova de posse na forma de imagem do detentor. A licença é emitida por uma autoridade confiável, geralmente um departamento de licenciamento governamental. A licença é fechada e pode conter um holograma, mostrando que ele não foi violado ou falsificado.  
  
 Por exemplo, considere dois tipos de credenciais com suporte no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: credenciais de certificado de nome de usuário e (x. 509).  
  
 Para a credencial de nome de usuário, o nome de usuário representa a identidade reivindicada e a senha apresenta a prova de posse. Nesse caso, a autoridade confiável é o sistema valida o nome de usuário e senha.  
  
 Na credencial do certificado, o nome do assunto, nome alternativo da entidade ou campos específicos no certificado podem ser usados para representar a identidade reivindicada e/ou recursos. Prova de posse dos dados na credencial é estabelecida usando a chave privada associada para gerar uma assinatura.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]programação de segurança de transferência e especificar credenciais, consulte [associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) e [comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Tipos de credenciais de cliente de transporte  
 A tabela a seguir mostra os possíveis valores usados ao criar um aplicativo que usa a segurança de transferência. Você pode usar esses valores no código ou configurações de associação.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar credenciais. Isso se traduz em um cliente anônimo.|  
|Basic|Especifica autenticação básica.  Para obter mais informações, consulte RFC2617, "[autenticação HTTP: Basic e a autenticação Digest](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Digest|Especifica a autenticação Digest.  Para obter mais informações, consulte RFC2617, "[autenticação HTTP: Basic e a autenticação Digest](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Especifica a autenticação do Windows usando a negociação SSPI em um domínio do Windows.<br /><br /> Negociação SSPI resulta em usando o protocolo Kerberos ou LanMan NT (NTLM).|  
|Windows|Especifica a autenticação do Windows usando SSPI em um domínio do Windows. Escolhe o SSPI do protocolo Kerberos ou NTLM como serviço de autenticação.<br /><br /> SSPI tenta protocolo Kerberos primeiro; Se isso falhar, em seguida, ele usará o NTLM.|  
|certificado|Executa a autenticação de cliente usando um certificado x. 509 normalmente.|  
  
### <a name="message-client-credential-types"></a>Tipos de credencial de cliente de mensagem  
 A tabela a seguir mostra os possíveis valores usados ao criar um aplicativo que usa a segurança de mensagem. Você pode usar esses valores no código ou configurações de associação.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Permite que o serviço interaja com clientes anônimos.|  
|Windows|Permite que as trocas de mensagens SOAP ocorrer sob o contexto autenticado de uma credencial do Windows. Usa o mecanismo de negociação de SSPI para escolher o protocolo Kerberos ou NTLM como um serviço de autenticação.|  
|Nome de usuário|Permite que o serviço exigir que o cliente seja autenticado com uma credencial de nome de usuário. Observe que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não permite qualquer operações criptográficas com o nome de usuário, como gerar uma assinatura ou criptografia de dados. Como tal, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] impõe que o transporte é protegido ao usar as credenciais de nome de usuário.|  
|certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Permite que o serviço exigir que o cliente seja autenticado usando um [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Credenciais de programação  
 Para cada um dos tipos de credencial de cliente, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação permite que você especifique os valores de credencial e validadores de credencial usando comportamentos de serviço e comportamentos do canal.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]a segurança tem dois tipos de credenciais: comportamentos de credencial e comportamentos de credencial do canal de serviço. Credencial comportamentos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] especificar os dados reais, ou seja, as credenciais usadas para atender aos requisitos de segurança expressados por meio de associações. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uma classe de cliente é o componente de tempo de execução que converte entre a invocação de operação e mensagens. Todos os clientes herdam o <xref:System.ServiceModel.ClientBase%601> classe. O <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade na classe base permite que você especifique vários valores de credenciais de cliente.  
  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], comportamentos de serviço são atributos aplicados para a classe que implementa um contrato de serviço (interface) para controlar programaticamente o serviço. O <xref:System.ServiceModel.Description.ServiceCredentials> classe permite que você especifique certificados para configurações de validação de cliente e a credencial de serviço para vários tipos de credencial de cliente.  
  
### <a name="negotiation-model-for-message-security"></a>Modelo de negociação de segurança de mensagem  
 O modo de segurança de mensagem permite que você execute a segurança de transferência para que a credencial de serviço é configurada no cliente fora da banda. Por exemplo, se você estiver usando um certificado armazenado no repositório de certificados do Windows, você deve usar uma ferramenta como um snap-in do Console de gerenciamento Microsoft (MMC).  
  
 O modo de segurança de mensagem também permite que você execute a segurança de transferência para que a credencial de serviço é trocada com o cliente como parte de uma negociação inicial. Para habilitar a negociação, defina o <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> propriedade `true`.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
