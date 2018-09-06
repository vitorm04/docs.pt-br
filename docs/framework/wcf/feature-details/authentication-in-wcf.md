---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 401bd8901f4d8b9292e83d3e54d0afce30c9584f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785824"
---
# <a name="authentication-in-wcf"></a>Autenticação no WCF
Os tópicos a seguir mostram um número de mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, a autenticação do Windows, certificados X.509 e o nome de usuário e senhas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 Recursos do ASP.NET incluem uma associação e provedor de função, um banco de dados para armazenar pares de nome/senha de usuário para autenticação e funções de usuário para autorização. Este tópico explica como os serviços do WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.  
  
 [Como usar um nome de usuário e validador de senha personalizados](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Demonstra como integrar um validador de nome/senha de usuário personalizada.  
  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Como uma proteção extra, um cliente pode autenticar o serviço especificando o esperado *identidade* do serviço. Se a identidade esperada e a identidade retornados pelo serviço não corresponderem, a autenticação falhará.  
  
 [Negociação de segurança e tempos limite](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 Descreve como usar o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade no <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe.  
  
 [Depuração de erros de autenticação do Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Se concentra em problemas comuns encontrados ao usar a autenticação do Windows.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
