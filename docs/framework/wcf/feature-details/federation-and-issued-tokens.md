---
title: "Federação e tokens emitidos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa3ed1b68cab19b0464067a2dc8f52be03279f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="federation-and-issued-tokens"></a>Federação e tokens emitidos
Com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], você pode criar clientes que se comunicam com segurança com os serviços que implementam as especificações de WS-Federation e WS-Trust. As especificações de usam XML, SOAP e WSDL Web Services Description Language () para fornecer mecanismos que permitem a autenticação e autorização em realms de confiança diferente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 Fornece uma visão geral da federação.  
  
 [Federação e confiabilidade](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Lista os problemas de design para estar ciente de quando criar federado serviços ou clientes.  
  
 [Como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Descreve os conceitos básicos de criação de um cliente federado com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Como: configurar as credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Descreve as etapas de criação de um serviço federado.  
  
 [Como: criar uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Descreve como configurar clientes e serviços que usam o `WSFederationHttpBinding`.  
  
 [Como: criar um serviço de Token de segurança](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Descreve as etapas de criação de um serviço de token de segurança.  
  
 [Declarações e Tokens de segurança de asserções Markup Language (SAML)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Descreve os tokens de segurança asserções Markup Language (SAML), que são extensíveis e habilitar a criação avançada tipos de declaração.  
  
 [Como: configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Descreve como criar um emissor local dos tokens de segurança.  
  
 [Como: desabilitar sessões seguranças em uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Descreve como desabilitar sessões seguras em uma `WSFederationHttpBinding`. Desabilitar sessões seguras é necessário ao criar uma Web farm que exige uma sessão para cada cliente.  
  
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
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Tokens personalizados](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
