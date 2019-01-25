---
title: WSDL e política
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 1e6b315c1830602e72b4b498cd38eed8428bc5ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741425"
---
# <a name="wsdl-and-policy"></a>WSDL e política
Este tópico aborda o Windows Communication Foundation (WCF) WSDL 1.1, detalhes de implementação de WS-Policy e mecanismo WS-PolicyAttachment, bem como declarações adicionais do WS-Policy e extensões WSDL 1.1 introduzidas pelo WCF.  
  
 O WCF implementa as especificações de WS-Policy e mecanismo WS-PolicyAttachment enviadas para o W3C com restrições e esclarecimentos descritos neste documento.  
  
 Este documento usa os prefixos e namespaces mostrado na tabela a seguir.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|wsp (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|wsp (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|HTTP|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Extensões WSDL1.1 do WCF  
 O WCF usa as seguintes extensões WSDL1.1 para descrever os requisitos de contrato de sessão.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs: Boolean, indica que essa operação inicia uma sessão do WCF; o valor padrão é `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs: Boolean, indica que essa operação encerra uma sessão do WCF; o valor padrão é `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs: Boolean, indica que este contrato requer sessão seja estabelecida.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>URIs de transporte de associação de 1.x HTTP SOAP  
 WCF usa os seguintes URIs para indicar os transportes para ser usado para elementos de extensão de ligação WSDL 1.1, SOAP 1.1 e SOAP 1.2.  
  
|Transporte|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Pipes nomeados|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Declarações de política implementadas pelo WCF  
 Além de declarações de política introduzidas nas especificações de serviços da Web (WS-*) e mencionado em outras seções deste documento, o WCF implementa as seguintes declarações de política.  
  
|Declaração de política|Assunto da diretriz|Descrição|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação básica HTTP.|  
|http:HttpDigestAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação Digest HTTP.|  
|http:HttpNegotiateAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação de negociação de HTTP.|  
|http:HttpNtlmAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação NTLM HTTP.|  
|msf:Streamed|Ponto de extremidade|Ponto de extremidade usa o enquadramento de mensagem em fluxo. Essa declaração é usada com o protocolo de enquadramento de mensagem fornecido para transportes, como TCP e pipes nomeados.|  
|msf:SslTransportSecurity|Ponto de extremidade|Ponto de extremidade usa a segurança de camada de transporte (TLS) com o enquadramento de mensagem.|  
|msf:WindowsTransportSecurity|Ponto de extremidade|Ponto de extremidade usa a negociação de provedor de segurança (SPNEGO) com o enquadramento de mensagem.|  
|msmq:MsmqBestEffort|Ponto de extremidade|MSMQ com garantias de melhor esforço.|  
|msmq:MsmqSession|Ponto de extremidade|MSMQ com garantias de sessão.|  
|msmq:MsmqVolatile|Ponto de extremidade|Volátil do MSMQ.|  
|msmq:Authenticated|Ponto de extremidade|Autenticação é usada com o transporte MSMQ.|  
|msmq:WindowsDomain|Ponto de extremidade|MSMQ usa a autenticação de domínio do Windows.|  
|cdp:CompositeDuplex|Ponto de extremidade|Ponto de extremidade usa duas conexões de transporte inversa separado do in e out de mensagens.|  
|mssp:RsaToken|Aninhados|Declaração de token chave RSA. Normalmente, esse requisito é atendido por uma chave RSA serializada diretamente como parte das informações de chave em uma assinatura de endosso.|  
|mssp:SslContextToken|Aninhados|Requer que um SecurityContextToken obtido usando o handshake TLS binário usando o WS-Trust. Declarações aninhadas incluem: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Aninhados|Especifica um requisito de que um token de segurança de solicitação (RST) solicitar mensagens [WS-Trust] usando a associação Cancel [WS-Trust, WS-SC] não ser enviado para o emissor de um determinado SecurityContextToken. Se essa declaração estiver presente, essas mensagens de solicitação não devem ser enviadas para o emissor. Se essa asserção não estiver presente, essas mensagens de solicitação podem ser enviadas para o emissor.|  
|mssp:RequireClientCertificate|Aninhados|Esse elemento opcional especifica um requisito para um certificado de cliente a ser fornecido como parte do protocolo TLSNEGO. Se essa declaração estiver presente, um certificado de cliente deve ser fornecido. Se essa asserção não estiver presente, um certificado de cliente não deve ser fornecido. Essa asserção não deve ser usada fora mssp:SslContextToken.|  
  
## <a name="see-also"></a>Consulte também
- [Publicação de WSDL personalizada](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
- [Como: Exportar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Como: Importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
