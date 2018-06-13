---
title: Configurando serviços
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803274"
---
# <a name="configuring-services"></a>Configurando serviços
Depois que você tiver criado e implementado o contrato de serviço, você está pronto para configurar seu serviço. Isso é onde você pode definir e personalizar como o serviço é exposto aos clientes, incluindo a especificação do endereço onde ele pode ser encontrado, o transporte e a codificação de mensagens usa para enviar e receber mensagens e o tipo de segurança requer.  
  
 Configuração conforme usado aqui inclui todas as formas imperativa no código ou usando um arquivo de configuração, no qual você pode definir e personalizar os vários aspectos de um serviço, como especificando seus endereços de ponto de extremidade, os transportes usados e seus esquemas de segurança. Na prática, a configuração de gravação é uma grande parte da programação de aplicativos do WCF.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md)  
 Começando com [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], o WCF é fornecido com um novo modelo de configuração padrão que simplifica a requisitos de configuração do WCF. Se você não fornecer qualquer configuração do WCF para um serviço específico, o tempo de execução configura automaticamente o serviço com comportamentos, associações e pontos de extremidade padrão.  
  
 [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Um serviço do Windows Communication Foundation (WCF) é configurável usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tecnologia de configuração. Mais comumente, os elementos XML são adicionados ao arquivo Web. config para um site de serviços de informações da Internet (IIS) que hospeda um serviço WCF. Os elementos permitem alterar detalhes, como os endereços de ponto de extremidade (os endereços reais usados para se comunicar com o serviço) em uma base por máquina.  
  
 [Associações](../../../docs/framework/wcf/bindings.md)  
 Além disso, o WCF inclui várias configurações comuns fornecidos pelo sistema na forma de associações que permitem que você selecionar rapidamente os recursos mais básicos como um serviço e um cliente se comunicam, como os transportes, segurança e mensagem codificações usadas.  
  
 [Pontos de extremidade](../../../docs/framework/wcf/endpoints.md)  
 Toda a comunicação com um serviço WCF ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade contêm o contrato, as informações de configuração que são especificadas nas associações e os endereços que indicam onde encontrar o serviço ou onde obter informações sobre o serviço.  
  
 [Protegendo serviços](../../../docs/framework/wcf/securing-services.md)  
 Usando o WCF e existente mecanismos de segurança, você pode implementar a confidencialidade, integridade, autenticação e autorização em qualquer serviço. Você também pode fazer auditoria de segurança êxitos e falhas.  
  
 [Criando serviços interoperáveis de perfil básico do WS-I 1.1](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Os requisitos para implantar um serviço que é interoperável com serviços e clientes em qualquer plataforma ou sistema operacional descritos em WS-I Basic Profile 1.1 especificação.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Serviços de design e implantação](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Hospedando serviços](../../../docs/framework/wcf/hosting-services.md)  
  
 [Compilando clientes](../../../docs/framework/wcf/building-clients.md)  
  
 [Introdução à extensibilidade](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Consulte também  
 [Programação básica do WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Visão geral conceitual](../../../docs/framework/wcf/conceptual-overview.md)  
 [Detalhes de recursos do WCF](../../../docs/framework/wcf/feature-details/index.md)
