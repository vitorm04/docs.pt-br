---
title: Overview1 de segurança
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
caps.latest.revision: 37
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: a50b3d3ec2a99d53bc7d5817f3ed530ef92d474b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="security-overview"></a>Visão geral de segurança
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é uma SOAP baseada em mensagens distribuídas programação plataforma e mensagens entre clientes e serviços de segurança que são essencial para proteger dados. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Fornece uma plataforma versátil e interoperável para a troca de mensagens de segurança com base na infraestrutura de segurança existente e os padrões de segurança reconhecido para mensagens SOAP.  
  
> [!NOTE]
>  Para obter um guia abrangente para segurança do WCF, consulte [orientações de segurança do WCF](http://go.microsoft.com/fwlink/?LinkID=158912).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa conceitos que são familiares se você tiver criado aplicativos distribuídos seguros com tecnologias existentes como HTTPS, o Windows segurança integrada, ou nomes de usuário e senhas para autenticar usuários. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não apenas integra infra-estruturas de segurança, mas também estende segurança distribuído além domínios somente do Windows usando mensagens SOAP seguras. Considere [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uma implementação de mecanismos de segurança existentes com a principal vantagem de usar o SOAP como o protocolo além de protocolos existentes. Por exemplo, as credenciais que identificam um cliente ou um serviço, como nome de usuário e senha ou certificados x. 509, tem interoperáveis perfis SOAP com base em XML. As mensagens usando esses perfis, são trocadas com segurança, aproveitando as especificações do open como assinaturas digitais XML e XML. Para obter uma lista de especificações, consulte [Web Services dá suporte para protocolos associações de interoperabilidade System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Outro paralelo é o modelo COM (Component Object) na plataforma Windows, que permite que os aplicativos distribuídos, seguros. COM tem um mecanismo de segurança abrangente no qual o contexto de segurança pode fluir entre componentes. Esse mecanismo impõe a autenticação, integridade e confidencialidade. No entanto, COM não habilitar a plataforma cruzada, proteger mensagens como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does. Usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você pode criar serviços e clientes que variam de domínios do Windows com a Internet. As mensagens interoperáveis de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são essenciais para a criação dinâmica orientados aos negócios serviços que ajudam você tenha confiança na segurança das suas informações.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Benefícios de segurança do Windows Communication Foundation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é uma plataforma de programação distribuída com base nas mensagens SOAP. Usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você pode criar aplicativos que funcionam como os serviços e clientes de serviço, criar e processar mensagens de um número ilimitado de outros serviços e clientes. Em tal aplicativo distribuído, as mensagens podem fluir de nó para nó, por meio de firewalls, para a Internet e várias intermediários SOAP. Isso apresenta uma variedade de ameaças à segurança de mensagem. Os exemplos a seguir ilustram algumas comum ameaças que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança pode ajudar a reduzir para trocar mensagens entre entidades:  
  
-   Observação do tráfego de rede para obter informações confidenciais. Por exemplo, em um cenário de transações bancárias online, um cliente solicita a transferência de fundos de uma conta para outra. Um usuário mal-intencionado intercepta a mensagem e, posteriormente com o número da conta e senha, executa uma transferência de fundos da conta comprometida.  
  
-   Entidades autorizadas atuando como serviços sem reconhecimento do cliente. Nesse cenário, um usuário mal-intencionado (o invasor) atua como um serviço online e intercepta as mensagens do cliente para obter informações confidenciais. O invasor usa dados roubados transferir fundos da conta comprometida. Esse ataque também é conhecido um *ataques de phishing*.  
  
-   Alteração de mensagens para obter um resultado diferente que o chamador que se destina. Por exemplo, alterar o número da conta para o qual um depósito é feito permite que os fundos ir para uma conta do invasor.  
  
-   Repetições de hacker em que um hacker incômodo repete a mesma ordem de compra. Por exemplo, uma livraria online recebe centenas de pedidos e envia os manuais para um cliente que não tem ordenados-los.  
  
-   Incapacidade de um serviço para autenticar um cliente. Nesse caso, o serviço não pode garantir que a pessoa apropriada executada a transação.  
  
 Em resumo, a segurança de transferência fornece as seguintes garantias:  
  
-   Autenticação do serviço de ponto de extremidade (participante).  
  
-   Autenticação do cliente principal (iniciador).  
  
-   Integridade da mensagem.  
  
-   Confidencialidade da mensagem.  
  
-   Detecção de repetição.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integração com infra-estruturas de segurança existentes  
 Geralmente, implantações de serviço da Web têm soluções de segurança existentes no local, por exemplo, o protocolo (SSL) ou o protocolo Kerberos. Alguns se beneficiar de uma infraestrutura de segurança que já tenha sido implantada, como domínios do Windows usando o Active Directory. Geralmente é necessário integrar com essas tecnologias existentes, avaliar e adotar as mais novas.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a segurança se integra com os modelos de segurança de transporte existentes e pode aproveitar a infraestrutura existente para modelos de segurança mais recentes de transferência com base na segurança de mensagens SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integração com os modelos de autenticação existentes  
 Uma parte importante de qualquer modelo de segurança de comunicação é a capacidade de identificar e autenticar as entidades em comunicação. Essas entidades na comunicação usam "identidades digitais" ou as credenciais para autenticar-se com os pontos de comunicação. Como plataformas de comunicação distribuído evoluíram, vários modelos de segurança relacionadas e autenticação de credencial foram implementados. Por exemplo, na Internet, o uso de um nome de usuário e senha para identificar os usuários é comum. Na intranet, o uso de um controlador de domínio do Kerberos para fazer backup de usuário e autenticação de serviço está se tornando comuns. Em determinados cenários, como entre dois parceiros comerciais, certificados podem ser usados para autenticar mutuamente os parceiros.  
  
 Portanto, no mundo dos serviços Web, onde o mesmo serviço poderá ser exposto aos clientes corporativos internos, bem como para parceiros externos ou clientes de Internet, é importante que a infraestrutura fornece para integração com segurança esses existente modelos de autenticação. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança dá suporte a uma ampla variedade de tipos de credencial (modelos de autenticação) incluindo:  
  
-   Chamador anônimo.  
  
-   Credencial do cliente de nome de usuário.  
  
-   Credencial do cliente de certificado.  
  
-   Windows (protocolo Kerberos e NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Padrões e interoperabilidade  
 Em um mundo com grandes implantações existentes, homogeneidade é rara. Plataformas de computação/comunicações distribuído precisam interoperar com as tecnologias de fornecedores diferentes oferecem. Da mesma forma, a segurança deve também ser interoperável.  
  
 Para permitir que os sistemas de segurança interoperável, empresas ativas no setor de serviços Web criou uma variedade de padrões. Especificamente, relacionados à segurança, alguns padrões importantes foram propostos: WS-Security: segurança de mensagens SOAP (aceitos pelo corpo de padrões da OASIS e anteriormente conhecido como WS-Security), WS-Trust, WS-SecureConversation e WS-SecurityPolicy.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a uma ampla variedade de cenários de interoperabilidade. O <xref:System.ServiceModel.BasicHttpBinding> classe destina-se no perfil básico de segurança (BSP) e o <xref:System.ServiceModel.WSHttpBinding> classe destina-se a padrões de segurança mais recentes, como 1.1 do WS-Security e WS-SecureConversation. Ao aderir a esses padrões, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança pode interoperar e integrar serviços Web que são hospedados em sistemas operacionais e plataformas diferentes do Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Áreas funcionais de segurança do WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança é dividida em três áreas funcionais: transferir a segurança, controle de acesso e auditoria. Rapidamente, as seções a seguir discutem essas áreas e fornecem links para obter mais informações.  
  
### <a name="transfer-security"></a>Segurança de transferência  
 Segurança de transferência abrange três principais funções de segurança: autenticação, integridade e confidencialidade. *Integridade* é a capacidade de detectar se uma mensagem foi violada. *Confidencialidade* é a capacidade de manter uma mensagem ilegível para qualquer pessoa que não seja o destinatário pretendido; isso é obtido por meio de criptografia. *Autenticação* é a capacidade de verificar uma identidade reivindicada. Juntas, essas três funções ajudam a garantir que as mensagens chegam com segurança de um ponto para outro.  
  
#### <a name="transport-and-message-security-modes"></a>Transporte e modos de segurança de mensagem  
 Dois mecanismos principais são usados para implementar a segurança de transferência em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: *transporte* modo de segurança e *mensagem* modo de segurança.  
  
-   *O modo de segurança de transporte* usa um protocolo de nível de transporte, como HTTPS, para obter a segurança de transferência. O modo de transporte tem a vantagem de ser amplamente adotada, disponível em muitas plataformas e computacionalmente menos complexas. No entanto, ele tem a desvantagem de proteger as mensagens somente de ponto a ponto.  
  
-   *Modo de segurança de mensagem*, no outro lado, usa WS-Security (e outras especificações) para implementar a segurança de transferência. Como a segurança da mensagem é aplicada diretamente para as mensagens SOAP e está contida dentro de envelopes SOAP, junto com os dados de aplicativo, ele tem a vantagem de ser transporte independente de protocolo, mais extensível e garantir segurança de ponta a ponta (em vez de ponto a ponto); ele tem a desvantagem de sendo várias vezes mais lento do que o modo de segurança de transporte porque ele tem que lidar com a natureza XML das mensagens de SOAP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Essas diferenças, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Um modo de segurança terceiro usa ambos os modos anteriores e traz as vantagens de ambos. Esse modo é chamado `TransportWithMessageCredential`. Nesse modo, segurança de mensagem é usada para autenticar o cliente e a segurança de transporte é usada para autenticar o servidor e fornecer a integridade e confidencialidade da mensagem. Graças isso, o `TransportWithMessageCredential` modo de segurança é quase tão rápido quanto o modo de segurança de transporte e fornece extensibilidade de autenticação de cliente da mesma maneira como a segurança de mensagem. No entanto, ao contrário do modo de segurança de mensagem, ele não fornece segurança de ponta a ponta completa.  
  
### <a name="access-control"></a>Controle de acesso  
 *Controle de acesso* também é conhecido como autorização. *Autorização* permite que diferentes usuários tenham privilégios diferentes para exibir dados. Por exemplo, como arquivos de recursos humanos da empresa contêm dados confidenciais de funcionários, somente os gerentes são permitidos para exibir dados de funcionários. Além disso, os gerentes podem exibir somente os dados para seus relatórios diretos. Nesse caso, o controle de acesso se baseia a função ("manager"), bem como a identidade específica do Gerenciador (para impedir que um Gerenciador de examinar os registros de funcionário do gerente de outro).  
  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], recursos de controle de acesso são fornecidos por meio da integração com o common language runtime (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> e por meio de um conjunto de APIs, conhecido como o *modelo de identidade*. Para obter detalhes sobre o controle de acesso e autorização baseada em declarações, consulte [estendendo segurança](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Auditoria  
 *Auditoria* é o log de eventos de segurança para o log de eventos do Windows. Você pode registrar eventos relacionados à segurança, como falhas de autenticação (ou êxitos). Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Para obter detalhes de programação, consulte [como: eventos de auditoria de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Protegendo serviços](../../../../docs/framework/wcf/securing-services.md)  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Diretrizes e práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Configurando serviços usando arquivos de configuração](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
