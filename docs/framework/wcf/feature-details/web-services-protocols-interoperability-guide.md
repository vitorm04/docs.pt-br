---
title: "Guia de interoperabilidade de protocolos de serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7dfcd092cb7b21e31ec1098df5e9534cd27cfc9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-protocols-interoperability-guide"></a>Guia de interoperabilidade de protocolos de serviços
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]implementa um número de protocolos de serviços da Web. Muitos desses protocolos incluem um número de pontos de extensibilidade da esquerda para a critério do implementador e opções. Este tópico fornece uma lista de Web services protocolos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa. Outros tópicos nesta seção fornecem detalhes de implementação para cada protocolo tem suportado.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Os protocolos implementados pelo WCF de serviços Web  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece suporte para protocolos de infraestrutura do Web services (WS) por meio de canais e protocolos de aplicativo de serviços da Web por meio do recurso de contratos. Interoperabilidade de protocolos de aplicativos é realizada por meio da linguagem de descrição de esquema XML 1.0 (XSD) e Web Services Description Language (WSDL) 1.1.  
  
 Interoperabilidade de protocolos de infraestrutura é fornecida pelo WS-* especificações. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os canais oferecem suporte para um número de WS -\* protocolos de infraestrutura. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]canais são configurados usando elementos de associação. As tabelas a seguir contêm a lista completa de WS -\* protocolos infraestrutura implementados por várias [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementos de associação.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>oferece suporte às especificações na tabela a seguir.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|Ligação de SOAP 1.1 HTTP|[Protocolo de acesso a objeto simples (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), seção 7|  
|SOAP 1.2 associação de HTTP|[Versão do SOAP 1.2 parte 2: Adjuncts (segunda edição)](http://go.microsoft.com/fwlink/?LinkId=95329), seção 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> suporte as especificações na tabela a seguir.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (quarta edição)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Protocolo de acesso a objeto simples (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Core|[Versão do SOAP 1.2 parte 1: Estrutura da mensagem (segunda edição)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|2004 do WS-Addressing/08|[Endereçamento (WS-Addressing) de serviços Web](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|Endereçamento 1.0 - Core de serviços Web do W3C|[1.0 - Core endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|Endereçamento associação SOAP 1.0 - de serviços Web do W3C|[Associação de SOAP 1.0 - endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|Serviços Web de W3C endereçamento 1.0 - WSDL associação *|[Associação de WSDL 1.0 - endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|Serviços Web do W3C endereçamento 1.0 metadados|[Metadados de 1.0 - endereçamento de serviços Web](http://www.w3.org/TR/ws-addr-metadata/)|  
|Associação de SOAP1.1 WSDL|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|Associação de SOAP1.2 WSDL|[Extensão de associação 1.1 WSDL para SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>oferece suporte às especificações na tabela a seguir.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|XOP|[Empacotamento de otimização de XML binário](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 associação|[Mecanismo de otimização de transmissão de mensagem SOAP](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM ligação de SOAP 1.1|[Ligação de SOAP 1.1 para MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|WS-PolicyAssertions MTOM|Para ser publicado.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>oferece suporte às especificações na tabela a seguir.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|WSS: Segurança de mensagens SOAP 1.0|[Web Services Security: Segurança de mensagens SOAP 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Perfil de Token de nome de usuário 1.0|[Perfil de segurança de UsernameToken 1.0 de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> exigir Password/@Type= PasswordText (padrão)|  
|WSS: Perfil de Token de x. 509 1.0|[Web Services Security x. 509 certificado perfil de Token](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 Profile 1.0 do Token|[Segurança de serviços da Web: Perfil de Token de SAML](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: Segurança de mensagens SOAP 1.1|[Web Services Security: Segurança de mensagens SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|Perfil de Token de nome de usuário 1.1 do WSS|[Segurança UsernameToken Profile 1.1 de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> não implementa a derivação de chaves com base em senha;<br /><br /> exigir Password/@Type= PasswordText (padrão)|  
|WSS: X509 Token Profile 1.1|[Web Services Security x. 509 Token perfil de certificado 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Perfil de Token Kerberos 1.1|[Perfil de segurança de Token Kerberos 1.1 de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 Profile 1.1 do Token|[Perfil de Token SAML 1.1 de segurança de serviços Web](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-Secure Conversation|[Linguagem de conversa segura de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Idioma de confiança de serviços Web](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Linguagem de conversa segura de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Como corrigida por errata enviado ao OASIS WS-SX Technical Committee.<br /><br /> [mensagem do WS-sx](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Protocolo de mensagens confiável versão 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>oferece suporte às especificações na tabela a seguir.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|Coordenação WS|[Coordenação de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Transação atômica de serviços Web](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 O <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <!--zz <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter>, --> `System.ServiceModel.Description.MetadataImporter`, `System.ServiceModel.Description.WSDLImporter`, e <xref:System.ServiceModel.Description.MetadataResolver> classes oferecem suporte para as seguintes especificações de metadados:  
  
-   [Esquema XML parte 1: Segunda edição das estruturas](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [Esquema XML parte 2: Tipos de dados Second Edition](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [1.2 mecanismo WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [O WS-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [Transferência de WS obter para recuperação de metadados](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Além disso, os seguintes perfis de interoperabilidade são implementados em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP Binding 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Segurança básica de perfil 1.0 trabalho rascunho](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Consulte também  
 [Protocolos com suporte por associações de interoperabilidade fornecidas pelo sistema de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [Protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [WSDL e política](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)  
 [Protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md)  
 [Protocolo de mensagens confiável versão 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)  
 [Protocolo de mensagens confiável versão 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)  
 [Protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)  
 [Protocolo de intercâmbio de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
