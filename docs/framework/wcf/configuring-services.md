---
title: "Configurando serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0783107d22f2d64dd8ba7936ce7d2a283f6d8317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-services"></a>Configurando serviços
Depois que você tiver criado e implementado o contrato de serviço, você está pronto para configurar seu serviço. Isso é onde você pode definir e personalizar como o serviço é exposto aos clientes, incluindo a especificação do endereço onde ele pode ser encontrado, o transporte e a codificação de mensagens usa para enviar e receber mensagens e o tipo de segurança requer.  
  
 Configuração conforme usado aqui inclui todas as formas imperativa no código ou usando um arquivo de configuração, no qual você pode definir e personalizar os vários aspectos de um serviço, como especificando seus endereços de ponto de extremidade, os transportes usados e seus esquemas de segurança. Na prática, gravar a configuração é a maior parte da programação de aplicativos [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)  
 A partir do [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é fornecido com um novo modelo de configuração padrão que simplifica os requisitos de configuração do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Se você não fornecer nenhum [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuração para um serviço específico, o tempo de execução configura automaticamente o serviço com pontos de extremidade padrão, associações e comportamentos.  
  
 [Configuring Services Using Configuration Files](../../../docs/framework/wcf/configuring-services-using-configuration-files.md) (Configurando serviços usando arquivos de configuração)  
 Um serviço [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] é configurável usando a tecnologia de configuração do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Mais comumente, os elementos XML são adicionados ao arquivo Web.config para um site do IIS (Serviços de Informações da Internet) que hospeda um serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Os elementos permitem alterar detalhes, como os endereços de ponto de extremidade (os endereços reais usados para se comunicar com o serviço) em uma base por máquina.  
  
 [Bindings](../../../docs/framework/wcf/bindings.md) (Associações)  
 Além disso, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclui várias configurações comuns fornecidos pelo sistema na forma de associações que permitem que você selecionar rapidamente os recursos mais básicos de como um serviço e um cliente se comunicar, como os transportes, segurança e codificações de mensagem usado.  
  
 [Endpoints](../../../docs/framework/wcf/endpoints.md) (Pontos de extremidade)  
 Toda a comunicação com um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade contêm o contrato, as informações de configuração que são especificadas nas associações e os endereços que indicam onde encontrar o serviço ou onde obter informações sobre o serviço.  
  
 [Securing Services](../../../docs/framework/wcf/securing-services.md) (Protegendo serviços)  
 Usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e mecanismos de segurança existente, você pode implementar a confidencialidade, integridade, autenticação e autorização em qualquer serviço. Você também pode fazer auditoria de segurança êxitos e falhas.  
  
 [Creating WS-I Basic Profile 1.1 Interoperable Services](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md) (Criando serviços interoperáveis de perfil básico do WS-I 1.1)  
 Os requisitos para implantar um serviço que é interoperável com serviços e clientes em qualquer plataforma ou sistema operacional descritos em WS-I Basic Profile 1.1 especificação.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Basic Programming Lifecycle](../../../docs/framework/wcf/basic-programming-lifecycle.md) (Ciclo de vida de programação básica)  
  
 [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)  
  
 [Hosting Services](../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)  
  
 [Building Clients](../../../docs/framework/wcf/building-clients.md) (Compilando clientes)  
  
 [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md) (Introdução à extensibilidade)  
  
 [Administration and Diagnostics](../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)  
  
## <a name="see-also"></a>Consulte também  
 [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md) (Programação básica do WCF)  
 [Conceptual Overview](../../../docs/framework/wcf/conceptual-overview.md) (Visão geral conceitual)  
 [WCF Feature Details](../../../docs/framework/wcf/feature-details/index.md) (Detalhes de recursos do WCF)
