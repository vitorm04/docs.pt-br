---
title: Segurança de aplicativos distribuídos
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dbc06afd4695b85f426fad2859b4c6d4b6684d6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402907"
---
# <a name="distributed-application-security"></a>Segurança de aplicativos distribuídos
Segurança do Windows Communication Foundation (WCF) é dividida em três áreas funcionais principais: segurança, controle de acesso e auditoria de transferência. Segurança de transferência fornece integridade, confidencialidade e autenticação. Segurança de transferência é fornecida por um dos seguintes: segurança, segurança de mensagem de transporte ou `TransportWithMessageCredential`.  
  
 Para uma visão geral de segurança de mensagem do WCF, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). Para obter mais informações sobre os outros dois conjuntos de segurança do WCF, consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) e [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Cenários de segurança de transferência  
 Cenários comuns que utilizam segurança de transferência WCF incluem o seguinte:  
  
-   Transferência segura usando o Windows. Um cliente WCF e serviço são implantadas em um domínio do Windows (ou uma floresta do Windows). As mensagens contêm dados pessoais, portanto, os requisitos incluem a autenticação mútua do cliente e serviço, integridade de mensagens e confidencialidade da mensagem. Além disso, é necessária uma prova que uma transação específica ocorreu, por exemplo, o receptor da mensagem deve registrar as informações de assinatura.  
  
-   Transferência segura usando `UserName` e HTTPS. Um cliente WCF e serviço precisam ser desenvolvidos para trabalhar com a Internet. As credenciais de cliente autenticam em relação a um banco de dados de pares de nome/senha do usuário. O serviço é implantado em um endereço HTTPS usando um certificado confiável do Secure Sockets Layer (SSL). Como as mensagens viajam pela Internet, o cliente e o serviço precisam ser mutuamente autenticadas e confidencialidade e a integridade das mensagens devem ser preservados durante a transferência.  
  
-   Transferência segura usando certificados. Um cliente WCF e serviço precisam ser desenvolvidos para trabalhar na Internet pública. O cliente e serviço têm certificados que podem ser usados para proteger as mensagens. O cliente e o serviço usarem a Internet para se comunicar entre si e para executar transações de alto valor que exigem a autenticação mútua, confidencialidade e integridade de mensagens.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integridade, confidencialidade e autenticação  
 Três funções — integridade, confidencialidade e autenticação — juntos são chamados de segurança de transferência. Segurança de transferência fornece as funções que ajudam a mitigar as ameaças para um aplicativo distribuído. A tabela a seguir descreve resumidamente as três funções que compõem a segurança de transferência.  
  
|Função|Descrição|  
|--------------|-----------------|  
|Integridade|*Integridade* é a garantia de que os dados estão completas e precisas, especialmente depois que ele percorrida a partir de um ponto para outro e possivelmente foram lido pela vários atores. Integridade deve ser mantida para evitar a violação de dados e geralmente é obtida com a assinatura digital de uma mensagem.|  
|Confidencialidade|*Confidencialidade* é a garantia de que uma mensagem não foi lido por qualquer pessoa que não seja o leitor pretendido. Por exemplo, um número de cartão de crédito deve ser mantido confidencial conforme eles são enviados pela Internet. Confidencialidade geralmente é fornecida pela criptografia de dados usando um esquema de chave pública/privada de chave.|  
|Autenticação|*Autenticação* é a verificação de uma identidade reivindicada. Por exemplo, ao usar uma conta bancária, é imperativo que somente o proprietário real da conta tenha permissão para retirar os fundos. A autenticação pode ser fornecida por uma variedade de meios. Um método comum é o sistema do usuário e senha. Um segundo é o uso de um certificado X.509 que é fornecido por terceiros.|  
  
## <a name="security-modes"></a>Modos de segurança  
 O WCF possui vários modos de segurança de transferência, que são descritos na tabela a seguir.  
  
|Modo|Descrição|  
|----------|-----------------|  
|Nenhum|Nenhuma segurança é fornecida na camada de transporte ou na camada de mensagem. Nenhuma das associações predefinidas usam este modo por padrão, exceto o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento ou, ao usar o código, o <xref:System.ServiceModel.BasicHttpBinding> classe.|  
|Transporte|Usa um transporte seguro, como HTTPS para integridade, confidencialidade e autenticação mútua.|  
|Mensagem|Usa a segurança de mensagem SOAP para integridade, confidencialidade e autenticação mútua. As mensagens SOAP são protegidas de acordo com os padrões WS-Security.|  
|Modo misto|Usa segurança de transporte para autenticação de servidor, a confidencialidade e integridade. Usa a segurança (WS-Security e outros padrões) para autenticação de cliente de mensagem.<br /><br /> (Esta enumeração para este modo é `TransportWithMessageCredential`.)|  
|Ambos|Executa a autenticação em ambos os níveis e proteção. Esse modo está disponível apenas na [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) elemento.|  
  
## <a name="credentials-and-transfer-security"></a>As credenciais e segurança de transferência  
 Um *credencial* são dados que são apresentados para estabelecer uma identidade reivindicada ou recursos. Apresentar uma credencial envolve a apresentar os dados e a prova de posse dos dados. O WCF oferece suporte a uma variedade de tipos de credenciais nos níveis de segurança de transporte e de mensagem. Você pode especificar um tipo de credencial para uma associação do WCF.  
  
 Em muitos países ou regiões, de motorista uma carteira é um exemplo de uma credencial. Uma licença contém dados que representa a identidade e recursos de um. Ele contém uma prova de posse na forma de imagem do detentor. A licença é emitida por uma autoridade confiável, normalmente, um departamento de licenciamento governamental. A licença é lacrada e pode conter um holograma, mostrando que ele não foi adulterado ou falsificado.  
  
 Por exemplo, considere dois tipos de credenciais com suporte no WCF: credenciais de certificado de nome de usuário e (x. 509).  
  
 Para a credencial de nome de usuário, o nome de usuário representa a identidade reivindicada e a senha apresenta a prova de posse. Nesse caso, a autoridade confiável é o sistema que valida o nome de usuário e senha.  
  
 Na credencial de certificado, o nome da entidade, o nome alternativo da entidade ou a campos específicos no certificado podem ser usados para representar a identidade reivindicada e/ou recursos. Prova de posse dos dados em que a credencial é estabelecida usando a chave privada associada para gerar uma assinatura.  
  
 Para obter mais informações sobre programação de segurança de transferência e especificar credenciais, consulte [associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) e [comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Tipos de credencial de cliente de transporte  
 A tabela a seguir mostra os valores possíveis usados ao criar um aplicativo que usa a segurança de transferência. Você pode usar esses valores no código ou configurações de associação.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar nenhuma credencial. Isso se traduz em um cliente anônimo.|  
|Basic|Especifica autenticação básica.  Para obter mais informações, consulte RFC2617, "[autenticação HTTP: autenticação básica e Digest](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Digest|Especifica a autenticação Digest.  Para obter mais informações, consulte RFC2617, "[autenticação HTTP: autenticação básica e Digest](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Especifica a autenticação do Windows usando a negociação SSPI em um domínio do Windows.<br /><br /> A negociação SSPI resulta em usando o protocolo Kerberos ou LanMan NT (NTLM).|  
|Windows|Especifica a autenticação do Windows usando o SSPI em um domínio do Windows. Escolhe o SSPI do protocolo Kerberos ou NTLM como serviço de autenticação.<br /><br /> SSPI tenta o protocolo Kerberos primeiro; Se isso falhar, ele usa NTLM.|  
|Certificado|Executa a autenticação de cliente usando um certificado, normalmente x. 509.|  
  
### <a name="message-client-credential-types"></a>Tipos de credencial de cliente de mensagem  
 A tabela a seguir mostra os valores possíveis usados ao criar um aplicativo que usa a segurança de mensagem. Você pode usar esses valores no código ou configurações de associação.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Permite que o serviço interaja com clientes anônimos.|  
|Windows|Permite que as trocas de mensagens SOAP ocorrer sob o contexto autenticado de uma credencial do Windows. Usa o mecanismo de negociação SSPI para escolher do protocolo Kerberos ou NTLM como um serviço de autenticação.|  
|Nome de usuário|Permite que o serviço exigir que o cliente seja autenticado com uma credencial de nome de usuário. Observe que o WCF não permite todas as operações criptográficas com o nome de usuário, como gerar uma assinatura ou criptografia de dados. Como tal, o WCF impõe que o transporte é protegido ao usar as credenciais de nome de usuário.|  
|Certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Permite que o serviço exigir que o cliente seja autenticado usando um [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>As credenciais de programação  
 Para cada um dos tipos de credenciais de cliente, o modelo de programação WCF permite que você especifique os valores de credencial e validadores de credencial usando comportamentos de serviço e comportamentos do canal.  
  
 Segurança do WCF tem dois tipos de credenciais: os comportamentos de credencial do canal e comportamentos de credencial de serviço. Comportamentos de credencial no WCF especificar os dados reais, ou seja, as credenciais usadas para atender aos requisitos de segurança expressados por meio de associações. No WCF, uma classe de cliente é o componente de tempo de execução que converte entre as mensagens e invocação de operação. Todos os clientes herdam o <xref:System.ServiceModel.ClientBase%601> classe. O <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade na classe base permite que você especifique vários valores de credenciais de cliente.  
  
 No WCF, os comportamentos de serviço são atributos aplicados à classe que implementa um contrato de serviço (interface) para controlar programaticamente o serviço. O <xref:System.ServiceModel.Description.ServiceCredentials> classe permite que você especificar certificados para configurações de validação de credenciais e de cliente de serviço para vários tipos de credencial de cliente.  
  
### <a name="negotiation-model-for-message-security"></a>Modelo de negociação de segurança de mensagem  
 O modo de segurança de mensagem permite que você execute a segurança de transferência para que a credencial de serviço seja configurada no cliente fora da banda. Por exemplo, se você estiver usando um certificado armazenado no repositório de certificados do Windows, você deve usar uma ferramenta como um snap-in do Console de gerenciamento Microsoft (MMC).  
  
 O modo de segurança de mensagem também permite que você execute a segurança de transferência para que a credencial de serviço é trocada com o cliente como parte de uma negociação inicial. Para habilitar a negociação, defina as <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> propriedade para `true`.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
