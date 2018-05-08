---
title: Conceitos de segurança utilizados no WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ac76f1742ab72de9f5180d1ea2fcbc668ec2140c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-concepts-used-in-wcf"></a>Conceitos de segurança utilizados no WCF
Segurança do Windows Communication Foundation (WCF) é criada nos conceitos já está em uso e implantada em várias infraestruturas de segurança.  
  
 O WCF dá suporte a alguns desses infraestruturas, como o protocolo (SSL) sobre HTTP (HTTPS). No entanto, WCF vai além do suporte a infra-estruturas de segurança, implementando novos padrões de segurança interoperável (como WS-Security) nas mensagens codificadas em SOAP. Se você estiver usando mecanismos existentes ou novos padrões interoperáveis, os conceitos de segurança por trás de ambos são os mesmos. Noções básicas sobre os conceitos por trás de infraestruturas existentes e os padrões mais recentes é fundamental para implementar o melhor modelo de segurança para um aplicativo.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Introdução à segurança para os serviços Web WCF  
 O grupo Microsoft Patterns e práticas escreveu um white paper detalhado sobre diretrizes de segurança do WCF que está disponível para download aqui: [guia de segurança do WCF](http://go.microsoft.com/fwlink/?LinkId=210210). Este white paper descreve os conceitos fundamentais de segurança como elas se relacionam com os serviços da web, principais conceitos de segurança do WCF, cenários de aplicativos de intranet e cenários de aplicativo de internet.  
  
## <a name="industry-wide-security-specifications"></a>Especificações de segurança do setor  
  
### <a name="public-key-infrastructure"></a>Infraestrutura de chave pública  
 Infraestrutura de chave pública (PKI) é um sistema de certificados digitais, autoridades de certificação e outras autoridades de registro que verificam e autenticar cada parte envolvida em uma transação eletrônica com o uso de criptografia de chave pública. Para obter mais informações, consulte [serviços de certificados do Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protocolo Kerberos  
 O *protocolo Kerberos* é uma especificação para a criação de um mecanismo de segurança que autentica os usuários em um domínio do Windows. Ele permite que um usuário estabelecer um contexto de seguro com outras entidades dentro de um domínio. Plataformas Windows 2000 e posteriores usam o protocolo Kerberos, por padrão. Noções básicas sobre os mecanismos do sistema é útil ao criar um serviço que irá interagir com os clientes da intranet. Além disso, desde o *Web Services Security Kerberos associação* é amplamente publicados, você pode usar o protocolo Kerberos para se comunicar com clientes de Internet (ou seja, o protocolo Kerberos é interoperável). Para obter mais informações sobre como o protocolo Kerberos é implementado no Windows, consulte [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certificados x. 509  
 Certificados x. 509 são uma forma de credencial primário usada em aplicativos de segurança. Para obter mais informações sobre o x. 509 certificados Consulte [certificados de chave pública x. 509](http://go.microsoft.com/fwlink/?LinkId=210213). Certificados x. 509 são armazenados em um repositório de certificados. Um computador executando o Windows tem vários tipos de armazenamentos de certificados, cada um com uma finalidade diferente. Para obter mais informações sobre os repositórios diferentes, consulte [repositórios de certificados](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>As especificações de segurança de serviços Web  
 As associações definidas pelo sistema oferecem suporte a várias especificações de segurança de serviços web comumente usadas. Para obter uma lista de associações fornecidas pelo sistema e as especificações de serviços da web oferecem suporte a consulte: [Web Services dá suporte para protocolos System-Provided associações de interoperabilidade](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mecanismos de controle de acesso  
 O WCF fornece várias maneiras para controlar o acesso a um serviço ou a operação. Entre elas estão:  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  Provedor de associação ASP.NET  
  
3.  Provedor de função do ASP.NET  
  
4.  Gerenciador de autorização  
  
5.  Modelo de identidade  
  
 Para obter mais informações sobre esses tópicos, consulte [mecanismos de controle de acesso](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
