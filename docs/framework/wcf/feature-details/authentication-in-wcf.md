---
title: Autenticação no WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964691"
---
# <a name="authentication-in-wcf"></a>Autenticação no WCF
Os tópicos a seguir mostram vários mecanismos diferentes no Windows Communication Foundation (WCF) que fornecem autenticação, por exemplo, autenticação do Windows, certificados X. 509 e nome de usuário e senhas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como usar o provedor de associação do ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 Os recursos do ASP.NET incluem uma associação e um provedor de função, um banco de dados para armazenar pares de nome de usuário/senha para autenticação e funções de usuário para autorização. Este tópico explica como os serviços WCF podem usar o mesmo banco de dados para autenticar e autorizar usuários.  
  
 [Como usar um nome de usuário e validador de senha personalizados](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 Demonstra como integrar um validador de nome de usuário/senha personalizado.  
  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 Como uma proteção extra, um cliente pode autenticar o serviço especificando a *identidade* esperada do serviço. Se a identidade esperada e a identidade retornada pelo serviço não corresponderem, a autenticação falhará.  
  
 [Negociação de segurança e tempos limite](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 Descreve como usar a propriedade <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> na classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.  
  
 [Depuração de erros de autenticação do Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Concentra-se em problemas comuns encontrados ao usar a autenticação do Windows.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>Veja também

- [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
