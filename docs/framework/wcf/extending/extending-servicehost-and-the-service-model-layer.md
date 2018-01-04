---
title: "Estendendo a camada de modelo de serviço e o ServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c73af3b9187fa5365d7ea99474ea182d5f5ae86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Estendendo a camada de modelo de serviço e o ServiceHost
A camada de modelo de serviço é responsável por recebendo mensagens de entrada fora dos canais subjacentes, convertendo-os em invocações do método no código do aplicativo e enviar os resultados de volta para o chamador. Extensões do modelo de serviço modificam ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de cliente ou o distribuidor, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do cliente, bem como as classes em que você pode inserir suas extensões personalizadas em aplicativos cliente. Por exemplo, executar o log de mensagens de cliente personalizadas, executar a serialização da mensagem personalizada e assim por diante.  
  
 [Estendendo dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do serviço, bem como as classes em que você pode inserir suas extensões personalizadas em aplicativos de serviço. Por exemplo, você pode executar o log de serviço personalizado, a validação do lado do serviço de mensagem, expedição personalizados e assim por diante.  
  
 [Objetos extensíveis](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Descreve os cinco objetos extensíveis e o <xref:System.ServiceModel.IExtensibleObject%601> padrão. O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar o novo estado para um objeto. Extensões, anexadas a um dos objetos extensíveis, habilitar comportamentos em diferentes estágios de processamento para acessar o estado compartilhado e anexado a um objeto extensível comum que eles possam acessar a funcionalidade.  
  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Para alterar as configurações em ou inserir extensões no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução, você usa comportamentos. O WCF inclui comportamentos implementados pelo sistema para controlar a limitação de instanciação e muitos outros aspectos de serviços e operações. Esta seção descreve como criar seus próprios comportamentos personalizados e como torná-los disponíveis tanto por meio de programação e usando arquivos de configuração.  
  
 [Estendendo a hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Descreve como estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>e usar o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes para personalizar o ambiente de host.  
  
## <a name="reference"></a>Referência  
  
## <a name="related-sections"></a>Seções relacionadas
