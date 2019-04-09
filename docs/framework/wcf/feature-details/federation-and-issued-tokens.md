---
title: Federação e tokens emitidos
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 5ea30c2e9593f289c91a47cc082becf47dedc450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072773"
---
# <a name="federation-and-issued-tokens"></a>Federação e tokens emitidos
Com o Windows Communication Foundation (WCF), você pode criar clientes que se comunicam com segurança com os serviços que implementam as especificações de WS-Federation e WS-Trust. As especificações de usarem o XML, SOAP e descrição de linguagem WSDL (Web Services) para fornecer mecanismos que permitem a autenticação e autorização em realms de confiança diferente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 Fornece uma visão geral da federação.  
  
 [Federação e confiabilidade](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Lista os problemas de design, você deve estar ciente de quando criar federado serviços ou clientes.  
  
 [Como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Descreve os fundamentos da criação de um cliente federado com o WCF.  
  
 [Como: configurar credenciais em um serviço de federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Descreve as etapas de criação de um serviço federado.  
  
 [Como: criar uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Descreve como configurar clientes e serviços que usam o `WSFederationHttpBinding`.  
  
 [Como: criar um serviço de token de segurança](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Descreve as etapas de criação de um serviço de token de segurança.  
  
 [Declarações e tokens de SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Descreve os tokens de segurança asserções SAML (Markup Language), que são extensíveis e permitem que você crie avançados tipos de declaração.  
  
 [Como: configurar um emissor local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Descreve como criar um emissor local dos tokens de segurança.  
  
 [Como: desabilitar sessões seguras em uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Descreve como desabilitar sessões seguras em um `WSFederationHttpBinding`. É necessário desabilitar sessões seguras, ao criar uma Web farm que exige uma sessão para cada cliente.  
  
## <a name="reference"></a>Referência  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Consulte também

- [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Tokens personalizados](../../../../docs/framework/wcf/extending/custom-tokens.md)
- [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
