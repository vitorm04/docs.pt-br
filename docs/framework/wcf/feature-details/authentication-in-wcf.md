---
title: "Autenticação no WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fbd4a322153bd9f560b6c039f586100770a0216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-wcf"></a>Autenticação no WCF
Os tópicos a seguir mostram um número de mecanismos diferentes em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que fornecem autenticação, por exemplo, a autenticação do Windows, certificados x. 509 e o nome de usuário e senhas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome e senha de usuário para autenticação e as funções de usuário para autorização. Este tópico explica como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem usar o mesmo banco de dados para autenticar e autorizar usuários.  
  
 [Como: usar um nome de usuário personalizada e validação de senha](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Demonstra como integrar um validador de nome e senha de usuário personalizada.  
  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço. Se a identidade esperada e a identidade retornada pelo serviço não coincidirem, a autenticação falhará.  
  
 [Negociação de segurança e tempos limite](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.  
  
 [Depuração de erros de autenticação do Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
