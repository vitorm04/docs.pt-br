---
title: Configurando serviços WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156501"
---
# <a name="configuring-wcf-services"></a>Configurando serviços WCF

Depois que você tiver projetado e implementado o contrato de serviço, você está pronto para configurar seu serviço. Isso é onde você pode definir e personalizar como o serviço é exposto aos clientes, incluindo especificando o endereço em que ele pode ser encontrado, o transporte e ele usa para enviar e receber mensagens e o tipo de segurança requer a codificação de mensagem.  
  
 Configuração como utilizado aqui inclui todas as maneiras, imperativa no código ou usando um arquivo de configuração, no qual você pode definir e personalizar vários aspectos de um serviço, como especificando seus endereços de ponto de extremidade, os transportes usados e seus esquemas de segurança. Na prática, gravar a configuração é a principal parte da programação de aplicativos do WCF.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md)  
 Começando com [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], o WCF é fornecido com um novo modelo de configuração padrão que simplifica os requisitos de configuração do WCF. Se você não fornecer nenhuma configuração do WCF para um serviço específico, o tempo de execução configura automaticamente o seu serviço com comportamentos, associações e pontos de extremidade padrão.  
  
 [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Um serviço do Windows Communication Foundation (WCF) é configurável usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tecnologia de configuração. Mais comumente, os elementos XML são adicionados ao arquivo Web. config para um site de serviços de informações da Internet (IIS) que hospeda um serviço WCF. Os elementos permitem que você altere detalhes, como os endereços de ponto de extremidade (endereços reais usados para se comunicar com o serviço) em uma base por máquina.  
  
 [Associações](../../../docs/framework/wcf/bindings.md)  
 Além disso, o WCF inclui diversas configurações comuns fornecidos pelo sistema na forma de associações que permitem que você selecionar rapidamente os recursos mais básicos para como um serviço e o cliente se comunicam, como os transportes, segurança e mensagem codificações usadas.  
  
 [Pontos de extremidade](../../../docs/framework/wcf/endpoints.md)  
 Toda a comunicação com um serviço WCF ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade contêm o contrato, as informações de configuração que são especificadas nas associações e os endereços que indicam onde encontrar o serviço ou onde obter informações sobre o serviço.  
  
 [Serviços de segurança](../../../docs/framework/wcf/securing-services.md)  
 Usando o WCF e existente mecanismos de segurança, você pode implementar a confidencialidade, integridade, autenticação e autorização em qualquer serviço. Você também pode fazer a auditoria para falhas e êxitos de segurança.  
  
 [Criando serviços interoperáveis de perfil básico de WS-I 1.1](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Os requisitos para implantar um serviço que é interoperável com serviços e clientes em qualquer plataforma ou sistema operacional são descritos em WS-I Basic Profile 1.1 especificação.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Serviços de implantação e projeção](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md)  
  
 [Compilando clientes](../../../docs/framework/wcf/building-clients.md)  
  
 [Introdução à extensibilidade](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Administração e diagnósticos](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Consulte também

- [Programação de WCF básica](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Visão geral conceitual](../../../docs/framework/wcf/conceptual-overview.md)
- [Detalhes de funcionalidades do WCF](../../../docs/framework/wcf/feature-details/index.md)
