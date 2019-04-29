---
title: Segurança Overview1
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 94f1284e864bc63c321e004ac4a20843b191711d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748532"
---
# <a name="security-overview"></a>Visão geral de segurança
Windows Communication Foundation (WCF) é uma SOAP baseada em mensagens distribuída plataforma de programação e proteger as mensagens entre clientes e serviços é fundamental para proteger os dados. O WCF fornece uma plataforma versátil e interoperável para troca de mensagens seguras, com base na infraestrutura de segurança existente e os padrões de segurança reconhecido para mensagens SOAP.  
  
> [!NOTE]
>  Para obter um guia abrangente para segurança do WCF, consulte [diretrizes de segurança do WCF](https://go.microsoft.com/fwlink/?LinkID=158912).  
  
 WCF usa conceitos que são familiares se você tiver criado aplicativos seguros e distribuídos com tecnologias existentes, como HTTPS, o Windows segurança integrada, ou nomes de usuário e senhas para autenticar usuários. WCF não apenas se integra com infra-estruturas existentes de segurança, mas também estende segurança distribuída além do Windows somente domínios por meio de mensagens seguras de SOAP. Considere uma implementação de mecanismos de segurança existente com a grande vantagem de usar o SOAP como o protocolo, além de protocolos existentes de WCF. Por exemplo, as credenciais que identificam um cliente ou um serviço, como o nome de usuário e senha ou certificados X.509, tem interoperáveis perfis SOAP com base em XML. As mensagens usando esses perfis, são trocadas com segurança, aproveitando as especificações do open, como assinaturas digitais XML e criptografia XML. Para obter uma lista de especificações, consulte [Web Services protocolos com suporte pelas associações de interoperabilidade System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Outro paralelo é o modelo COM (Component Object) na plataforma Windows, que permite que aplicativos distribuídos seguros. COM tem um mecanismo de segurança abrangente no qual o contexto de segurança pode fluir entre os componentes; Esse mecanismo impõe a integridade, confidencialidade e autenticação. No entanto COM não permite várias plataformas, como faz o WCF do sistema de mensagens segura. Usando o WCF, você pode criar serviços e clientes que se estendem de domínios do Windows pela Internet. As mensagens interoperáveis do WCF são essenciais para a compilação dinâmica, serviços orientados pelos negócios que ajudam você a se sentir confiantes na segurança de suas informações.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Benefícios de segurança do Windows Communication Foundation  
 O WCF é uma plataforma de programação distribuída, com base em mensagens SOAP. Usando o WCF, você pode criar aplicativos que funcionam como serviços e clientes de serviço, criar e processar mensagens de um número ilimitado de outros serviços e clientes. Em tal um aplicativo distribuído, as mensagens podem fluir de nó para nó, por meio de firewalls, a Internet e diversos intermediários SOAP. Isso apresenta uma variedade de ameaças de segurança de mensagem. Os exemplos a seguir ilustram algumas ameaças comuns que a segurança do WCF pode ajudar a atenuar ao trocar mensagens entre entidades:  
  
- Observação do tráfego de rede para obter informações confidenciais. Por exemplo, em um cenário de serviços bancários online, um cliente solicita a transferência dos fundos de uma conta para outra. Um usuário mal-intencionado intercepta a mensagem e, mais tarde com o número da conta e senha, executa uma transferência dos fundos de uma conta comprometida.  
  
- Entidades não autorizadas que atua como serviços sem reconhecimento do cliente. Nesse cenário, um usuário mal-intencionado (os invasores) atua como um serviço online e intercepta mensagens do cliente para obter informações confidenciais. Em seguida, o invasor usa os dados roubados para transferir os fundos de uma conta comprometida. Esse ataque também é conhecido uma *ataques de phishing*.  
  
- Alteração de mensagens para obter um resultado diferente de chamador que se destina. Por exemplo, a alteração do número de conta para o qual um depósito é feito permite que os fundos ir para uma conta de invasor.  
  
- Reproduções de hacker em que um hacker incômodo repete a mesma ordem de compra. Por exemplo, uma livraria online recebe centenas de pedidos e envia os livros para um cliente que não tem ordenados-los.  
  
- Incapacidade de um serviço para autenticar um cliente. Nesse caso, o serviço não pode garantir que a pessoa apropriada executada a transação.  
  
 Em resumo, a segurança de transferência fornece as seguintes garantias:  
  
- Autenticação do serviço de ponto de extremidade (Respondente).  
  
- Autenticação de entidade de segurança (iniciador) do cliente.  
  
- Integridade da mensagem.  
  
- Confidencialidade da mensagem.  
  
- Detecção de reprodução.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integração com infra-estruturas existentes de segurança  
 Muitas vezes, implantações de serviço Web tem soluções de segurança em vigor, por exemplo, o Secure Sockets Layer (SSL) ou o protocolo Kerberos. Alguns tirar proveito de uma infra-estrutura de segurança que já foi implantado, como os domínios do Windows usando o Active Directory. Ele geralmente é necessário integrar essas tecnologias já existentes ao avaliar e adotar as mais novas.  
  
 Segurança do WCF se integra com os modelos de segurança de transporte existentes e pode aproveitar a infraestrutura existente para modelos de segurança de transferência mais recentes com base em segurança de mensagem SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integração com os modelos de autenticação existentes  
 Uma parte importante de qualquer modelo de segurança de comunicação é a capacidade de identificar e autenticar as entidades na comunicação. Essas entidades na comunicação usam "identidades digitais" ou as credenciais, para se autenticar com os pontos de comunicação. Como as plataformas de comunicação distribuídos evoluíam, várias autenticação de credenciais e modelos de segurança relacionados foram implementados. Por exemplo, na Internet, o uso de um nome de usuário e senha para identificar os usuários é comum. Na intranet, o uso de um controlador de domínio do Kerberos para fazer backup de usuário e autenticação de serviço está se tornando comuns. Em determinados cenários, tais como entre dois parceiros de negócios, certificados podem ser usados para autenticar mutuamente os parceiros.  
  
 Assim, no mundo dos serviços da Web, onde o mesmo serviço poderá ser exposto aos clientes corporativos internos, bem como para parceiros externos ou clientes de Internet, é importante que a infra-estrutura fornece para integração com segurança esses existente modelos de autenticação. Segurança do WCF dá suporte a uma ampla variedade de tipos de credenciais (modelos de autenticação) incluindo:  
  
- Chamador anônimo.  
  
- Credencial de cliente de nome de usuário.  
  
- Credencial do cliente de certificado.  
  
- Windows (protocolo Kerberos e NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Padrões e interoperabilidade  
 Em um mundo com grandes implantações existentes, a homogeneidade é rara. Plataformas de computação/comunicações distribuída precisam interoperar com as tecnologias que oferecem diferentes fornecedores. Da mesma forma, a segurança também deve ser interoperável.  
  
 Para permitir que os sistemas de segurança interoperável, Active Directory no setor de serviços Web de empresas criaram uma variedade de padrões. Especificamente, quanto à segurança, alguns padrões importantes foram propostos: WS-Security: Segurança de mensagem SOAP (aceitos pelo corpo do padrões OASIS e anteriormente conhecido como WS-Security), WS-Trust, WS-SecureConversation e WS-SecurityPolicy.  
  
 O WCF oferece suporte a uma ampla variedade de cenários de interoperabilidade. O <xref:System.ServiceModel.BasicHttpBinding> classe destina-se no perfil de segurança (BSP) básico e o <xref:System.ServiceModel.WSHttpBinding> classe destina-se os padrões de segurança mais recentes, como WS-Security 1.1 e WS-SecureConversation. Ao aderir a esses padrões, segurança do WCF pode interoperar e integrar com serviços da Web que são hospedados em sistemas operacionais e plataformas diferentes do Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Áreas funcionais de segurança do WCF  
 Segurança do WCF é dividida em três áreas funcionais: transferir a segurança, controle de acesso e auditoria. Resumidamente, as seções a seguir abordam essas áreas e fornecem links para obter mais informações.  
  
### <a name="transfer-security"></a>Segurança de transferência  
 Segurança de transferência abrange três principais funções de segurança: autenticação, confidencialidade e integridade. *Integridade* é a capacidade de detectar se uma mensagem foi violada. *Confidencialidade* é a capacidade de manter uma mensagem não pode ser lido por qualquer pessoa que não seja o destinatário pretendido; isso é feito pelo uso de criptografia. *Autenticação* é a capacidade de verificar uma identidade reivindicada. Juntas, essas três funções ajudam a garantir que as mensagens chegam com segurança de um ponto para outro.  
  
#### <a name="transport-and-message-security-modes"></a>Transporte e modos de segurança de mensagem  
 Dois mecanismos principais são usados para implementar a segurança de transferência no WCF: *transporte* modo de segurança e *mensagem* modo de segurança.  
  
- *Modo de segurança de transporte* usa um protocolo de nível de transporte, como HTTPS, para fins de segurança de transferência. O modo de transporte tem a vantagem de ser amplamente adotada, disponível em muitas plataformas e computacionalmente menos complexo. No entanto, ele tem a desvantagem de proteger mensagens apenas de ponto a ponto.  
  
- *Modo de segurança de mensagem*, por outro lado, usa WS-Security (e outras especificações) para implementar a segurança de transferência. Como a segurança da mensagem é aplicada diretamente para as mensagens SOAP e está contida dentro de envelopes SOAP, junto com os dados de aplicativo, ele tem a vantagem de ser transporte independente de protocolo, mais extensível e garantindo segurança de ponta a ponta (em vez de ponto a ponto); ele tem a desvantagem de que está sendo várias vezes mais lento do que o modo de segurança de transporte porque tem que lidar com a natureza XML das mensagens SOAP.  
  
 Para obter mais informações sobre essas diferenças, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Um terceiro modo de segurança usa ambos os modos anteriores e traz vantagens de ambos. Esse modo é chamado `TransportWithMessageCredential`. Nesse modo, segurança de mensagem é usada para autenticar o cliente e segurança de transporte é usada para autenticar o servidor e fornecer a integridade e confidencialidade da mensagem. Graças a isso, o `TransportWithMessageCredential` modo de segurança é quase tão rápido quanto o modo de segurança de transporte e oferece extensibilidade de autenticação de cliente da mesma forma como a segurança de mensagem. No entanto, ao contrário do modo de segurança de mensagem, ele não fornece segurança de ponta a ponta completa.  
  
### <a name="access-control"></a>Controle de acesso  
 *Controle de acesso* também é conhecido como autorização. *Autorização* permite que diferentes usuários tenham privilégios diferentes para exibir os dados. Por exemplo, como arquivos de recursos humanos da empresa contêm dados confidenciais de funcionários, somente gerentes são permitidos para exibir dados de funcionários. Além disso, os gerentes podem exibir apenas os dados para seus relatórios diretos. Nesse caso, o controle de acesso baseia-se na função ("manager"), bem como a identidade específica do Gerenciador (para impedir que um gerente de examinar os registros de funcionário do gerente de outra).  
  
 No WCF, os recursos de controle de acesso são fornecidos por meio da integração com o common language runtime (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> e por meio de um conjunto de APIs, conhecido como o *modelo de identidade*. Para obter detalhes sobre o controle de acesso e autorização baseada em declarações, consulte [estendendo segurança](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Auditoria  
 *Auditoria* é o registro em log de eventos de segurança para o log de eventos do Windows. Você pode registrar eventos relacionados à segurança, como falhas de autenticação (ou sucessos). Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Para obter detalhes de programação, consulte [como: Auditar eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Protegendo serviços](../../../../docs/framework/wcf/securing-services.md)
- [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
- [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Diretrizes e práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Configurando serviços usando arquivos de configuração](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md)
- [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
