---
title: Protegendo serviços e clientes
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2e0440aadcad7c4297cdc6e6489ca004480420ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497406"
---
# <a name="securing-services-and-clients"></a>Protegendo serviços e clientes
As informações nesta seção se concentra na programação de segurança no Windows Communication Foundation (WCF). Em geral, isso inclui a seleção de uma associação fornecida pelo sistema apropriada, definindo as propriedades do elemento de segurança e, em seguida, definir propriedades dos comportamentos de serviço que determinam como as credenciais são recuperadas para uso, o serviço ou cliente. Essas técnicas aborda os requisitos de segurança da maioria dos usuários para a maioria dos cenários, como mostrado na [cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Se seu cenário exigir mais recursos, consulte primeiro [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); se uma solução não estiver visível, consulte [estendendo segurança](../../../../docs/framework/wcf/extending/extending-security.md). Se você estiver criando (ou interagir com) um sistema que usa declarações avançada, consulte os tópicos [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Programação de segurança do WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 Uma visão geral do modelo de programação usada para proteger as mensagens.  
  
 [Visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Uma visão geral de como proteger mensagens por meio da camada de transporte.  
  
 [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Resume os motivos para usar a segurança em nível de mensagem no Windows Communication Foundation (WCF).  
  
 [Sessões seguras](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Uma discussão sobre as considerações necessárias ao proteger uma sessão do WCF.  
  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 Obter uma explicação de algumas das tarefas comuns exigidas quando usando certificados x. 509.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [Estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [Estendendo a segurança](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Consulte também  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
