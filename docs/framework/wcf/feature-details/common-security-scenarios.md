---
title: Cenários comuns de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
author: BrucePerlerMS
ms.openlocfilehash: 081518fb1b3eb1f66c772cd401c19c0eb523d32a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200822"
---
# <a name="common-security-scenarios"></a>Cenários comuns de segurança
Os tópicos nesta seção uma série de possíveis clientes e as configurações de segurança do serviço de catálogo. As configurações variam de acordo com uma série de fatores. Por exemplo, se um cliente ou serviço estiver em uma intranet, ou se a segurança é fornecida pelo Windows ou de transporte (como HTTPS).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Serviço e cliente de Internet desprotegido](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Um exemplo de um cliente público, não segura e serviço.  
  
 [Serviço e cliente desprotegido de Intranet](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Um serviço básico do Windows Communication Foundation (WCF) desenvolvido para fornecer informações sobre uma rede privada segura para um aplicativo WCF.  
  
 [Segurança de transporte com autenticação básica](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 O aplicativo permite que clientes façam logon usando autenticação personalizada.  
  
 [Segurança de transporte com autenticação do Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Mostra um cliente e serviço protegidos pela segurança do Windows.  
  
 [Segurança de transporte com um cliente anônimo](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Esse cenário usa a segurança de transporte (como HTTPS) para garantir a confidencialidade e integridade.  
  
 [Segurança de transporte com autenticação de certificado](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Mostra um cliente e protegido por um certificado de serviço.  
  
 [Segurança de mensagem com um cliente anônimo](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Mostra um cliente e serviço protegidos pela segurança de mensagem do WCF.  
  
 [Segurança de mensagem com um nome de usuário cliente](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 O cliente é um aplicativo de formulários do Windows que permite que os clientes façam logon usando um nome de usuário de domínio e uma senha.  
  
 [Segurança de mensagem com um certificado de cliente](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Servidores têm certificados e cada cliente tem um certificado. Um contexto de segurança é estabelecido por meio de negociação de segurança de camada de transporte (TLS).  
  
 [Segurança de mensagem com um cliente do Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Uma variação do cliente de certificado. Servidores têm certificados e cada cliente tem um certificado. Um contexto de segurança é estabelecido por meio de negociação de TLS.  
  
 [Segurança de mensagem com um cliente do Windows sem negociação de credencial](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Mostra um cliente e um serviço protegido por um domínio do Kerberos.  
  
 [Segurança de mensagem com certificados mútuos](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Servidores têm certificados e cada cliente tem um certificado. O certificado do servidor é distribuído com o aplicativo e está disponível fora da banda.  
  
 [Segurança de mensagem com tokens emitidos](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Segurança federada que permite o estabelecimento da relação de confiança entre domínios independentes.  
  
 [Subsistema confiável](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Um cliente acessa um ou mais serviços Web que são distribuídos em uma rede. Os serviços Web de acessar recursos adicionais (como bancos de dados ou outros serviços da Web) que devem ser protegidos.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Autenticação](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federação e tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes e práticas recomendadas de segurança](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
