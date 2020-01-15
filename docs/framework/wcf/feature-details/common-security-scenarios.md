---
title: Cenários comuns de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 578ec2d7d5abe1285007ad22d8bacd69e695b1d3
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964280"
---
# <a name="common-security-scenarios"></a>Cenários comuns de segurança
Os tópicos nesta seção catalogam várias configurações de segurança de cliente e serviço possíveis. As configurações variam de acordo com uma série de fatores. Por exemplo, se um serviço ou cliente está em uma intranet ou se a segurança é fornecida pelo Windows ou pelo transporte (como o HTTPS).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Serviço e cliente de Internet desprotegido](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Um exemplo de um cliente e serviço públicos e desprotegidos.  
  
 [Serviço e cliente desprotegido de Intranet](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Um serviço de Windows Communication Foundation básico (WCF) desenvolvido para fornecer informações sobre uma rede privada segura para um aplicativo WCF.  
  
 [Segurança de transporte com autenticação básica](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 O aplicativo permite que os clientes façam logon usando a autenticação personalizada.  
  
 [Segurança de transporte com autenticação do Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Mostra um cliente e um serviço protegidos pela segurança do Windows.  
  
 [Segurança de transporte com um cliente anônimo](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Esse cenário usa a segurança de transporte (como HTTPS) para garantir a confidencialidade e a integridade.  
  
 [Segurança de transporte com autenticação de certificado](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Mostra um cliente e um serviço protegidos por um certificado.  
  
 [Segurança de mensagem com um cliente anônimo](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Mostra um cliente e um serviço protegidos pela segurança de mensagem do WCF.  
  
 [Segurança de mensagem com um nome de usuário cliente](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 O cliente é um aplicativo Windows Forms que permite que os clientes façam logon usando um nome de usuário e senha de domínio.  
  
 [Segurança de mensagem com um certificado de cliente](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Os servidores têm certificados e cada cliente tem um certificado. Um contexto de segurança é estabelecido por meio da negociação TLS.  
  
 [Segurança de mensagem com um cliente do Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Uma variação do cliente de certificado. Os servidores têm certificados e cada cliente tem um certificado. Um contexto de segurança é estabelecido por meio da negociação TLS.  
  
 [Segurança de mensagem com um cliente do Windows sem negociação de credencial](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Mostra um cliente e um serviço protegidos por um domínio Kerberos.  
  
 [Segurança de mensagem com certificados mútuos](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Os servidores têm certificados e cada cliente tem um certificado. O certificado do servidor é distribuído com o aplicativo e está disponível fora de banda.  
  
 [Segurança de mensagem com tokens emitidos](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Segurança federada que permite o estabelecimento de confiança entre domínios independentes.  
  
 [Subsistema confiável](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Um cliente acessa um ou mais serviços Web que são distribuídos em uma rede. Os serviços Web acessam recursos adicionais (como bancos de dados ou outros serviços Web) que devem ser protegidos.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Security](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Veja também

- [Diretrizes e práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
