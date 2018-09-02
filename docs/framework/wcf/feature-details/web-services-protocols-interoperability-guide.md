---
title: Guia de interoperabilidade de protocolos de serviços
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: da5014292a8ebfcea48a7b6e1a0cdfd014b09961
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403638"
---
# <a name="web-services-protocols-interoperability-guide"></a>Guia de interoperabilidade de protocolos de serviços
Windows Communication Foundation (WCF) implementa um número de protocolos de serviços da Web. Muitos desses protocolos incluem uma série de opções e os pontos de extensibilidade da esquerda para a critério do implementador. Este tópico fornece uma lista de protocolos de serviços Web que WCF implementa. Outros tópicos dentro desta seção fornecem detalhes de implementação para cada protocolo com suporte.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Implementado pelo WCF de protocolos de serviços Web  
 O WCF fornece suporte para protocolos de infraestrutura do Web services (WS) por meio de canais e protocolos de aplicativo por meio do recurso de contratos de serviços Web. Interoperabilidade de protocolos de aplicativo é realizada por meio da linguagem de descrição de esquema XML 1.0 (XSD) e Web Services Description Language (WSDL) 1.1.  
  
 Interoperabilidade de protocolos de infraestrutura é fornecida pelo WS-* especificações. Canais do WCF dão suporte para um número de WS -\* protocolos de infraestrutura. Canais do WCF são configurados usando os elementos de associação. As tabelas a seguir contêm a lista completa de WS -\* protocolos de infra-estrutura implementados por diversos elementos de associação do WCF.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> dá suporte a especificações na tabela a seguir.  
  
|Especificação/documento|Link|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](https://go.microsoft.com/fwlink/?LinkId=90372)|  
|Ligação de SOAP 1.1 HTTP|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=90520), seção 7|  
|SOAP 1.2 associação de HTTP|[Parte 2 do SOAP versão 1.2: Adjuncts (segunda edição)](https://go.microsoft.com/fwlink/?LinkId=95329), seção 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> dão suporte as especificações na tabela a seguir.  
  
|Especificação/documento|Link|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (quarta edição)](https://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Core|[SOAP versão 1.2 parte 1: Estrutura de mensagens (segunda edição)](https://go.microsoft.com/fwlink/?LinkId=94664)|  
|2004 de WS-Addressing/08|[Endereçamento (WS-Addressing) de serviços Web](https://go.microsoft.com/fwlink/?LinkId=81239)|  
|1.0 - Core endereçamento de serviços Web do W3C|[1.0 - Core endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=96688)|  
|Endereçamento 1.0 - associação de SOAP de serviços de Web do W3C|[Associação de SOAP 1.0 - endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=96689)|  
|Serviços Web do W3C endereçamento 1.0 - WSDL ligação *|[Associação de WSDL 1.0 - endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=96690)|  
|Endereçamento 1.0 metadados do W3C Web Services|[Metadados de 1.0 - endereçamento de serviços da Web](http://www.w3.org/TR/ws-addr-metadata/)|  
|Associação de SOAP1.1 WSDL|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)|  
|Associação de SOAP1.2 WSDL|[Extensão de associação 1.1 da WSDL para SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> dá suporte a especificações na tabela a seguir.  
  
|Especificação/documento|Link|  
|-----------------------------|----------|  
|XOP|[XML binário otimizado de empacotamento](https://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 associação|[Mecanismo de otimização da transmissão de mensagens SOAP](https://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM ligação de SOAP 1.1|[Ligação de SOAP 1.1 para MTOM 1.0](https://go.microsoft.com/fwlink/?LinkId=96712)|  
|WS-PolicyAssertions MTOM|Para ser publicado.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> dá suporte a especificações na tabela a seguir.  
  
|Especificação/documento|Link|  
|-----------------------------|----------|  
|WSS: Segurança de mensagem SOAP 1.0|[Web Services Security: Segurança de mensagem SOAP 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Perfil de Token de nome de usuário 1.0|[Web Services Security UsernameToken Profile 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> exigir Password/@Type= PasswordText (padrão)|  
|WSS: X. 509 Token Profile 1.0|[Web Services Security certificado perfil de Token X.509](https://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 Token Profile 1.0|[Web Services Security: Perfil de Token de SAML](https://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: Segurança de mensagem SOAP 1.1|[Web Services Security: Segurança de mensagem SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=91240)|  
|Perfil de Token de nome de usuário 1.1 do WSS|[Web Services Security UsernameToken Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> não implementam a derivação de chave baseado em senha;<br /><br /> exigir Password/@Type= PasswordText (padrão)|  
|WSS: X509 Token Profile 1.1|[Web Services Security certificado perfil de Token X.509 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Perfil de Token Kerberos 1.1|[Perfil de Token Kerberos de segurança 1.1 de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 Profile 1.1 de Token|[Perfil de Token SAML 1.1 de segurança de serviços Web](https://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-Secure Conversation|[Linguagem de conversa segura de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Idioma de confiança de serviços Web](https://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Linguagem de conversa segura de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Como corrigida por errata enviado ao OASIS WS-SX Technical Committee.<br /><br /> [mensagem do WS-sx](https://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Protocolo de Reliable Messaging versão 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> dá suporte a especificações na tabela a seguir.  
  
|Especificação/documento|Link|  
|-----------------------------|----------|  
|WS-Coordination|[Coordenação de serviços Web](https://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Transação atômica de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 O <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <!--zz <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter>, --> `System.ServiceModel.Description.MetadataImporter`, `System.ServiceModel.Description.WSDLImporter`, e <xref:System.ServiceModel.Description.MetadataResolver> classes oferecem suporte para as seguintes especificações de metadados:  
  
-   [Esquema XML parte 1: Segunda edição das estruturas](https://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [Esquema XML parte 2: Tipos de dados Second Edition](https://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-Policy 1.2](https://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](https://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [O WS-MetadataExchange 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [Obter do WS-Transfer para recuperação de metadados](https://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Além disso, os seguintes perfis de interoperabilidade são implementados em WCF:  
  
-   [Perfil básico 1.1](https://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [SOAP Simple associação 1.0](https://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Criar o perfil de segurança básica 1.0 trabalho rascunho](https://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Consulte também  
 [Protocolos de serviços Web com suporte em associações de interoperabilidade fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [Protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)  
 [Referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [WSDL e política](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)  
 [Protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md)  
 [Protocolo de Reliable Messaging versão 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)  
 [Protocolo de Reliable Messaging versão 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)  
 [Protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)  
 [Protocolo de troca de contexto](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
